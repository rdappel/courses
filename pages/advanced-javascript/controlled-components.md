---
title: Controlled Components
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/controlled-components
dev: http://localhost:3006/appel/advanced-javascript/controlled-components
repo: https://github.com/rdappel/courses
---

# What are Controlled Components?

In React, a controlled component is a form element whose value is controlled by React state. Instead of the DOM maintaining its own state (like traditional HTML forms), React becomes the "single source of truth" for the form data.

This gives you full control over the form data and allows you to:

- Validate input as the user types
- Conditionally enable/disable submit buttons
- Transform or format input values
- Synchronize multiple inputs

# Basic Controlled Input

Let's start with a simple example of a controlled text input:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the example:

```javascript
import { useState } from 'react'

const NameForm = () => {
	const [ name, setName ] = useState('')

	return (
		<div>
			<h2>Enter your name</h2>
			<input
				type="text"
				value={name}
				onChange={({ target }) => setName(target.value)}
			/>
			<p>Hello, {name || 'Guest'}!</p>
		</div>
	)
}

export default NameForm
```

> [!NOTE] The key to a controlled component is setting both the `value` prop (from state) and the `onChange` handler (to update state). This creates a two-way binding.

## How It Works

1. The input's `value` is set to the `name` state variable
2. When the user types, the `onChange` event fires
3. The `handleChange` function updates the state with the new value
4. React re-renders the component with the updated state
5. The input displays the new value

> [!IMPORTANT] Without the `onChange` handler, the input would be read-only because React controls its value through state.

# Other Input Types

React's controlled component pattern works with all form elements. Let's look at checkboxes, radio buttons, and select dropdowns:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code I added in the video:

## Checkboxes

```javascript
const [agreed, setAgreed] = useState(false)

<h2>Terms and Conditions</h2>
<label>
	<input
		type="checkbox"
		checked={agreed}
		onChange={({ target }) => setAgreed(target.checked)}
	/>
	I agree to the terms and conditions
</label>
<p>{agreed ? 'Thank you for agreeing!' : 'You must agree to continue.'}</p>
```

## Radio Buttons

```javascript
const [size, setSize] = useState('small')

<h2>Select Size</h2>
<label>
	<input
		type="radio"
		value="small"
		checked={size === 'small'}
		onChange={({ target }) => setSize(target.value)}
	/>
	Small size
</label>
<label>
	<input
		type="radio"
		value="medium"
		checked={size === 'medium'}
		onChange={({ target }) => setSize(target.value)}
	/>
	Medium size
</label>
<label>
	<input
		type="radio"
		value="large"
		checked={size === 'large'}
		onChange={({ target }) => setSize(target.value)}
	/>
	Large size
</label>
<p>You have selected: {size}</p>
```

## Select Dropdown

```javascript
const [country, setCountry] = useState('usa')

<h2>Select Country</h2>
<select value={country} onChange={({ target }) => setCountry(target.value)}>
	<option value="usa">USA</option>
	<option value="canada">Canada</option>
	<option value="mexico">Mexico</option>
</select>
<p>Your selected country: {country}</p>
```

> [!IMPORTANT] For checkboxes, use `checked` instead of `value`, and read from `event.target.checked` instead of `event.target.value`.

# Input Validation

One of the main benefits of controlled components is the ability to validate input in real-time:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the example:

```javascript
const [ email, setEmail ] = useState('')
const [ isEmailValid, setIsEmailValid ] = useState(false)

const handleEmailChange = ({ target }) => {
	const { value, validity } = target
	setEmail(value)
	setIsEmailValid(validity.valid && value !== '')
}

<h2>Enter your email</h2>
<input
	type="email"
	value={email}
	required
	onChange={handleEmailChange}
	style={isEmailValid ? {} : { backgroundColor: 'red'}}
/>
<p>Your email is: {isEmailValid ? email : 'Invalid!'}</p>
```
