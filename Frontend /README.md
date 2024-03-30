
# Frontend

## React

- useState : Every time state changes, it forces a refresh on the page
    - Problem : When a component refreshes , it forces entire page to refresh, may cause slow render performance
    - Solution : Abstract component into its own codebase, forcing state change to happen only within its own codebase
    - More details : Look into Age slider example for edit profile in subme sports

---

## Named exports vs default

Resource : https://medium.com/@etherealm/named-export-vs-default-export-in-es6-affb483a0910

- Using named exports (EX: export function something(){} ), we can do this multiple times in a single file whereas export default can only be written once in a file
- When using named exports you need to destructure it when importing
    - import {testFunction) from ./a.js
- Or you can use it this way
    - import * as aFunctions from ./a.js
        
         aFunctions.testFunction()
        
- When using default exports, you can import it without {} and you can use any name you would like for the imported function/component

---

### Virtualization

https://dev.to/mr_mornin_star/create-a-react-virtualizationwindowing-component-from-scratch-54lj

- When rendering a huge list of items, you can use virtualization to improve render performance of your list-based component

---

## MFE - Microfrontends

Independently deliverable applications / components

- **Pros**
    - Allows for better product ownership of a product
    - MFE can be independently deployed
        - Changes made to MFE immediately reflects on applications that uses MFE
    - UX consistency, fast bug fixes across apps that use it
- **Cons**
    - More complex, module federation to share dependencies can be quite tricky
    - Passing data between MFE’s is tricky, cross component communication is tricky
    - MFE builds at runtime (in the browser when node is running), any error that occurs to the MFE will break the application using it, thus breaking the browser

---

## Module Federation

Used for exposing a module of an application (running on a different host), allowing it to be consumed as an MFE in another remotely hosted application

- The modulefederationlplugin can be used to expose and consume Module Federated Components
- Additional resource : https://www.youtube.com/watch?v=-LMQKc4bVSk
