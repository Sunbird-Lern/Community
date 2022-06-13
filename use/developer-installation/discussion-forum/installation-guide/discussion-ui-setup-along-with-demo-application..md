# Discussion-UI setup along with demo application.

**Background**:

Discussion-UI library is an angular base library that will help any platform to configure and use a discussion forum.

In the Sunbird use case, any of the learning sections can have a discussion forum attached to it like Courses, Groups, etc. This is being achieved by this library.

#### Git Repository: <a href="#git-repository" id="git-repository"></a>

{% embed url="https://github.com/Sunbird-Ed/discussions-UI" %}

**Prerequisite**:

1. [Nodebb](nodebb-setup.md#nodebb) Local setup
2. [Discussion Middleware](discussion-middleware.md) Local setup

### How to setup Discussions-UI

**Step:1**

Clone the discussion-ui repo from [https://github.com/Sunbird-Ed/discussions-UI.git](https://github.com/Sunbird-Ed/discussions-UI.git).

```
git clone git@github.com:Sunbird-Ed/discussions-UI.git 2> cd discussion-UI
```

**Step:2**

Install dependencies.

```
yarn
```

**Step:3**

Change the configuration of library/application to communicate with local NodeBB & Discussion-middleware\
**Note**: Make sure Local discussion-middeware & NodeBB is running.

the `host` in `urlconfig.json` file. Add below url.

```
host: 'http://localhost:3002'
```

**Step:4**

Build the discussion-ui library using.

```
npm run build-lib
```

This will generate a dist file along with assets. For every change in discussion-ui library you have to run build command.

**Step:5**

Run the demo application using the command.

```
npm run demo
```

This is a simple angular application which is used to test df-library in local.

**Note**: Demo application will run on port **4200.**

\\
