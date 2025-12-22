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

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/controlled-components-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/controlled-components-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

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

```javascript
import { useState } from 'react'

const NameForm = () => {
	const [name, setName] = useState('')

	const handleChange = (event) => {
		setName(event.target.value)
	}

	return (
		<div>
			<h2>Enter Your Name</h2>
			<input 
				type="text" 
				value={name} 
				onChange={handleChange}
				placeholder="Type your name..."
			/>
			<p>Hello, {name || 'stranger'}!</p>
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

# Multiple Inputs

When working with forms that have multiple fields, you can manage each input with its own state variable:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState } from 'react'

const UserForm = () => {
	const [firstName, setFirstName] = useState('')
	const [lastName, setLastName] = useState('')
	const [email, setEmail] = useState('')

	const handleSubmit = (event) => {
		event.preventDefault()
		console.log({ firstName, lastName, email })
	}

	return (
		<form onSubmit={handleSubmit}>
			<h2>User Registration</h2>
			<div>
				<label>First Name:</label>
				<input 
					type="text" 
					value={firstName} 
					onChange={(e) => setFirstName(e.target.value)}
				/>
			</div>
			<div>
				<label>Last Name:</label>
				<input 
					type="text" 
					value={lastName} 
					onChange={(e) => setLastName(e.target.value)}
				/>
			</div>
			<div>
				<label>Email:</label>
				<input 
					type="email" 
					value={email} 
					onChange={(e) => setEmail(e.target.value)}
				/>
			</div>
			<button type="submit">Register</button>
		</form>
	)
}

export default UserForm
```

> [!TIP] Using `event.preventDefault()` in the submit handler prevents the browser from refreshing the page, which is the default form behavior.

# Using a Single State Object

For forms with many fields, you can use a single state object instead of multiple state variables:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState } from 'react'

const UserForm = () => {
	const [formData, setFormData] = useState({
		firstName: '',
		lastName: '',
		email: ''
	})

	const handleChange = (event) => {
		const { name, value } = event.target
		setFormData(prev => ({
			...prev,
			[name]: value
		}))
	}

	const handleSubmit = (event) => {
		event.preventDefault()
		console.log(formData)
	}

	return (
		<form onSubmit={handleSubmit}>
			<h2>User Registration</h2>
			<div>
				<label>First Name:</label>
				<input 
					type="text" 
					name="firstName"
					value={formData.firstName} 
					onChange={handleChange}
				/>
			</div>
			<div>
				<label>Last Name:</label>
				<input 
					type="text" 
					name="lastName"
					value={formData.lastName} 
					onChange={handleChange}
				/>
			</div>
			<div>
				<label>Email:</label>
				<input 
					type="email" 
					name="email"
					value={formData.email} 
					onChange={handleChange}
				/>
			</div>
			<button type="submit">Register</button>
		</form>
	)
}

export default UserForm
```

> [!NOTE] The `name` attribute on each input must match the property name in your state object. The square bracket notation `[name]` is used to dynamically access the property.

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

## Checkboxes

```javascript
const [agreed, setAgreed] = useState(false)

<label>
	<input 
		type="checkbox" 
		checked={agreed} 
		onChange={(e) => setAgreed(e.target.checked)}
	/>
	I agree to the terms and conditions
</label>
```

## Radio Buttons

```javascript
const [size, setSize] = useState('medium')

<div>
	<label>
		<input 
			type="radio" 
			value="small" 
			checked={size === 'small'}
			onChange={(e) => setSize(e.target.value)}
		/>
		Small
	</label>
	<label>
		<input 
			type="radio" 
			value="medium" 
			checked={size === 'medium'}
			onChange={(e) => setSize(e.target.value)}
		/>
		Medium
	</label>
	<label>
		<input 
			type="radio" 
			value="large" 
			checked={size === 'large'}
			onChange={(e) => setSize(e.target.value)}
		/>
		Large
	</label>
</div>
```

## Select Dropdown

```javascript
const [country, setCountry] = useState('')

<select value={country} onChange={(e) => setCountry(e.target.value)}>
	<option value="">Select a country...</option>
	<option value="us">United States</option>
	<option value="ca">Canada</option>
	<option value="mx">Mexico</option>
</select>
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

```javascript
import { useState } from 'react'

const EmailForm = () => {
	const [email, setEmail] = useState('')
	const [error, setError] = useState('')

	const validateEmail = (value) => {
		const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
		if (value && !emailRegex.test(value)) {
			setError('Please enter a valid email address')
		} else {
			setError('')
		}
	}

	const handleChange = (e) => {
		const value = e.target.value
		setEmail(value)
		validateEmail(value)
	}

	const handleSubmit = (e) => {
		e.preventDefault()
		if (!error && email) {
			console.log('Valid email:', email)
		}
	}

	return (
		<form onSubmit={handleSubmit}>
			<div>
				<label>Email:</label>
				<input 
					type="email" 
					value={email} 
					onChange={handleChange}
					style={{ borderColor: error ? 'red' : '' }}
				/>
				{error && <p style={{ color: 'red' }}>{error}</p>}
			</div>
			<button type="submit" disabled={!!error || !email}>
				Submit
			</button>
		</form>
	)
}

export default EmailForm
```

> [!TIP] Disable the submit button when the form has validation errors or required fields are empty. This provides immediate feedback to users.

# Formatting Input Values

Controlled components allow you to format or transform input values as the user types:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState } from 'react'

const PhoneForm = () => {
	const [phone, setPhone] = useState('')

	const formatPhoneNumber = (value) => {
		// Remove all non-digits
		const digits = value.replace(/\D/g, '')
		
		// Format as (XXX) XXX-XXXX
		if (digits.length <= 3) {
			return digits
		} else if (digits.length <= 6) {
			return `(${digits.slice(0, 3)}) ${digits.slice(3)}`
		} else {
			return `(${digits.slice(0, 3)}) ${digits.slice(3, 6)}-${digits.slice(6, 10)}`
		}
	}

	const handleChange = (e) => {
		const formatted = formatPhoneNumber(e.target.value)
		setPhone(formatted)
	}

	return (
		<div>
			<label>Phone Number:</label>
			<input 
				type="tel" 
				value={phone} 
				onChange={handleChange}
				placeholder="(555) 555-5555"
			/>
		</div>
	)
}

export default PhoneForm
```

> [!CAUTION] Be careful when formatting input values - make sure the cursor position doesn't jump unexpectedly. Complex formatting might require additional cursor position management.

# Best Practices

1. **Always use controlled components for forms** - They give you complete control over form data
2. **Validate early and often** - Provide immediate feedback to users as they type
3. **Use meaningful names** - Name your state variables and input names clearly
4. **Group related fields** - Consider using a single state object for forms with multiple fields
5. **Prevent default form submission** - Use `event.preventDefault()` to handle submissions yourself
6. **Disable invalid submissions** - Disable the submit button when the form is invalid

> [!TIP] For very large forms, consider using a form library like React Hook Form or Formik to reduce boilerplate code and improve performance.
