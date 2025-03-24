# DevTools: console.context()

Authors:
 - *[Leah Tu](https://github.com/leahmsft)*, Microsoft Edge
 - *[Patrick Brosset](https://github.com/captainbrosset)*, Microsoft Edge


## Status of this feature

An initial version of this feature has been available in Microsoft Edge starting with version 79. This explainer proposes improvements to the feature.

## Introduction

When debugging web applications with large code bases having many components from many different teams, it can be challenging for developers to filter through the many log messages that appear in the Console tool and find the relevant ones. Often, developers want to filter the messages so that only the ones from the component they're working on appear. For example, a developer might want to see the logs that are emitted by a given UI component only, or by a database utility module only.

Developers can use existing techniques that help with this use case, but these techniques have limitations:

* Use the `console.group()` API to group related log messages together.

  * However, this requires developers to always open the group before logging and then close it.
  * Also, unrelated logs could also get included into groups.
  * Finally, nested groups lead to nested log messages, which might not always be desirable if developers want to focus only on their component.

* Prefix log messages with a name.

  * This can be tedious and error prone. Developers can build their own console logging utility to handle this systematically.

## Goals
Our goal is to improve on the existing experimental `console.context()` method to provide a better solution for logging messages from a multi-component web app's code base, and more easily filter messages in the Console.

The `console.context(contextName)` method returns an instance of an object that implements the same methods as the `console` namespace. Developers can create different contexts for the different parts of their apps. Messages logged from a context object _belong_ to the context and can be filtered in the Console tool, currently by typing `context:contextName` in the Console's search field.

The main goals are:

1. Improve the debugging process for large web applications, by making it easier and faster to navigate many console log messages thanks to context-based filtering.
2. Improve the overall readability of the console.
3. Make it easy for developers to create contextual loggers, without requiring them to write their own utility code.

## Use case in DevTools
Developers can create multiple named contexts for different parts of their application. By logging messages to a named context, you can easily identify and follow the flow of a specific part of your application.

### Current experience in Chromium
In the DevTools Console panel, you can filter messages based on the name of the context. If a colour is specified for a context, the log messages will appear in that colour improving the visual clarity of messages from different contexts.

1. Create a specific logger instance for a part of your app:

`const myComponentLogger = console.context("name-of-my-component");`

2. Then log messages as normal, using your new logger:

`myComponentLogger.log("This is a log message from my component");`

`myComponentLogger.warn("This is a warning message from my component");`

3. You could also give your log messages a colour to colour-code them for different loggers:

`myComponentLogger.log("%cThis is a log message from my component", "background-color:lemonchiffon;");`

Here is what the Console tool might look like, with the colour-coded logs from all of the components of the app:

![DevTools Console panel with context logs](console-with-context-logs.png)

Here is what the Console tool would show, once the logs have been filtered by context, to show only the logs from one component:

![DevTools Console panel with filtered context logs](console-with-context-logs-filtered.png)

### Proposed improvements
This is a useful feature, but it could be improved by making changes to the method and adding in new functionality in the DevTools Console to support this.

For `console.context()`,

**1. Add a second, optional `color` argument to `console.context()` to accept a colour.**

Adding a colour to each logger instance will help developers easily find messages at a glace in the Console, without needing to filter other messages. It's possible to add colour to a single log message today. However, in order to colour-code a logger's messages, it would need to be specified for every message to that logger. This is tedious and error prone since it involves not only logging individual messages but also remembering which colour is for each logger. Giving developers the ability to specify a colour to the logger itself will solve this issue and make it more efficient.

If a `color` isn't given, then we should assign a random color that hasn't been used yet when a new logger instance is created. This will ensure that all context log messages are easily distinguishable.

For the DevTools console UI,

**1. Add a new filter option for contexts**

It's possible to filter for context log messages by searching `context:context-name`, but this requires extra effort. To make it more user-friendly, we will add context names to the Console sidebar, so that you can simply click on a context and the Console will filter out everything else.

If you log messages to a logger with `error()`, `warn()`, `info()`, `debug()`, then those will be displayed in a dropdown under the context name with a count.

![DevTools Console panel sidebar with context filters](console-sidebar-with-context-filters.png)

**2. Add badges to contextual log messages**

Since all contexts will have an assigned colour, we will display the context name and its colour on a badge on all of its messages. This will keep messages easy to read and help developers see the context for any message at a glace.

![DevTools Console panel with badges on context logs](console-with-context-logs-badges.png)