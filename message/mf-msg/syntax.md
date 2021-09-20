# Syntax

{% hint style="success" %}
You can escape any format by adding `\` before it!
{% endhint %}

| Name | Syntax | Alternative |
| :---: | :---: | :---: |
| **Bold** | \*\*Bold\*\* | - |
| _Italic_ | \*Italic\* | \_Italic\_ |
| ~~Strikethrough~~ | ~~Strikethrough~~ | - |
| Underlined | \_\_Underlined\_\_ | - |
| Obfuscated | \|\|Obfuscated\|\| | - |
| Legacy color | &cColor! | - |
| Hex | &lt;\#000000&gt;Hex! | &\#000000Hex! |
| Gradient | &lt;g:\#000:\#ffffff&gt;Gradient! | - |
| Rainbow | &lt;r:0.5:1.0&gt;Rainbow! | - |
| Action | \[Text!\]\(hover: Hover Message!\) | - |
| Legacy format | &lBold |  |
| Line break | \n |  |

{% hint style="warning" %}
When using line break on the IDE make sure to escape it `\\n` or it won't work.
{% endhint %}

### Examples

![\*\*Bold\*\* \*Italic\* ~~Strikethrough~~ \_\_underline\_\_ \|\|obfuscated\|\|](../../.gitbook/assets/image%20%282%29.png)

![\*\*\*You can\*\* \_\_also\_\_ ~~parse~~ more\* \_\_\*complex\* \*\*messages\*\*!\_\_](../../.gitbook/assets/image%20%287%29.png)

![&amp;lt;g:\#009FFF:\#ec2F4B&amp;gt;\*\*This\*\* is a \*gradient\* example!](../../.gitbook/assets/image%20%2810%29.png)

![&amp;lt;r:0.5:1.0&amp;gt;\*\*This\*\* is a \*rainbow\* example!](../../.gitbook/assets/image.png)

### Actions

![This is an \[action\]\(hover: &amp;lt;r&amp;gt;Hover message!\) example!](../../.gitbook/assets/image%20%288%29.png)

The syntax for actions are simple, the text that'll be displayed goes in the `[ ]` and the action itself goes in `( )` the currently supported actions are:

* **Hover** - Displays a hover message, `[**Message**](hover: <r>Hover message here!)` both supports the markdown syntax as well.
* **Command** - Runs a command when clicked `[**Message**](command: /home)` if no `/` is present, it'll just say the message in chat instead, when clicking.
* **Suggest** - Suggests a command when clicked`[**Message**](suggest: /home)`
* **Clipboard** - Copies the text to clipboard when clicked`[**Message**](clipboard: This will be copied)`
* **Url** -  Opens a URL link when clicked`[**Message**](url: https://mf.mattstudios.me/)`

{% hint style="info" %}
To have an action with both hover and a click event use the separator `|`, which can also be escaped like `\|`.
Example: `[**Message**](clipboard: This will be copied|hover: Hover message here!)`
{% endhint %}



