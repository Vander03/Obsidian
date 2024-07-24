## 1 Design Patterns
### 1.1 The Model-View-Controller (MVC)
NEED to be used and implemented to maintain good code quality
![700](Pasted%20image%2020240315142802.png)

This design pattern aims to split application information into three parts:
- **Model:** Handles the data:
	- Data management - interacts with databases and performs CRUD operations
	- Business Logic - handles core functionality of the application, including calculations and processing, i.e. the thinking
	- Data Validation - ensures user data matches all required criteria
- **View:** Handles the UI
	- Usually just the XML file
	- Displays data - displays data from the model in readable format
	- Captures user input - e.g. buttons, typing gestures
	- UI Updates - handles updates to the UI when changes to the mode are made (usually with the *Observer Pattern*)
- **Controller:** Manages input, updates Model/view

**Purpose**
- Separation of Concerns: Divides the application into three components, each with a clear responsibility
	- Assits with:
		- Testability
		- Maintainability
		- Scaling
		- Reusability


## 2 Accessibility 

### 2.1 Usability
Usability is a measure of how easy and efficient it is for a user to achieve their goals when using an interface. It is a key factor in the success of any application, and it is important to consider usability when designing a GUI. There are several aspects of usability that you should consider when designing a GUI, including:

| Criterion     | Description                                                                                   | Example                                                                                                                          | Measurement                                |
|---------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------|
| Effectiveness | How well the UI supports users in completing actions accurately and successfully              | A travel booking application should allow users to find and book flights, hotels, and other services without errors or confusion | Completion rate, error rate, accuracy rate |
| Efficiency    | How much time, effort, and resources are required to use the UI and achieve the desired goals | A music streaming app should enable users to access and play their favourite songs quickly and easily                            | Task time, clicks, keystrokes              |
| Satisfaction  | How pleasant, enjoyable, and satisfying the UI is for the users                               | A social media platform should provide users with a positive and engaging experience that meets their needs and expectations     | Ratings, feedback, retention               |

### 2.2 Organisation of information
Information should be organised in a way that is easy to understand and navigate. This can be achieved by using a clear and consistent layout, grouping related information together, and providing clear and meaningful labels for controls. The following criteria are important for the organisation of information:

| Criterion         | Description                                                                         | Example                                                                                                                   | Measurement                             |
|-------------------|-------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|-----------------------------------------|
| Clarity           | Information content conveyed quickly and accurately                                 | A progress bar that shows the status of a file upload                                                                     | Task completion time, user satisfaction |
| Discriminability  | Displayed information distinguished accurately                                      | A color-coded map that shows different regions or categories                                                              | Error rate, user confidence             |
| Conciseness       | No information overload                                                             | A minimalist dashboard that shows only the essential data                                                                 | Cognitive load, user preference         |
| Consistency       | Information is presented in a uniform manner                                        | An application that uses the same styles and information format (e.g., decimal places for currency) across all components | Error rate, user satisfaction           |
| Detectability     | The user's attention is directed towards relevant information                       | A notification that alerts the user about an important event, or a call-to-action button                                  | Task completion time, user satisfaction |
| Legibility        | Information is easy to read                                                         | A font size and contrast that are appropriate for the target audience                                                     | Readability, user comfort               |
| Comprehensibility | The meaning is clearly understandable, unambiguous, interpretable, and recognizable | A label that uses plain language and avoids jargon                                                                        | Comprehension, user feedback            |
### 2.3 User Guidance
In the process of navigating the interface, it is important that the user receive guidance to help them understand how to use the interface. This can be achieved by considering the following aspects:

| Criterion          | Description                                                                                                     | Example                                                                                                            | Measurement                           |
|--------------------|-----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|---------------------------------------|
| Prompts            | Indicating explicitly (specific prompts) or implicitly (generic prompts) that the system is available for input | A blinking cursor in a text field or a voice assistant saying "How can I help you?"                                | User response time, user satisfaction |
| Feedback informing | About the user's input timely, perceptible, and non-intrusive                                                   | A confirmation message after submitting a form or a subtle animation after tapping a button                        | User error rate, user confidence      |
| Status information | Indicating the continuing state of the application, the system's hardware/software and the user's activities    | A progress bar showing the completion of a task or a notification showing the battery level                        | User awareness, user trust            |
| Error management   | Including error prevention, error correction, user support for error management, and error messages             | A validation message preventing invalid input or a clear and helpful error message explaining how to fix a problem | User error rate, user satisfaction    |
| On-line help       | For system-initiated and user initiated requests with specific information for the current context of use       | A tooltip explaining a feature or a help button linking to a relevant documentation page                           | User learning, user satisfaction      |

## 3 Design Elements
### 3.1 [Use appropriate names for each widget]

The name of a widget is the label or text that identifies the widget and its function. It should be clear, concise, and descriptive, so that the user can easily understand what the widget does and how to use it.

For example, a button that submits a form should be named Submit or Save, not Button1 or ClickMe, because the former names indicate the action and the outcome of the button, while the latter names are vague and ambiguous.

### 3.2 [Use an appropriate layout]

The layout of a form is the arrangement and alignment of the widgets on the screen. The layout of a form should be logical so that the user can easily navigate and interact with the form without frustration or confusion.

For example, instead of using a very long but thin VBox, it is better to combine HBox and VBox or other layouts to create a balanced and proportional form. When laying out a form, it is important to consider the size, shape, and position of the widgets, as well as the spacing, padding, and margins between them.

### 3.3 [Use appropriate headings and units to present information]

The heading of a form, or a section of an application, is the title or text that introduces the purpose and scope of the subject. The unit of a data is the symbol or text that indicates the measurement or format of the data, such as meters, kilograms, dollars, etc.

The heading and the unit should be appropriate and accurate, so that the user can easily comprehend the information presented and the required inputs. For example, the heading should be relevant and specific, such as Personal Details or Payment Options, not Form1 or Data Entry.

### 3.4 [Use consistent output formats (e.g. money as 2 decimal places)]

The output format of a data is the way the data is displayed or stored in the system, such as the number of digits, the decimal separator, the date format, etc. The output format of a data should be consistent and correct, so that the user can easily interpret and compare the data.

For example, money should be displayed or stored as 2 decimal places, such as $12.34, not $12.3456 or $12.3, because the former format is more precise and standard, while the latter formats are more ambiguous and irregular.

### 3.5 [Use tool tips to provide help]

A tool tip is a small pop-up window that appears when the user hovers over or clicks on a widget, and provides additional information or guidance about the widget. A tool tip should be used to provide help to the user, such as explaining the function or the usage of the widget, or giving a hint or a warning about the input or the output of the widget.

For example, in JavaFX, you can use the setTooltip(Tooltip) method to set a tool tip for a widget, like submitButton.setTooltip(new Tooltip("Click to submit the form. You cannot undo this action."));.

### 3.6 [Report when each of the functionality is in progress, completed, or failed, along with any messages or errors]

The functionality of a form is the action or the result that the form performs or produces, such as validating, submitting, saving, etc. The functionality of a form should be reported to the user, so that the user can know the status and the outcome of the form.

For example, in JavaFX, you can use the ProgressBar widget to show the progress of a task, and you can use the setProgress(double) method to set the progress of the bar. This widget shows the user how much of the task has been completed and how much is remaining.

You can also use the Alert or Dialog widget to show messages or errors to the user, such as confirming the success or the failure of the task, or explaining the reason or the solution of the error.

### 3.7 [Allow or not allow users to interact with a widget under some circumstances]

The interaction of a form is the input or the output that the user or the system provides or receives, such as typing, clicking, selecting, etc. The interaction of a form should be controlled by the system, so that the user can only interact with the widgets that are relevant and available for the current situation.

For example, in JavaFX, you can use the setDisable(boolean) method to disable / enable a widget (true to disable, false to enable). This method prevents or allows the user to interact with the widget, such as entering data, pressing a button, or choosing an option, especially when the application depends on the completion of a previous task or the satisfaction of a certain condition.




### 3.8 Use of Colours
- Consider colourblind people in design
	- Caused by missing red, green or blue cones in the eye, meaning those colours aren't seen correctly
	- Red-green colour blindness is the most common
- Do not use colour as the only way to identify something important
	- Line Graphs - use dotted lines, dashed lines etc
	- Bar Graphs - use different fill textures
	- Required fields in form: use asterisk
	- Avoid red -green gradients, blue-red works well
	- Can upload UI to colour blindness simulator
		- https://daltonlens.org/colorblindness-simulator
	- Check colours with colour accessibility tool
		- https://color.adobe.com/create/color-accessibility
	- 
![700](Pasted%20image%2020240315150550.png)


### 3.9 Use of Fonts
- Choose a legible font: Sans-serif fonts preferred (Arial, Helvetica, Vedana)
- Use reasonable font size: ensure it is affected by system scale, fonts appear smaller on high dpi devices
- Check font contrast: minimum of 5:1 contrast for header, 7:1 for body

### 3.10 Keyboard Navigation
- One handed operation: some users can't use both hands or don't own a mouse. Application should be able to function with just a keyboard
- Keyboard shortcuts: Assign keyboard shortcuts to common actions
- Use standard navigational controls: Arrows, tab controls, action cancelling, focus activation
- **Common shortcuts:**
	- **TAB** to move the focus
	- **Shift+TAB** to move backwards in the focus
	- **Spacebar** to check/uncheck a textbox
	- **Arrow Keys** to change the selection of the radio buttons, to move in a drop-down list, or to scroll (scrollbar) when available
	- **Return key** to activate the element that has the focus (link, button, menu)

### 3.11 Error Feedback
- **Clear Error Messages:** When there is an invalid user input, clearly highlight where it is and what is wrong
- **Avoid Error Messages:** Where possible, prevent errors from occurring or suggest solutions


### 3.12 Data validation
- **Constrain Input:** only allow input of the correct type to be entered
- **Highlight Errors:** if theres an error in the input, highlight exactly where it is
- **Clearly label required fields**


## 4 Resources
**Colour Palette Generator:** [Adobe Colour Wheel](https://color.adobe.com/create/color-wheel)
**Styling Library:** [JFoenix](https://github.com/sshahine/JFoenix), [BootstrapFX](https://github.com/kordamp/bootstrapfx)
**Follow UI Design Patterns:** https://ui-patterns.com/
