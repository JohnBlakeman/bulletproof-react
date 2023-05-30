```json
{
  "name": "bulletproof-react",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@craco/craco": "^6.1.2",                       # Create React App Configuration Override
    "@headlessui/react": "^1.2.0",                  # Component Library - integrates with Tailwind CSS
    "@heroicons/react": "^1.0.1",                   # Icon Library - integrates with Tailwind CSS
    "@hookform/resolvers": "^2.5.2",                # Form builder - integrates with Zod
    "@tailwindcss/typography": "^0.4.1",            # Typeography - text presentation and layout
    "@testing-library/jest-dom": "^5.11.4",         # Unit testing - assertions made easier
    "@testing-library/react": "^11.1.0",            # Unit testing - react wrapper
    "@testing-library/user-event": "^12.1.10",      # Unit testing - trigger dom events
    "@types/jest": "^26.0.15",                      # Typescript - type definition [jest]
    "@types/node": "^16.0.0",                       # Typescript - type definition [node]
    "@types/react": "^17.0.0",                      # Typescript - type definition [react]
    "@types/react-dom": "^17.0.0",                  # Typescript - type definition [react-dom]
    "axios": "^0.21.1",                             # Http requests - ajax / promises
    "clsx": "^1.1.1",                               # Conditional CSS classes
    "dayjs": "^1.10.6",                             # Date and time handling library
    "dompurify": "^2.2.9",                          # XSS protection - sanitises strings from user input
    "history": "^5.0.0",                            # Unused? - Browser History interaction and hooks
    "intersection-observer": "^0.12.0",             # DOM event hooks -
    "jsonwebtoken": "^8.5.1",                       # JWT implementation
    "lodash": "^4.17.21",                           # Power tools for common operations
    "marked": "^2.0.7",                             # Mark down html parser
    "nanoid": "^3.1.23",                            # alternative guid generator
    "react": "^17.0.2",                             # react
    "react-dom": "^17.0.2",                         # react dom interactions
    "react-error-boundary": "^3.1.3",               # Error boundaries - stops blank screen on react render errors
    "react-helmet-async": "^1.1.2",                 # React Helmet extended to run async - handles injecting into <head>
    "react-hook-form": "^7.7.1",                    # Handles form data
    "react-query": "^3.34.15",                      # state management system
    "react-query-auth": "^1.0.0",                   # uses react-query to handler user data
    "react-router-dom": "^6.0.0-beta.0",            # url route handling
    "react-scripts": "4.0.3",                       # standard CRA library for handling standard react scripts
    "type-fest": "^1.2.0",                          # collection of typescript types, plenty of wheels to make life easier
    "typescript": "^4.1.2",                         # strong typing
    "web-vitals": "^1.0.1",                         # statistics and metrics to assist with performance reports and links with chrome and google tools
    "zod": "^3.1.0",                                # Schema validation - integrates with hookform/resolvers
    "zustand": "^3.5.2"                             # state management - obtains state via hooks transiently without causing renders
  },
  "scripts": {
    "start": "craco start",                                                                 # start with craco CRA configuration
    "start:cli": "cross-env BROWSER=none craco start",                                      # start with cross platform configuration
    "build": "craco build",                                                                 # build with craco CRA configuration
    "test": "is-ci \"test:coverage\" \"test:jest\"",                                        # running test in continual integration environment (coverage) or locally (jest)
    "test:jest": "craco test",                                                              # run test using craco CRA configuration
    "test:coverage": "CI=1 yarn test:jest -- --coverage",                                   # run test in continual integration environment
    "postinstall": "husky install",                                                         # install husky after npm / yarn install command
    "cy:install": "cypress install",                                                        # install cypress
    "cy:run": "cypress run",                                                                # run cypress
    "cy:open": "cypress open",                                                              # run cypress and pass in parameters
    "test:e2e:dev": "start-server-and-test start:cli http://localhost:3000 cy:open",        # end to end dev environment headed testing
                                                                                            #   launch test server
                                                                                            #   start with cross platform configuration
                                                                                            #   start with craco CRA
                                                                                            #   start cypress end to end testing
    "pretest:e2e:run": "yarn build",                                                        # build project before running end to end test
    "test:e2e:run": "start-server-and-test serve http://localhost:3000 cy:run",             # end to end test headless testing
    "test:e2e": "is-ci \"test:e2e:run\" \"test:e2e:dev\"",                                  # run tests depending if in continual integration environment
    "serve": "serve --no-clipboard --single --listen 3000 build",                           # start with serve http deamon
    "eject": "react-scripts eject",                                                         # eject CRA features
    "lint": "eslint --fix --ext .js,.ts,.tsx ./src --ignore-path .gitignore",               # lint project
    "prettier": "prettier --ignore-path .gitignore --write \"**/*.+(js|json|ts|tsx)\"",     # prettify code in all project files of given types
    "format": "npm run prettier -- --write",                                                # run prettify command using npm, then pass in arguments after -- to prettier script
    "check-types": "tsc --project tsconfig.json --pretty --noEmit",                         # typescript check compile errors, --noEmit stops compile (leave that to webpack?)
    "check-format": "npm run prettier -- --list-different",                                 # output code files that violate prettier rules and return failed
    "validate-and-build": "npm-run-all --parallel check-types check-format lint build",     # parallel run validation and build scripts: typescript, prettier, lint and build
    "validate": "npm-run-all --parallel check-types && lint-staged",                        # parallel run validation, git stage changes and lint before commit
    "generate": "plop",                                                                     # enter plop menu - to select what template to run
    "storybook": "start-storybook -p 6006 -s public",                                       # run storybook server
    "build-storybook": "build-storybook -s public"                                          # build storybook cache before running
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "resolutions": {
    "babel-loader": "8.1.0"
  },
  "devDependencies": {
    "@mswjs/data": "^0.3.0",                                # mock data library - relational models
                                                            # storybook - developing and testing components in isolation
    "@storybook/addon-actions": "^6.3.2",                   #   display data received by event handlers
    "@storybook/addon-essentials": "^6.3.2",                #   extended functionality
    "@storybook/addon-links": "^6.3.2",                     #   navigate between stories
    "@storybook/node-logger": "^6.3.2",                     #   npmlog loggin utility
    "@storybook/preset-create-react-app": "^3.1.7",         #   CRA integration
    "@storybook/react": "^6.3.2",                           #   React integration
                                                            # testing-library - unit testing made easy
    "@testing-library/cypress": "^7.0.6",                   #   cypress integration
    "@testing-library/react-hooks": "^7.0.0",               #   hooks testing made easy
                                                            # typescript types
    "@types/dompurify": "^2.2.2",                           #   dompurify
    "@types/faker": "^5.5.7",                               #   faker
    "@types/jsonwebtoken": "^8.5.1",                        #   jsonwebtoken
    "@types/lodash": "^4.14.170",                           #   lodash
    "@types/marked": "^2.0.3",                              #   marked
    "@typescript-eslint/eslint-plugin": "^4.25.0",          #   eslint-plugin
    "@typescript-eslint/parser": "^4.25.0",                 #   parser
    "autoprefixer": "^9",                                   # css prefix util
    "cross-env": "^7.0.3",                                  # corss platform environment variables (windows, linux and mac)
    "cypress": "^7.6.0",                                    # Very much like Playwrite and unit testing framework
                                                            # eslint
    "eslint-config-prettier": "^8.3.0",                     #   prettier configuration
    "eslint-import-resolver-typescript": "^2.4.0",          #   typescript type import assistance
    "eslint-plugin-cypress": "^2.11.3",                     #   cypress integration
    "eslint-plugin-import": "^2.23.4",                      #   plugin import - enhaced linting
    "eslint-plugin-jest-dom": "^3.9.0",                     #   jest integration
    "eslint-plugin-jsx-a11y": "^6.4.1",                     #   assessibility
    "eslint-plugin-prettier": "^3.4.0",                     #   prettier
    "eslint-plugin-react": "^7.24.0",                       #   react integration
    "eslint-plugin-react-hooks": "^4.2.0",                  #   react hooks integration
    "eslint-plugin-testing-library": "^4.6.0",              #   testing-library integration
    "faker": "^5.5.3",                                      # generate massive amounts of fake data in the browser and node.js
    "husky": "^6.0.0",                                      # executing git hooks - lint code before it is committed
    "is-ci": "^3.0.0",                                      # checks if current environment is a continual integration server
    "is-ci-cli": "^2.2.0",                                  #   run different cli script when continual integration environment
    "lint-staged": "^11.0.0",                               # lint check staged git files - stops you from committing rubbish
    "msw": "^0.29.0",                                       # mock service worker - rest / graphql api mocking library
    "npm-run-all": "^4.1.5",                                # run multiple npm scripts in parallel or sequential
    "plop": "^2.7.4",                                       # prompt based component / template generator
    "postcss": "^7",                                        # css linter and task automation
    "prettier": "^2.3.0",                                   # opinionated code formatter, it enforces a consistent style by parsing your code
    "react-test-renderer": "^17.0.2",                       # render react component to a dom object for unit testing purposes
    "serve": "^12.0.0",                                     # http server / deamon
    "start-server-and-test": "^1.12.5",                     # http server for testing with cypress
    "tailwindcss": "npm:@tailwindcss/postcss7-compat",      # builds css using shortcuts
    "tsconfig-paths-webpack-plugin": "^3.5.1"
  },
  "msw": {
    "workerDirectory": "public"
  },
  "jest": {
    "moduleNameMapper": {
      "^@/(.+)": "<rootDir>/src/$1"
    },
    "collectCoverageFrom": [
      "src/**/*.{js,jsx,ts,tsx}",
      "!src/**/*.d.ts",
      "!src/**/*.stories.{js,jsx,ts,tsx}",
      "!src/test/**/*.{js,jsx,ts,tsx}"
    ]
  },
  "eslintConfig": {
    "overrides": [
      {
        "files": [
          "**/*.stories.*"
        ],
        "rules": {
          "import/no-anonymous-default-export": "off"
        }
      }
    ]
  },
  "lint-staged": {
    "*.+(ts|tsx)": [
      "yarn lint"
    ]
  }
}
```
