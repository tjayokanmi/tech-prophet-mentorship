# HTML Forms Cheatsheet

A quick reference for creating HTML forms, collecting user input, and building accessible forms.

## 1. Basic Form Structure

```html
<form action="/submit" method="POST">
    <!-- Form controls go here -->

    <button type="submit">Submit</button>
</form>
```

| Attribute | Purpose |
|---|---|
| `action` | Specifies where form data is sent. |
| `method` | Specifies how form data is sent. |
| `GET` | Sends form data as URL parameters. |
| `POST` | Sends form data in the request body. |

**Remember:** `POST` does not encrypt data. Use HTTPS to protect data in transit.

## 2. Input Types

The `<input>` element collects different types of user input.

| Input type | Purpose |
|---|---|
| `text` | General text input. |
| `email` | Email address. |
| `password` | Password input. |
| `number` | Numeric input. |
| `tel` | Telephone number. |
| `url` | Website address. |
| `date` | Date selection. |
| `radio` | Select one option from a group. |
| `checkbox` | Select one or more options. |
| `file` | Upload a file. |
| `submit` | Submit a form. |

Example:

```html
<label for="email">Email Address:</label>
<input type="email" id="email" name="email" required>
```

## 3. Labels and Accessibility

A `<label>` gives an individual form control an accessible name.

```html
<label for="fullname">Full Name:</label>
<input type="text" id="fullname" name="fullname">
```

**Important:** The label's `for` attribute must match the input's `id`.

## 4. Grouping Related Controls

Use `<fieldset>` to group related form controls and `<legend>` to describe the group.

```html
<fieldset>
    <legend>Availability</legend>

    <input type="radio" id="online" name="availability" value="online">
    <label for="online">Online</label>

    <input type="radio" id="onsite" name="availability" value="onsite">
    <label for="onsite">Onsite</label>
</fieldset>
```

- `<fieldset>` groups related controls.
- `<legend>` describes the group.
- `<label>` describes an individual control.

## 5. Radio Buttons vs Checkboxes

**Radio buttons:** Choose one option from a group. Use the same `name` for all options in that group.

```html
<input type="radio" id="beginner" name="level" value="beginner">
<label for="beginner">Beginner</label>

<input type="radio" id="advanced" name="level" value="advanced">
<label for="advanced">Advanced</label>
```

**Checkboxes:** Allow users to select multiple options.

```html
<input type="checkbox" id="python" name="interest" value="python">
<label for="python">Python</label>

<input type="checkbox" id="javascript" name="interest" value="javascript">
<label for="javascript">JavaScript</label>
```

## 6. Dropdown Lists

Use `<select>` and `<option>` to create a dropdown list.

```html
<label for="experience">Experience Level:</label>

<select id="experience" name="experience" required>
    <option value="" selected disabled>
        Choose an option
    </option>
    <option value="beginner">Beginner</option>
    <option value="intermediate">Intermediate</option>
    <option value="advanced">Advanced</option>
</select>
```

- `<select>` creates the dropdown.
- `<option>` creates each choice.
- `value` determines the data submitted.
- A disabled, empty placeholder helps prevent accidental selection of the prompt.

## 7. Textarea

Use `<textarea>` when users need to enter longer text.

```html
<label for="message">Your Message:</label>

<textarea
    id="message"
    name="message"
    rows="5"
    cols="40"
    maxlength="500"
    required>
</textarea>
```

| Attribute | Purpose |
|---|---|
| `rows` | Sets the visible number of text lines. |
| `cols` | Sets the visible width in characters. |
| `maxlength` | Limits the number of characters. |
| `required` | Makes the field mandatory. |

## 8. Form Validation Attributes

HTML provides built-in validation attributes.

| Attribute | Purpose |
|---|---|
| `required` | Field must be completed. |
| `minlength` | Minimum number of characters. |
| `maxlength` | Maximum number of characters. |
| `min` | Minimum permitted value. |
| `max` | Maximum permitted value. |
| `pattern` | Requires a value to match a regular expression. |
| `placeholder` | Displays a hint inside a control. |
| `readonly` | Prevents editing while allowing the value to be submitted. |
| `disabled` | Disables a control; its value is generally not submitted. |

Example:

```html
<input
    type="text"
    id="username"
    name="username"
    minlength="3"
    maxlength="20"
    required>
```

## 9. Important Form Attributes

| Attribute | Purpose |
|---|---|
| `id` | Uniquely identifies an element in the document. |
| `name` | Identifies the field when form data is submitted. |
| `value` | Defines the value submitted for a control. |
| `type` | Defines the kind of input control. |

**Do not confuse `id` and `name`:**

- `id` connects a label to its control and identifies the element.
- `name` identifies the data field submitted to the server.
- `value` is the actual value submitted.

## 10. Submit Button

```html
<button type="submit">Submit Application</button>
```

Other button types:

- `submit` — submits the form.
- `reset` — resets form controls to their initial values.
- `button` — a general-purpose button, commonly used with JavaScript.

## 11. Common Beginner Mistakes

1. Forgetting to connect a label's `for` attribute to an input's `id`.
2. Forgetting the `name` attribute on controls that should submit data.
3. Giving radio buttons in the same group different `name` attributes.
4. Forgetting that checkboxes can submit multiple values.
5. Using `<input>` instead of `<textarea>` for long messages.
6. Forgetting to specify the button's `type`.
7. Using duplicate IDs.
8. Assuming `required` replaces proper labels and accessible structure.
9. Assuming `POST` automatically encrypts submitted data.

## 12. Quick Revision Checklist

Before submitting an HTML form assignment, check:

- [ ] Form has an appropriate `action` and `method`.
- [ ] Every data-entry control has a label.
- [ ] Related controls are grouped with `<fieldset>` and `<legend>` where appropriate.
- [ ] Input types match the information being collected.
- [ ] Radio buttons have shared names within each group.
- [ ] Checkboxes have appropriate names and values.
- [ ] Dropdowns contain meaningful options.
- [ ] Required fields have suitable validation.
- [ ] IDs are unique.
- [ ] Submit button has `type="submit"`.
- [ ] Form has been tested in a browser.

---

**Core principle:** A good HTML form should collect the right information, communicate clearly with users, provide appropriate validation, and remain accessible to people using different assistive technologies.
