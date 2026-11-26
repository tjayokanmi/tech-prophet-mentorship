# HTML Forms: The Complete Idiot's Cheatsheet

A practical, copy-paste reference for building HTML forms—covering basic containers, text inputs, choice controls, validation attributes, and common beginner traps.

---

## 1. The `<form>` Container
Every form starts and ends with a `<form>` tag. It wraps all your inputs and tells the browser where and how to send the data.

```html
<form action="/submit-page" method="POST">
  <!-- Your inputs go here -->
  <button type="submit">Send Form</button>
</form>
```

* **`action="/submit-page"`**: The URL/backend script that receives the form data.
* **`method="GET"`**: Appends form data to the URL (best for search bars; never use for passwords).
* **`method="POST"`**: Sends form data invisibly in the request body (best for logins, signups, and sensitive data).

---

## 2. Labels & Accessibility (`<label>`)
Always pair every input with a `<label>`. Clicking the label automatically focuses or toggles the input.

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

* **Golden Rule:** The label's `for` attribute **must match** the input's `id` attribute.

---

## 3. Single-Line Text & Data Inputs (`<input>`)
The `<input>` tag is self-closing and changes behavior based on its `type` attribute.

| `type` Attribute | Purpose | Example Code |
| :--- | :--- | :--- |
| **`text`** | Standard single-line text | `<input type="text" name="fullname">` |
| **`email`** | Validates `@` and domain format | `<input type="email" name="user_email">` |
| **`password`** | Masks typed characters with dots | `<input type="password" name="pwd">` |
| **`number`** | Numeric input with up/down arrows | `<input type="number" name="age" min="1" max="120">` |
| **`tel`** | Opens numeric keypad on mobile | `<input type="tel" name="phone">` |
| **`url`** | Validates web addresses (`https://...`) | `<input type="url" name="website">` |
| **`date`** | Native calendar date picker | `<input type="date" name="birthday">` |
| **`file`** | File upload selector | `<input type="file" name="resume" accept=".pdf,.doc">` |
| **`hidden`** | Invisible data sent with the form | `<input type="hidden" name="user_id" value="42">` |

> **Note for File Uploads:** If your form includes `<input type="file">`, you **must** add `enctype="multipart/form-data"` to your opening `<form>` tag.

---

## 4. Choice Controls (Radio, Dropdown, Checkbox)

### Quick Comparison
| Control | Tag / Type | How Many Picks? | Best Used For |
| :--- | :--- | :--- | :--- |
| **Radio Button** | `<input type="radio">` | **1** (from 2–5 options) | Yes/No, Gender, Shipping speed |
| **Dropdown** | `<select>` + `<option>` | **1** (from 6+ options) | Country, State, Birth year |
| **Checkbox** | `<input type="checkbox">` | **0, 1, or Many** | Toppings, Interests, "I agree" boxes |

### Radio Buttons (Pick One)
All radio buttons in the same question **must share the exact same `name`**.

```html
<p>Pick your favorite meal:</p>
<input type="radio" id="breakfast" name="meal" value="breakfast" checked>
<label for="breakfast">Breakfast</label><br>

<input type="radio" id="lunch" name="meal" value="lunch">
<label for="lunch">Lunch</label>
```

### Dropdown Menu (Pick One from Many)
Put `name` on `<select>`, and put `value` on each `<option>`. Use `selected` (not `checked`) for defaults.

```html
<label for="country">Country:</label>
<select id="country" name="country">
  <option value="">--Please choose--</option>
  <option value="ng" selected>Nigeria</option>
  <option value="gh">Ghana</option>
  <option value="ke">Kenya</option>
</select>
```

### Checkboxes (Pick Multiple or Agree)
Only checked boxes send their `value` to the server.

```html
<input type="checkbox" id="pepperoni" name="toppings" value="pepperoni" checked>
<label for="pepperoni">Pepperoni</label><br>

<input type="checkbox" id="terms" name="agree_terms" value="yes" required>
<label for="terms">I agree to the Terms</label>
```

---

## 5. Multi-Line Text (`<textarea>`)
Used for long messages, comments, or bios. Unlike `<input>`, it uses an opening and closing tag.

```html
<label for="bio">Bio:</label><br>
<textarea id="bio" name="bio" rows="5" cols="40" placeholder="Tell us about yourself..."></textarea>
```

* **`rows` & `cols`**: Control the visible height (lines) and width (characters).
* **#1 Beginner Trap:** `<textarea>` **does not** use a `value="..."` attribute. Put default text *between* the tags:
  ```html
  <textarea name="bio">Default text goes here.</textarea>
  ```

---

## 6. Grouping & Buttons

### Grouping Related Fields (`<fieldset>` & `<legend>`)
Draws a neat box around related inputs with a title.

```html
<fieldset>
  <legend>Shipping Address</legend>
  <label for="city">City:</label>
  <input type="text" id="city" name="city">
</fieldset>
```

### Form Buttons (`<button>`)
```html
<button type="submit">Submit Form</button> <!-- Sends form data -->
<button type="reset">Clear Form</button>   <!-- Resets all fields to default -->
<button type="button">Click Me</button>    <!-- Does nothing unless wired to JavaScript -->
```

---

## 7. Essential HTML5 Validation & Helper Attributes

| Attribute | Where to Use | What It Does |
| :--- | :--- | :--- |
| **`name`** | Almost all inputs | **Crucial:** Key name used to send data to the server. Without `name`, data is ignored! |
| **`value`** | Inputs & `<option>` | Sets the default text or the data sent when a radio/checkbox is selected. |
| **`placeholder`** | Text inputs & `<textarea>` | Faint hint text inside an empty box that vanishes when typing starts. |
| **`required`** | Inputs, `<select>`, `<textarea>` | Prevents form submission until the field is filled out. |
| **`checked`** | Radio & Checkbox | Pre-selects the option when the page loads. |
| **`selected`** | `<option>` (inside `<select>`) | Pre-selects the dropdown item when the page loads. |
| **`disabled`** | Any form control | Greys out the field, blocks clicks, and **does not** send data on submit. |
| **`readonly`** | Text inputs & `<textarea>` | Blocks editing, but **still sends** the data when submitted. |
| **`maxlength` / `minlength`** | Text inputs & `<textarea>` | Sets maximum or minimum character count. |
| **`min` / `max`** | `number`, `date`, `range` | Sets minimum or maximum allowed numeric/date values. |

---

## 8. Complete Copy-Paste Starter Form

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Registration Form</title>
</head>
<body>

  <form action="/register" method="POST">
    <fieldset>
      <legend>Account Details</legend>

      <label for="name">Full Name:</label><br>
      <input type="text" id="name" name="full_name" placeholder="Jane Doe" required><br><br>

      <label for="email">Email:</label><br>
      <input type="email" id="email" name="email" placeholder="jane@example.com" required><br><br>

      <label for="password">Password:</label><br>
      <input type="password" id="password" name="password" minlength="8" required><br><br>

      <label for="role">Role:</label><br>
      <select id="role" name="role" required>
        <option value="">--Select Role--</option>
        <option value="student">Student</option>
        <option value="developer">Developer</option>
        <option value="designer">Designer</option>
      </select><br><br>

      <p>Experience Level:</p>
      <input type="radio" id="beginner" name="level" value="beginner" checked>
      <label for="beginner">Beginner</label>
      <input type="radio" id="pro" name="level" value="pro">
      <label for="pro">Pro</label><br><br>

      <label for="notes">Additional Notes:</label><br>
      <textarea id="notes" name="notes" rows="4" cols="35" placeholder="Anything else?"></textarea><br><br>

      <input type="checkbox" id="agree" name="terms" value="accepted" required>
      <label for="agree">I agree to the Terms & Conditions</label><br><br>

      <button type="submit">Create Account</button>
      <button type="reset">Reset</button>
    </fieldset>
  </form>

</body>
</html>
```
