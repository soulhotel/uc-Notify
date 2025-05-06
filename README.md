# uc-Notify
Notification kit with modern design and dynamic functionality.


### uc Notify - Notification kit

A Notification kit with a modern design and dynamic functionality, made to handle:
1. Usage
    - `import 'uc-notify/uc-notify.js';` inside of module scripts.
    - Summon uc notify via `window.ucNotify("your message")`
    - Summon within functions, mouse clicks, state changes
    - Pass along verification notifications
    - Pass along timers, errors, reminders
    - Pass along yes or no functions through notifications
    - Pass along User Input (val) via input field, between user and function (host)
1. Styling
    - `uc-notify/uc-notify.css` is loaded within `uc-notify.js`
    - styling automatically adjust to dark/light mode systems
    - styling can be overwritten with CSS from any :root


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


Prefered way to use:
