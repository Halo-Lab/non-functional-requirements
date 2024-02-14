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


