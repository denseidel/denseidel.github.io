---
id: buildfrontend
title: DO: Build Frontend Component
---

The frontend is developed using [Javascript](https://www.freecodecamp.org/news/beaucarnes/learn-javascript-full-course--j4Va5cR1p)/[Penetration-Testing](https://www.freecodecamp.org/news/beaucarnes/web-app-penetration-testing-full-course--pena5cR1p) using the Framework with the largest mature ecosystem [React](https://github.com/enaqx/awesome-react)([Course](https://www.udemy.com/react-the-complete-guide-incl-redux/)) and [React Best Practices](https://www.zerrtech.com/blog/react-design-best-practices).

## Decisions

<!-- adrlog -->

- [ADR-0001](adr/0001-use-ant-design-as-a-ui-framework.md) - Use Ant Design as a UI framework
- [ADR-0002](adr/0002-use-react-for-desktop-and-mobile.md) - Use React for Desktop and Mobile
- [ADR-0003](adr/0003-use-gatsby-for-landing-pages.md) - Use Gatsby for Landing Pages
- [ADR-0004](adr/0004-use-web-over-native-for-uis.md) - Use web over native for UIs

<!-- adrlogstop -->

## PLAN: Product Requirement Documentation, User Stories

Create a one pager for the [product requirement documentation - including the user interaction and design](https://web.archive.org/web/20190422164155/https://www.atlassian.com/agile/product-management/requirements) - [TEMPLATE](https://docs.google.com/document/d/1-kKH6L1eHzGRNX_59DEK1D-u7TPns79OVBOkbtdZvsA/edit#). For the User Interaction & Design [create content structure & components](https://developers.google.com/web/fundamentals/codelabs/your-first-multi-screen-site/#create_your_content_and_structure).

## DO: Setup Component Development

We use [storybook](https://www.learnstorybook.com/react/en/get-started/) for component based development. Set it up:

```bash
# Create our application:
npx create-react-app ui --typescript
cd ui
npm install
```

```
# Add Storybook:
# Setup storybook webpack to work with typescript: https://medium.com/@dandobusiness/setting-up-a-react-typescript-storybook-project-5e4e9f540568 (step 4) / https://storybook.js.org/docs/configurations/typescript-config/
npm i -D @storybook/react
npm install @types/storybook__react
# some plugins
npm i -D awesome-typescript-loader
npm i -D react-docgen-typescript-loader
npm i -D react-docgen-typescript-webpack-plugin
```

Create files in `.storybook`:

```bash
.storybook
 - addons.js
 - config.js
 - tsconfig.json
 - webpack.config.js
```

```js
// .storybook/config.js
import { configure } from "@storybook/react";
const req = require.context("../src/components", true, /.stories.tsx$/);
function loadStories() {
  req.keys().forEach(req);
}
configure(loadStories, module);
```

```js
// .storybook/tsconfig.json
{
  "compilerOptions": {
    "baseUrl": "./",
    "allowSyntheticDefaultImports": true,
    "module": "es2015",
    "target": "es5",
    "lib": ["es6", "dom"],
    "sourceMap": true,
    "allowJs": false,
    "jsx": "react",
    "moduleResolution": "node",
    "rootDir": "../",
    "outDir": "dist",
    "noImplicitReturns": true,
    "noImplicitThis": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "declaration": true
  },
  "include": [
    "src/**/*"
  ],
  "exclude": [
    "node_modules",
    "build",
    "dist",
    "scripts",
    "acceptance-tests",
    "webpack",
    "jest",
    "src/setupTests.ts",
    "**/*/*.test.ts",
    "examples"
  ]
}
```

```js
// .storybook/webpack.config.js

const path = require("path");
const SRC_PATH = path.join(__dirname, "../src");
const STORIES_PATH = path.join(__dirname, "../stories");
//dont need stories path if you have your stories inside your //components folder
module.exports = ({ config }) => {
  config.module.rules.push({
    test: /\.(ts|tsx)$/,
    include: [SRC_PATH, STORIES_PATH],
    use: [
      {
        loader: require.resolve("awesome-typescript-loader"),
        options: {
          configFileName: "./.storybook/tsconfig.json"
        }
      },
      { loader: require.resolve("react-docgen-typescript-loader") }
    ]
  });
  config.resolve.extensions.push(".ts", ".tsx");
  return config;
};
```

Add command `"storybook": "start-storybook -p 9001 -c .storybook"` to `package.json`.

Create first component in `src/components`:

```js
import * as React from "react";
export interface IButtonProps {
  children?: React.ReactNode;
  onClick?: (e: any) => void;
}
const styles = {
  border: "1px solid #eee",
  borderRadius: 3,
  backgroundColor: "#FFFFFF",
  cursor: "pointer",
  fontSize: 15,
  padding: "3px 10px",
  margin: 10
};
const Button: React.SFC<IButtonProps> = props => (
  <button onClick={props.onClick} style={styles} type="button">
    {props.children}
  </button>
);
Button.defaultProps = {
  children: null,
  onClick: () => {}
};
export default Button;
```

Create test story `button.stories.tsx`:

```js
import { storiesOf } from "@storybook/react";
import * as React from "react";
import Button from "./Button";
storiesOf("Button", module)
  .add("with text", () => <Button>Hello Button</Button>)
  .add("with some emoji", () => <Button>😀 😎 👍 💯</Button>);
```

Start storybook: `npm run storybook`

# Run the test runner (Jest) in a terminal:

yarn test

# Start the component explorer on port 9009:

yarn run storybook

# Run the frontend app proper on port 3000:

yarn start

````

Start building your [components](https://www.learnstorybook.com/react/en/simple-component/).

### [Bit](https://docs.bit.dev/docs/quick-start.html)

To share the components we use [bit](https://docs.bit.dev/docs/quick-start.html).

```bash
# Install bit
npm install bit-bin -g

# Init Bit for your project
cd project-directory
bit init

# Track components with Bit
bit add src/components/*

# Defining a compiler (https://bit.dev/bit/envs/compilers/react-typescript)
bit import bit.envs/compilers/react-typescript -c
bit build

# Tagging component versions
bit tag --all 1.0.0

# Export the components
bit login
bit export user-name.collection-name


# Consume components in other projects
npm config set '@bit:registry' https://node.bit.dev
npm i @bit/mui-org.material-ui.button

````

## DO: Design & Style the frontend

The foundations of UI design is [CSS3, Flexbox, and CSS grid](https://developer.mozilla.org/en-US/docs/Web/Guide) extended by [React Best Practices and Patterns](https://www.sitepoint.com/react-architecture-best-practices/). Suplement this with **Ant Design** as a UI Framework for [Desktop](https://ant.design) and [Mobile](https://mobile.ant.design/docs/react/introduce). Some Samples can be found [here](https://github.com/ant-design/ant-design/issues/477).

- [7 Practical Tips for Cheating at Design](https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886)

[58 bytes of css to look great nearly everywhere](https://jrl.ninja/etc/1/)

```css
main {
  max-width: 38rem;
  padding: 2rem;
  margin: auto;
}
```

### Use [Figma](https://www.figma.com/) or sketches on paper/ipad for mocking & design

## DO: Prepare the codebase

### Architecture

- Application: [MVVM](https://medium.cobeisfresh.com/level-up-your-react-architecture-with-mvvm-a471979e3f21) vs Redux
- Code: [Redux General](https://redux.js.org/faq/codestructure), [ducks](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be)
  - Tutorial Basics: https://learn.freecodecamp.org/front-end-libraries/redux
  - Docs !: https://redux.js.org/basics/usagewithreact#implementing-components
  - Redux - Ducks: https://github.com/erikras/ducks-modular-redux
  - Redux - Saga: https://github.com/redux-saga/redux-saga / https://flaviocopes.com/redux-saga/

#### Project Structure

Theory: [https://hackernoon.com/my-journey-toward-a-maintainable-project-structure-for-react-redux-b05dfd999b5](https://hackernoon.com/my-journey-toward-a-maintainable-project-structure-for-react-redux-b05dfd999b5)

```text
src
 ├── components
 │
 ├── containers
 │  ├── auth.js
 │  ├── productList.js
 │  └── productDetail.js
 │
 ├── reducers (aka ducks)
 │  ├── index.js (combineReducers + complex selectors)
 │  ├── auth.js (reducers, action types, actions creators, selectors)
 │  └── product.js (reducers, action types, actions creators, selectors)
 │
 ├── sagas
 │  ├── index.js (root saga/table of content of all the sagas)
 │  ├── auth.js
 │  └── product.js
 │
 └── services
    ├── authenticationService.js
    └── productsApi.js
```

## DO: Build Our Frontend

Use [create-react-app with antd](https://ant.design/docs/react/use-with-create-react-app)

```bash
# initialize app
npm create react-app antd-demo
cd antd-demo
# add antd
npm install antd
# configure the build to work with scss https://ant.design/docs/react/use-with-create-react-app#Advanced-Guides (required for antd)
```

### Build your components

I keep the project structure and architecture (about state) in mind. Also I sketch the app out first!
The I [build the components](https://www.udemy.com/react-the-complete-guide-incl-redux/learn/v4/t/lecture/8108994?start=0), [add routing](https://www.udemy.com/react-the-complete-guide-incl-redux/learn/v4/t/lecture/8145908?start=0) and [add redux for state management](https://www.udemy.com/react-the-complete-guide-incl-redux/learn/v4/t/lecture/8211904?start=0).

### Add authentication

Use [AWS amplify](https://aws-amplify.github.io/docs/js/authentication#manual-setup) with the [generated identity provider config](../platform/iam.md#saas-aws-cognito):

```js
import Amplify from "aws-amplify";

Amplify.configure({
  Auth: {
    region: config.region,
    userPoolId: config.userPoolId,
    userPoolWebClientId: config.userPoolWebClientId,
    mandatorySignIn: true
  }
});

const currentConfig = Auth.configure();
```

### More topics

- Serverside Rendering: [https://github.com/phodal/serverless-react-server-side-render/blob/master/src/index.js](https://github.com/phodal/serverless-react-server-side-render/blob/master/src/index.js)

### Build & Deploy Frontend

#### CI/CD Serverless Frontend

```yaml
# https://github.com/denseidel/saas-platform-template/blob/master/devops/frontend-preview/azure-pipelines.yaml
# Add steps that analyze code, save build artifacts, deploy, and more:
# https://docs.microsoft.com/azure/devops/pipelines/languages/javascript

pr:
  branches:
    include:
      - master
  paths:
    include:
      - /frontend
    exclude:
      - README.md
      - /adr/*
      - .adr-dir

pool:
  vmImage: "Ubuntu-16.04"

steps:
  - task: NodeTool@0
    inputs:
      versionSpec: "8.x"
    displayName: "Install Node.js"

  - script: |
      apt-get update && apt-get install -y libgconf-2-4
      curl -fsSL https://get.pulumi.com | sh
    displayName: "setup credentials & dependencies"

  - script: |
      export PATH=$PATH:$HOME/.pulumi/bin
      cd devops/frontend-preview
      npm install
      pulumi stack select denseidel/saas-template-frontend/dev
      pulumi stack output -j > ../../frontend/src/config.json
      cd ../../frontend
      npm install && npm run build
    env:
      PULUMI_ACCESS_TOKEN: $(pulumi.access.token)
      AWS_ACCESS_KEY_ID: $(aws.master.accesskey)
      AWS_SECRET_ACCESS_KEY: $(aws.master.accesssecret)
    displayName: "build"

  - script: |
      cd frontend
      npm run e2e
    displayName: "run test"

  - script: |
      # setup preview environment & artifact bucket & upload to artifiact bucket
      export PATH=$PATH:$HOME/.pulumi/bin
      cd devops/frontend-preview
      #npm install
      pulumi stack select denseidel/saas-template-frontend/dev
      pulumi up -y
    env:
      PULUMI_ACCESS_TOKEN: $(pulumi.access.token)
      AWS_ACCESS_KEY_ID: $(aws.master.accesskey)
      AWS_SECRET_ACCESS_KEY: $(aws.master.accesssecret)
    displayName: "Setup Infrastucture & Deploy to preview environment"
```

#### Container Deployment

##### Dockerize

1. [http://mherman.org/blog/2017/12/07/dockerizing-a-react-app/](http://mherman.org/blog/2017/12/07/dockerizing-a-react-app/)
2. [https://www.peterbe.com/plog/how-to-create-react-app-with-docker](https://www.peterbe.com/plog/how-to-create-react-app-with-docker)

## DO: Frontend Testing

Use [Efficient Testing](https://medium.com/@darioghilardi/end-to-end-testing-on-a-react-redux-app-10f5a26f2f61) and be [economical](https://jobs.zalando.com/tech/blog/economic-perspective-testing/). Whenever your code base changes signifficantly you have to adapt your unit test. Therefore: Use a typed language. Focus on integration and end-to-end tests. Use unit tests only where they make sense (e.g. pure algorithmic code with complex corner cases). Be economic. Be lean.

> add cypress as an example