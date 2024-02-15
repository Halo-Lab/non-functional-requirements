# Front-End Application Usability

This chapter delves into the usability of applications, focusing on commonly encountered issues and critical aspects of web applications.

## Forms

Creating user-friendly forms poses one of the most intricate challenges in web development. While web designers dedicate significant effort to this task, developers must also understand certain aspects of form design and behavior that are frequently overlooked.
Issues with Submit Buttons

### Submit buttons behaviour

It is considered best practice to disable the submit button after the form is submitted until a response is received. This helps prevent unintentional duplicate submissions. Additionally, employing loading indicators can inform users that their submission is being processed.

Another approach is to initially disable the submit button and only enable it once all required fields are filled. This prevents users from submitting incomplete forms and triggering validation errors. However, this approach also restricts users from receiving immediate feedback, such as a list of errors following an unsuccessful submission. 

### Keyboard Navigation

Keyboard navigation is crucial for ensuring the accessibility of web forms. Here are some recommendations:

- Ensure all interactive elements are focusable.
- Provide clear visual indications for focused elements.
- Use `tabindex` to establish a logical tab order that follows the visual flow of the form.
- Enable keyboard-based form submission for enhanced usability.

### Form Validation

There are two main strategies for form validation. The first is to validate the entire form after a submit attempt. The second is to validate each field after it loses focus (on-blur validation). Both strategies have advantages and disadvantages, so it's important to consider how to use them based on your form's evaluation.

Validation on submit attempt doesn't distract the user from filling out the form, but it may require significant error correction after validation. On the other hand, validation on blur forces the user to immediately correct errors as they occur, ensuring that the user won't encounter annoying errors after submitting the form.

It's common to use validation on submit for small forms with a few fields, while validation on blur is more effective for larger forms. However, sometimes it's beneficial to use elements of both strategies simultaneously. For instance, you can employ validation on submit for small or medium-sized forms, while also using on-blur validation for specific fields with strict rules, such as email addresses or phone numbers.


### Autosaving and Saving Data on Demand

Saving data is crucial for large forms. You can implement autosaving or enable saving form data on demand, for example, by clicking the "Save" button. Here are some recommendations:

- Provide visual feedback to inform the user when data is saved.
- Validate the form before saving data.
- Consider the possibility of saving a partially filled large form, for example, when a user fills some fields and can save data without filling other mandatory fields.

## Errors

It is crucial to be informed about errors in your application not solely from users, but also from error tracking services such as Sentry or Rollbar. For more information about these systems, refer to the Monitoring chapter. Here, we focus on how to handle errors properly.

Errors are inevitable; they occur constantly. When they happen, it's important to inform the user about what has occurred and provide guidance on what they can do. For instance, when a request fails, you can display a message like "Network error. Please try again later or contact the administrator."

This is why it's recommended to use `try/catch` blocks for risky operations such as retrieving or sending data, creating, reading, or writing files, etc.

```javascript
try {
  // Here we attempt to perform a risky operation, for example, requesting data
} catch (error) {
  // Here we handle the error to inform the user or log the error
  alert(`${error.message}. Please try again later or contact the administrator`);
}
```

Note: If you simply log errors to the console, users could be confused. They might even be unaware of the error in some cases. That's why it's crucial to take action for the user within the `catch` block.

