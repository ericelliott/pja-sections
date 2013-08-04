# Feature Toggle

Continuous deployment is the process of testing, integrating, and deploying software in rapid cycles in order to deliver bug fixes and new features to customers as quickly as possible. It gained popular acceptance as a cornerstone of extreme programming, and agile methodologies. It is very popular among Software as a Service providers.

A ***feature toggle*** system allows you to integrate features into your codebase even before they're finished and ready to release. During development, the features are toggled off by default. In order to turn them on, you must enable them manually. Using this method, you can deploy unfinished or untested changes into your production system without interfering with the user experience.

Feature toggles can allow software integration cycles that run in weeks, days, or even hours, as opposed to months or years. They are an essential component in a broader continuous integration system.

Feature toggles are popular in the startup community, but have gained widespread acceptance in the enterprise, including larger companies such as Facebook, Google, Yahoo, and Adobe.


## Organizing Features

Deciding how to organize features begins with deciding what exactly constitutes a feature. Once you figure that out, you should also decide how you're going to classify or group features together.


### Scale of a Feature

"Feature" can mean almost anything, ranging from a new page or route to an additional select option on a select element. Deciding how to classify the scope of the feature is up to the project manager, but it's easy to go overboard with features. My recommendation is to toggle at the page / route level whenever possible.

Features should be toggled on and off at the largest scale possible. For example, if you're building a new page, you shouldn't check whether the feature is on for every operation used to build up the page. Instead, toggle the feature at the route level. If the feature is a new element on the page, create a new view for that element, and only render that view if the feature is toggled on.

APIs should also use a feature toggle system, and the API should be capable of toggling at the route level, as well.

If you happen to use a hypermedia API and hypermedia-aware client, you can turn features on and off in the client simply by adding or removing resources from the API. For example, if you want to disable a route, just remove it from your hypermedia links, and the client won't be able to discover and use the route.


### Feature Groups

Sometimes it's handy to group features together. You should definitely do so for features that are designed to interact with each other. It's possible to build a feature dependency graph to keep track of which features rely on each other to opperate correctly, and then toggle them on and off simultaneously.

Groups can also be handy for marketing purposes. Sometimes it's useful to group several exciting new features together into a newsworthy release. For products that rely on publicity cycles to spur growth, engineering must provide the technical capabilities to generate worthy news events.

It's essential for product to engage marketing in a realistic way. The executives and marketing team should not start touting a release date until the features are in the testing stage and nearing completion. Features don't need to be released the moment they're complete. You can hold completed features for a scheduled marketing event, and flip the toggle switch at the precise moment that marketing has promised delivery. Since the features are already deployed into production, they'll be live and ready to use immediately.

Features are often grouped in default sets for each environment, as well. A default set commonly includes all of the features that will be toggled on in the next deploy cycle.


## Lifespan of a Feature


The creation of a feature begins with naming and documentation. Before you write a line of code, name and describe the feature, along with any required criteria to qualify it for production activation.


### Development

Start with a few functional unit tests. What does the feature do? How can you verify that behavior with code? Once that's done, begin the implementation, wrapping the lines of code that trigger the feature in a conditional block that only executes if the feature is enabled.

### Staging

At the staging phase, features can be toggled on or off. Generally, the next set of production deploy defaults will be toggled on by default in staging.


### Production Testing

### Feature Rollout

### Default Activation

Default activation means that the feature is active by default across the whole system, and not on a user-by-user basis. A feature can stay in this state until it is no longer needed, or until it is phased out, or it can progress to full integration status.


### Full Integration

Once a feature has made it this far, it's time to consider removal of the feature toggle from the source code and the feature name from the features database. Cleaning up feature branching can reduce code complexity and make it easier to maintain which features are active.

## Implementation
