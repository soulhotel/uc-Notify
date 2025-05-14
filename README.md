# <p align="center">uc Notify . . </p>

###### <p align="center">. . an attempt at a Notification UI/UX kit. I'll admit I did not even attempt to look into this, or what even classifies as a ui/ux kit. I just wanted to make something I can import into future js projects.</p>

Anyway this is a modern looking notification ui, with  some extended functionality.
- It's easy to invoke: `ucNotify() "show this message" "yes does this" "no does that"`.
- It gives flexibility to the developer by invocating notify on dynamic inputs on the in-script side of things `yes`, can be `whatever`, while `no` can be `nevermind`.
- It gives flexibility by in-script structure: `"ucNotify() "just make sure they see this, yes/no not needed" "okay"`.
- It can be used to pass along input: `"ucNotify() "i need the user to type something" "confirm" "input"`.

1. Usage
    - place `uc-notify folder` into project
    - `import 'uc-notify/uc-notify.js';` inside of module scripts.
    - Summon uc notify via `window.ucNotify("your message")`
    - Summon through functions, buttons, events, state changes
    - Pass along notifications for verification, timers, reminders, errors, etc
    - Pass along y/n functions, customized y/n inputs, parsing automatically handled
    - Pass along User Input (val) via input field, between user, host, function, etc
1. Styling
    - `uc-notify/uc-notify.css` is loaded within `uc-notify.js`
    - styling automatically adjust to dark/light mode systems
    - styling can be overwritten with CSS from any :root


https://github.com/user-attachments/assets/ab77a259-33a2-4977-961f-14965a69f9a2



### Some of the ways ucNotify can be summoned


| Invocation                                                | Message | Yes Label | No Label | Yes Handler | No Handler | Input |
| --------------------------------------------------------- | ------- | --------- | -------- | ----------- | ---------- | ----- |
|  ucNotify("Just a message")                               | ✅      | "Okay"    | ❌       | ❌          | ❌         | ❌    |
|  ucNotify("Message", "Yes")                               | ✅      | "Yes"     | ❌       | ❌          | ❌         | ❌    |
|  ucNotify("Message", "Yes", "No")                         | ✅      | "Yes"     | "No"     | ✅          | ❌         | ❌    |
|  ucNotify("Message", fn1)                                 | ✅      | "Yes"     | ❌       | ✅          | ❌         | ❌    |
|  ucNotify("Message", "Yes", fn1)                          | ✅      | "Yes"     | ❌       | ✅          | ❌         | ❌    |
|  ucNotify("Message", "Yes", "No", "input")                | ✅      | "Yes"     | "No"     | ❌          | ❌         | ✅    |
|  ucNotify("Message", { yes: fn1, no: fn2, input: true })  | ✅      | "Yes"     | "No"     | ✅          | ✅         | ✅    |


| Invocation                                                 | Valid? | Reason                                                          |
| ---------------------------------------------------------- | ------ | --------------------------------------------------------------- |
|  ucNotify("msg")                                           | ✅     | Passive notificaiton, acknowledge or dismiss                    |
|  ucNotify("msg", "Sure")                                   | ✅     | Passive with custom label, acknowledge or dismiss as "Sure"     |
|  ucNotify("msg", "Yes", "No")                              | ❌     | Two buttons but no action — add atleast 1 function              |
|  ucNotify("msg", "Maybe", () => {})                        | ✅     | Custom label and handler {function}                             |
|  ucNotify("msg", "Confirm", "Cancel", () => {})            | ⚠️     | Custom labels, 1 function applied to first label "Confirm"      |
|  ucNotify("msg", "Confirm", () => {}, "Cancel", () => {})  | ✅     | Custom labels, 2 functions applied to both labels               |



| Invocation                                                              | Input Enabled? | Notes                                        |
| ----------------------------------------------------------------------- | -------------- | -------------------------------------------- |
|  ucNotify("Your name?", "This", () => {}, "No", () => {}, "needinput")  | ✅             | Standard way to enable input                 |
|  ucNotify("Confirm action?", () => {}, "needinput")                     | ✅             | Just function + input                        |
|  ucNotify("Save?", "Okay", "needinput")                                 | ✅             | Passive button + input                       |
|  ucNotify("Hello?", "Hi", "Bye")                                        | ❌             | Invalid, no input flag                       |
|  ucNotify("Add to list...", { needinput: true })                        | ✅             | Object-based shorthand                       |
|  ucNotify("Verify your #", "Okay", "needinput")                         | ✅             | Allowed — 2nd arg string, 3rd is "needinput" |


