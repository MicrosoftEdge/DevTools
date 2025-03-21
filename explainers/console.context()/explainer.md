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

1. Improve the debugging process by making it easier and faster to navigate console log messages with context-based grouping.
2. Improve the overall readability of the console.

## Use case in DevTools
Developers can create multiple named contexts for different parts of their application. By logging messages to a named context, you can easily identify and follow the flow of a specific part of your application.

In the DevTools Console panel, you can filter messages based on the name of the context. If a colour is specified for a context, the log messages will appear in that colour improving the visual clarity of messages from different contexts.

1. Create a specific logger instance for a part of your app:

`const myComponentLogger = console.context("name-of-my-component");`

2. Then log messages as normal, using your new logger:

`myComponentLogger.log("This is a log message from my component");`

`myComponentLogger.warn("This is a warning message from my component");`

3. For an even nicer experience, give your logger a color:

`myComponentLogger.log("%cThis is a log message from my component", "background-color:lemonchiffon;");`

Here is what the Console tool might look like, with the logs from all of the components of the app:

![DevTools Console panel with context logs](console-with-context-logs.png)

Here is what the Console tool would show, once the logs have been filtered by context, to show only the logs from one component:

![DevTools Console panel with filtered context logs](console-with-context-logs-filtered.png)