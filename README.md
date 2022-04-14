# Microfrontends with React: A Complete Developer's Guide Section 4 -

## Inflexible Requirements #1
Zero coupling between child projects

- No importing of functions/objects/classes/etc
- No shared state
- Shared libraries through MF is OK

## Inflexible Requirements #2
Near-zero coupling between container and child apps

- Container shouldn't assume that a child is using a particular framework
- Any necessary communication done with callbacks or simple events

## Inflexible Requirements #3
CSS from one project shouldn't affect another

## Inflexible Requirements #4
Version control (monorepo vs separate) shouldn't have any impact on the overall project

- Some people want to use monorepos
- Some people want to keep everything in a separate repo

## Inflexible Requirements #5
Container should be able to decide to always use the latest version of a microfrontend or specify a specific version

1. Container will always use the latest version of a child app (doesn't require a redeploy of container)
2. Container can specify exactly waht version of a child it wants to use (requires a redeploy to change)

## Deployment

- Want to deploy each microfrontend independently (including the container)
- Location of child app remoteEntry.js files must be known at build time
- Many front-end deployment solutions assume you're deploying a single project - we need something that can handle multiple different ones
- Probably need a CI/CD pipeline of some sort
- At present, the remoteEntry.js file name is fixed! Need to think about caching issues

## Workflow For Deploying Container
- Whenever code is pushed to the master/main branch and this commit contains a change to the 'container' folder
- Change into the container folder
- Install dependencies
- Create a production build using webpack
- Upload the result to AWS S3

## Multi-Tier Navigation
1. Both the Container + Individual SubApps need routing features
2. Sub-apps might need to add in new pages/routes all the time
3. We might need to show two or more microfrontends at the same time
4. We want to use off-the-shelf routing solutions
5. We need navigation features for sub-apps in both hosted mode and in isolation
6. If different apps need to communicate information about routing, it should be done in as generic a fashion as possible

