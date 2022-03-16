# DevTools: Documentation Search
Authors:
- [Erica Draud](https://github.com/erdraud), Program Manager
- [Sean Larkin](https://github.com/TheLarkInn), Technical Program Manager

## Status of this feature
This feature is a proposed experiment.

## Background
This project was part of the Project Mallard effort to improve Bing searches for developers. Search and solution finding occupy most of a developer’s time on the web. On average, a developer may click 5-10 times until they have found the solution they are looking for. Developers use a variety of services and software that provide contextual hints as to what solutions they might look for, or what work they are assigned to on any given day. These services may include (but are not limited to) ADO, Jira, GitHub, or any other project management software that has their day-to-day work tracked. In combination with the Microsoft Developer Graph, information about the developer can be used to inform and suggest more intelligent and relevant searches.  

For example, a developer has 3 high priority work items on his current ADO sprint all referencing JavaScript animations. They also might have 2 websites bookmarked in Microsoft Edge on JavaScript animations. Prior to ever searching for a solution, Developer Search, leverages the intelligence from the Microsoft Developer Graph, and uses NTP real estate to highlight popular LinkedIn Learning courses on JavaScript and CSS Animations, previous pull requests merged in that project’s codebase, the developer’s bookmarked pages, and finally relevant and popular articles related to the topic. The results are then enriched by the developer’s own search query and are combined to provide a solution in half the time and clicks.  

Open Source developer Tobias Koppers commented on his challenge to find solutions across GitHub: 

> The webpack project consists of over 100 repositories across 2 GitHub projects. If I have to track down a particular issue, I would have to search for it across either all of GitHub or every one of the individual projects and repositories. It would save me hours a week to simply configure my Edge/Bing search to include search results across specific GitHub repositories/projects and return results from PR & Issues.  

## Goals
  1. Detect when a Microsoft Edge user is a Developer and
2. Collect all relevant solution areas based on criteria of assigned work items and tasks and 
3. Leverage Bing’s search platform to create developer focused customer models and insights.

## Non-goals
1.	Build a separate search, AI, ML model from Bing today

## Hypotheses
* Users will find this valuable in that it will save them time by making it easier to access the developer resources they’re looking for; we'll know it's true if 20% of users are 1-month active users (returning users).
* Users will research Elements and Console more than the other documentation combined; we'll know it's true if the number of documentation searches for Elements and Console are more than 100% of the other documentation searches.
* Users will have trouble finding this feature without a tooltip/pop-up; we'll know it's true with overall usage (if people turn it on).

This initial experiment will run as a flagged rollout especially since the UI may also affect users outside of DevTools. We will test all three hypotheses and focus on iterating for validating the feature’s value as well as which commands are most valuable.

## Solutions

![Documentation Search UI](doc-search.png]

### Solution 1: Omnibox Integration
Our ideal option is to have the Documentation Search integrated into the address bar (called the omnibox from now on). We would use a unique character typed into the omnibox to trigger the feature. In the Omnibox experiment, there are other character like `?` and `#` that users can type before typing their command or selecting the command from the drop-down menu. We would find a character to access a similar experience to find the right documentation for the search. We could have a series of keywords that the user can type to access the appropriate documents.

We would start by integrating into the Commander as an experiment like that of the original Omnibox experiment before the more technical and time-consuming work of integrating into the existing omnibox.

### Solution 2: Improved Bing searches
Alternatively, we could detect developers and set up Bing filters that will provide the user with results from only the most relevant websites.

As developers, we often go back to searching for the same solution 5-6 times before we have it memorized. Even after visiting the same solution page 5-6 times, we may never bookmark, favorite, or document the location of that solution. Microsoft Developer Search can create dictionaries of repeated “searched and found” solutions to quickly recall them in one step.  
Examples of this could be simple searches like: 
* slice() vs splice() 
* call() vs apply() vs bind() 
* getTimeout() vs getInterval() 
* lodash.map  

Searches like this could yield predictive answers to the exact page a developer “bounced” from (indicating their solution was found) the first 3-4 times. To save developers precious context switching and time, this “bounced” search could even be leveraged across other Microsoft developer products such as VS Code, VS, and VS Online to find answers right in the IDE and code editor. Or in short, the more a developer searches and finds solutions, the less time they will spend in the future needing to find those same solutions.  

### Solution 3: DevTools Welcome tool integration
We previously did a research study where users said that they would like a search bar for the Welcome tool, especially if it could help them find the documentation they need. In proposing this solution, it could be done in addition to Solution 1 or 2 or on its own.

This search bar could have the UI pulled from the search bar on docs.microsoft.com, shown in the mockup under [Solutions](#solutions). Upon selecting the search result, it could open the documentation either within DevTools or in a new tab.

## Next steps
* Design review
* Flagged rollout

## Things to consider
* Discoverability could be an issue
Searches shouldn't conflict with traditional search engine searches
* Accessibility and privacy compliance needs work
* Need to remove Chrome's petal suggestions for technical, localization, and business reasons
* Commands are relatively easy to add, so we can always add more in the future
