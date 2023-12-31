## Personal Information
- **Name** :Mohit Kumar
- **Email** : mohitkumarhans2001@gmail.com
- **Github** : [mohitkumar](https://github.com/mohitkumar0011)
- **LinkedIN** : [mohitkumar](https://www.linkedin.com/in/mohitkumar0011/)
- **University** : Maharaja Agrasen Institute of Technology
- **Major** : Computer Science

## Project Abstract
Jaeger UI is built on React. While we are seemingly already on v18.x of React, the upgrade was not done across the board and 
some other dependencies are still lagging behind, e.g. `"@types/react": "16.8.7"`. It's also blocking upgrades of other 
dependencies. This project is likely to involve a substantial amount of code contribution, as certain upgrade require fixing 
the code to use the new APIs, and sometimes we may run into dependencies that are EOL and need to be replaced altogether. 
### Expected Outcome 
Ideal outcome is to have _all_ dependencies upgraded to the latest versions (with the help of @dependabot) and fix all 
deprecation warnings during the build. But incremental progress towards that goal is also acceptable.


## Introduction
I am a student at Maharaja Agrasen Institute of Technology, pursuing a major in Computer Science. I am a web development enthusiast with proficiency in JavaScript and React. I have made a couple of projects in React and APIs. I came to know about this mentorship via Twitter. I am interested in this program as it aligns with my skill set and will give me an opportunity to upskill myself, learn from my mentors and the community, tackle new challenges, gain exposure to real-world projects. I have the necessary skills like a good understanding of JavaScript, React, etc., which will be helpful on my journey. I am looking forward to an experience full of learning and collaboration.
## Proposed Solution 
We need to update Jaeger UI to the latest version of React that is React 18. 
ReactDOM.render is not available in React 18 so we need to change it to latest version of react , i.e.
```
// Before
import { render } from 'react-dom';

// After
import { createRoot } from 'react-dom/client';
```
Some of the changes to made in jaeger-ui/packages/jaeger-ui/package.json:-
```
// Before

@types/react": "16.8.7"
"@types/react-dom": "18.2.5"
"@types/react-router-redux": "^5.0.21"
"@types/redux-form": "^8.3.5"
"@types/rollup-plugin-visualizer": "^4.2.1"
"@babel/core": "^7.21.0"
"@babel/preset-react": "^7.18.6"
"react": "^18.2.0"
"react-circular-progressbar": "^2.1.0"
"react-dom": "^18.2.0"
"react-ga": "^3.3.1"
"react-helmet": "^6.1.0"
"react-icons": "2.2.7"
"react-redux": "^5.0.6"
"react-router-dom": "4.3.1"
"react-router-redux": "5.0.0-alpha.8"
"react-virtualized-select": "^3.1.0"
"react-vis": "^1.7.2"
"react-vis-force": "^0.3.1"
// After

@types/react: 18.2.20
@types/react-dom: 18.2.7
@types/react-router-redux: 7.1.25
@types/redux-form: 9.9.3
@types/rollup-plugin-visualizer: 4.4.0
@babel/core: ^7.22.10
@babel/preset-react: ^7.22.10
react: ^18.2.10
react-circular-progressbar: ^2.2.4
react-dom: ^18.2.10
react-ga: ^3.3.2
react-helmet: ^6.1.1
react-icons: 4.3.0
react-redux: ^5.0.7
react-router-dom: 5.3.0
react-router-redux: 7.1.25
react-virtualized-select: 3.1.2
react-vis: 1.7.4
react-vis-force: 0.3.2
```

We need to perform similar updates to the dependencies of other folders in Jaeger UI wherever required. As we know that there are some deprecations from React 16 to React 18, so we need to update those as well, for example:

1. **Enzyme Deprecation**: Enzyme is no longer available in React 18. It needs to be replaced with suitable alternatives.

2. **Render Function Deprecation**: The `render` function has been deprecated in favor of the `createRoot` function.

3. **RenderCallbacks Deprecation**: The `renderCallbacks` prop is deprecated. Instead, you should use the `useEffect` hook to perform side effects after a component renders.

4. **getDerivedStateFromProps Deprecation**: The `static getDerivedStateFromProps` method has been deprecated. The `useEffect` hook should be used to update component state based on prop changes.

5. **Modern Features**: Modern features like promises should be incorporated wherever required.

6. **TypeScript Updates**: In TypeScript, several code changes are necessary to align with React 18:
   - The `children` prop must be explicitly listed when defining props.
   - Remove `{}` from `ReactFragment`.
   - `this.context` becomes `unknown`.
   - Remove deprecated types to align with official React types.

Many files in the project currently use the deprecated render function. These should be updated to use createRoot. For example, `page.test.js` currently uses the render function and needs to be changed.
This project aims to update Jaeger UI's dependencies to React 18 and address these deprecations by updating code snippets and functions to the latest versions. The goal is to ensure that Jaeger UI is compatible with React 18 while maintaining code quality and stability.
