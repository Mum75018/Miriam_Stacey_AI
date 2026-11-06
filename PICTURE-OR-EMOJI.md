# Switching the Bot's Face: Picture or Emoji

All of these changes are in `style.css`. Line numbers can shift as the file is edited, so if they don't match, press **Ctrl+F** and search for the text in the "Find it by searching" column.

## What changes

| Lines | What it is | Find it by searching | Picture version | Emoji version |
|---|---|---|---|---|
| 100 | Emoji variable | `--bot-face: "` | Commented out | **Active** |
| 108 | Picture variable | `--bot-face: url` | **Active** | Commented out |
| 212–220 | Top badge picture rule | Second `.header__badge::before` | **Active** | Commented out |
| 477–489 | Bot message picture rule | Second `.message.assistant::before` | **Active** | Commented out |

**Never change the emoji rules** at lines 201 and 454. When two rules style the same thing, the later one in the file wins. If the picture rules are active, they override the emoji rules. If they are commented out, the emoji rules take effect.

**Commenting out** means putting `/*` before the code and `*/` after it, so the browser ignores it. **Uncommenting** means removing those two marks.

## Switch to the emoji

**1. Swap the two variable lines.**

Line 100 becomes active. Its note after the code can stay as it is.

```css
--bot-face: "🤖";
```

Line 108 gets commented out.

```css
/* --bot-face: url("assets/OIP.jpeg"); */
```

**2. Comment out the top badge picture rule (lines 212–220).**

```css
/* .header__badge::before {
    content: "";
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background-image: var(--bot-face);
    background-size: cover;
    background-position: center;
} */
```

**3. Comment out the bot message picture rule (lines 477–489).**

```css
/* .message.assistant::before {
    content: "";
    position: absolute;
    left: -52px;
    top: -2px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-image: var(--bot-face);
    background-size: cover;
    background-position: center;
    box-shadow: 0 6px 14px rgba(0, 0, 0, 0.35);
} */
```

**4. Save and check.** Press **Ctrl+S**, then refresh the browser with **F5**.

## Switch to a picture

**1. Add the image.** Put it in the `assets` folder, which sits next to `index.html`. Square images work best, because the picture gets trimmed into a circle.

**2. Swap the two variable lines.**

Line 100 gets commented out.

```css
/* --bot-face: "🤖"; */
```

Line 108 becomes active. Change the file name to match your image exactly, including capital letters and the ending, such as `.png` or `.jpeg`.

```css
--bot-face: url("assets/OIP.jpeg");
```

**3. Uncomment both picture rules.** Remove the `/*` and `*/` from around the rules at lines 212–220 and 477–489.

**4. Save and check.** Press **Ctrl+S**, then refresh the browser with **F5**.

## Change to a different emoji or picture

- **Emoji:** with the emoji version active, replace the emoji on line 100 and keep the quotation marks.
- **Picture:** with the picture version active, add the new file to `assets` and change the file name on line 108.

## If something goes wrong

| What you see | Likely cause | Fix |
|---|---|---|
| The circle is empty | The file name or folder name doesn't match | Compare the `url("...")` text with the real names, letter by letter |
| Styles stop working further down the page | A `/*` or `*/` is missing or extra | Check that every `/*` has one matching `*/` |
| The picture appears in one place but not the other | Only one picture rule was uncommented | Uncomment both rules |
| Nothing changed | The file wasn't saved, or the page wasn't refreshed | Press **Ctrl+S**, then **F5** in the browser |

To undo a mistake, press **Ctrl+Z** in the editor, then save again.

**Don't comment out the emoji rule at line 454.** It has comments inside it, and CSS comments can't go inside other comments, so the first `*/` closes your comment early and breaks the CSS.
