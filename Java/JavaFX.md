
## Main

Contains the main logic of the app
```java
package com.example.javafxreadingdemo;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.scene.Scene;
import javafx.stage.Stage;

import java.io.IOException;

public class HelloApplication extends Application {
	// good practice to put properties at the top here for easy editing

    @Override
    public void start(Stage stage) throws IOException {
        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));
        Scene scene = new Scene(fxmlLoader.load(), 320, 240); // new scene applies properties and creates object to be rendered
        stage.setTitle("Hello!"); // title of window
        stage.setScene(scene); // sets the scene to be displayed in the window
        stage.show(); // render
    }

    public static void main(String[] args) {
        launch();
    }
}
```

## XML

XML contains the information of what is to be shown in the window, applied from top down with elements stacking on top of each other

```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.geometry.Insets?>
<?import javafx.scene.control.Label?>
<?import javafx.scene.layout.VBox?>

<?import javafx.scene.control.Button?>
// VBox is the root container of the elements
// alignment determines the alignment of elements in the box
// spacing is the spacing between elements in pixels
// xmlns:fx namespace to reference JavaFX attributes and elements
// fx:controller is the controller class for the element, in this case refers back to main HelloController
<VBox alignment="CENTER" spacing="20.0" xmlns:fx="http://javafx.com/fxml"
      fx:controller="com.example.javafxreadingdemo.HelloController">
  <padding>
    <Insets bottom="20.0" left="20.0" right="20.0" top="20.0"/> // padding that adds padding around element
  </padding>

  <Label fx:id="welcomeText"/> // shows welcomming message
  <Button text="Hello!" onAction="#onHelloButtonClick"/> // button with onAction element that points back to the onHelloButtonClick method
</VBox>
```

## Controller file

Contains methods that are called when actions are performed in the view

In JavaFX, the controller class is the glue between the view (the FXML file), and the logic of the application. It contains methods that are called when certain actions are performed in the view, and it can also update the view based on the logic of the application.

The controller class is simply a Java class that is associated with an FXML file using the` fx:controller` attribute in the root element of the FXML file. The controller class must have a public no-argument constructor, and it can have methods that are annotated with @FXML to indicate that they are used to handle events in the view.

```java
package com.example.javafxreadingdemo;

import javafx.fxml.FXML;
import javafx.scene.control.Label;

public class HelloController {
    @FXML // used to inject Label element from the FXML file into the controller (which has the fx:id attribute set to welcomeText). This allows the controller to interact with the Label
    private Label welcomeText;

    @FXML
    protected void onHelloButtonClick() {
        welcomeText.setText("Welcome to JavaFX Application!");
    }
}
```



## Stages
Top-level containers for a JavaFX container. Essentially windows

## Scenes
Content container that attaches to a stage, can only have one active per stage. This is made out of **nodes**, graphical shapes or containers that hold more nodes. Containers can also hold other containers
- Nodes are interactive fields such as buttons, text fields etc, is also known as **controls**
- Topmost node is called **root node**

## Controls
- UI elements that are included in scenes, e.g. buttons, text, fields and labels
- A list of common JavaFX controls and examples can be found [here](https://docs.oracle.com/javase/8/javafx/user-interface-tutorial/ui_controls.htm)
- If what we need doesn't exist, try find a maintained Github repo
![800](Pasted%20image%2020240314213438.png)

## Common Controls
Imported using `import javafx.scene.control.*;`
Or in FXML: `<?import javafx.scene.control.*?>`

| Control         | Description                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------ |
| `Button`        | A button that can be clicked to perform an action.                                               |
| `Label`         | A simple control that displays a single line of read-only text.                                  |
| `TextArea`      | A control that allows the user to enter multiple lines of text.                                  |
| `PasswordField` | A control that allows the user to enter a single line of text, but hides the characters entered. |
| `CheckBox`      | A control that allows the user to select one or more options from a set.                         |
| `RadioButton`   | A control that allows the user to select a single option from a set.                             |
| `ComboBox`      | A control that allows the user to select an item from a drop-down list.                          |
| `ScrollBar`     | A control that allows the user to scroll through a range of values.                              |
| `FileChooser`   | A control that allows the user to select a file from the file system.                            |
| `ProgressBar`   | A control that displays the progress of a task.                                                  |
| `Slider`        | A control that allows the user to select a value from a range of values.                         |
| `ListView`      | A control that displays a list of items, with the ability to select one or more items.           |
| `TableView`     | A control that displays a table of items, with the ability to sort and filter the items.         |
| `TreeView`      | A control that displays a tree of items, with the ability to expand and collapse the tree        |

## JavaFX Packages
- `javafx.scene.chart` gives some pretty fancy charts


## Layout Panes
Import using `import javafx.scene.layout.*;`
Or if in FXML `<?import javafx.scene.layout.*?>`

![700](Pasted%20image%2020240314231237.png)

| Layout       | Description                                                                                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------- |
| `Pane`       | A simple layout container that allows you to place UI controls at specific coordinates.                       |
| `VBox`       | A layout container that arranges its children in a single vertical column.                                    |
| `HBox`       | A layout container that arranges its children in a single horizontal row.                                     |
| `BorderPane` | A layout container that divides its area into five regions: top, bottom, left, right, and center.             |
| `GridPane`   | A layout container that arranges its children in a grid of rows and columns.                                  |
| `FlowPane`   | A layout container that arranges its children in a flow, wrapping to the next line when it runs out of space. |
| `StackPane`  | A layout container that stacks its children on top of each other.                                             |
| `TilePane`   | A layout container that arranges its children in a grid with a fixed number of columns.                       |

## Styling with CSS
**NOT** the same as web CSS
Should be located in the same folder as your FXML file
To be able to use CSS, add the stylesheet to the `start` method: 
```JSX
@Override
public void start(Stage stage) throws IOException {
    String stylesheet = HelloApplication.class.getResource("stylesheet.css").toExternalForm(); // insert here
    scene.getStylesheets().add(stylesheet); // apply here
    // ... rest of the code to create the scene
}
```


```CSS
/* Select all buttons and set the background color to red
and the text color to white */
.button {
    -fx-background-color: #121212;
    -fx-text-fill: white;
    -fx-border-color: white;
    -fx-border-radius: 5;
}

/* Set color of button when mouse hovers over it */
.button:hover {
    -fx-background-color: #2e2e2e;
}

/* Set color of node with fx:id="confirmBtn", targets specific button instead of them all */
#confirmBtn {
    -fx-background-color: #23ad56;
}

.text-field {
    -fx-background-color: #121212;
    -fx-text-fill: white;
    -fx-border-color: white;
    -fx-border-radius: 5;
}

.label {
    -fx-text-fill: white;
}

/* Set the root's color to lightblue */
.root {
    -fx-background-color: #121212;
}
```

### Change specific element 
Using the `fx:id` attribute, we can single out an element. Used as `fx:id="nameHere"`. This can be applied to both CSS and the Controller Class to single out and control elements

## Widgets
Not all widgets are equally suitable for different types of data or tasks. Some widgets are better than others in terms of usability, efficiency, and user satisfaction.

For example, a phone number should be entered using a text field, not a slider.

| Widget        | Use Case                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------- |
| `TextField`   | Entering a name, email, or phone number                                                     |
| `TextArea`    | Entering a description, comment, or message                                                 |
| `ComboBox`    | Selecting a country, state, or category                                                     |
| `DatePicker`  | Selecting a birthdate, appointment, or deadline                                             |
| `FileChooser` | Uploading a photo, document, or video                                                       |
| `CheckBox`    | Agreeing to terms, subscribing to a newsletter, or selecting preferences                    |
| `RadioButton` | Selecting the storage size of a new computer, the color of a product, or the payment method |
| `Slider`      | Adjusting the volume, brightness, or temperature                                            |


## Editor Types
- WYSIWYG
- JavaFX Scene Builder. Downloadable from IntelliJ

