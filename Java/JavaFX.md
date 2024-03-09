
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

