package sample;

import javafx.application.Application;
import javafx.fxml.FXMLLoader;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.*;
import javafx.scene.control.Label;
import javafx.scene.control.Slider;
import javafx.scene.layout.HBox;
import javafx.scene.layout.VBox;
import javafx.scene.paint.Color;
import javafx.scene.paint.PhongMaterial;
import javafx.scene.shape.Box;
import javafx.scene.shape.Cylinder;
import javafx.scene.transform.Rotate;
import javafx.scene.transform.Translate;
import javafx.stage.Stage;

public class Main extends Application {
    private Rotate horizontalRotate;
    private Rotate verticalRotate;

    private double horizontalAngle = 0;
    private double verticalAngle = 0;

    public void start(Stage primaryStage) throws Exception{
        horizontalRotate = new Rotate(horizontalAngle, Rotate.Y_AXIS);
        verticalRotate = new Rotate(verticalAngle, Rotate.X_AXIS);

        Label horizontalLabel = new Label("Horizontal");
        Label verticalLabel = new Label("Vertical");

        Slider horizontalSlider = new Slider(0,360,0);
        horizontalSlider.setPrefWidth(100);
        horizontalSlider.setShowTickLabels(true);
        Slider verticalSlider = new Slider(0,360,0);
        verticalSlider.setShowTickLabels(true);
        verticalSlider.setPrefWidth(100);
        HBox hbox = new HBox(10,horizontalSlider,verticalSlider);

        VBox rootNode = new VBox(10);
        rootNode.setAlignment(Pos.CENTER);

        Group shapeGroup = new Group();
        SubScene shapesSub = new SubScene(shapeGroup, 400, 300, true, SceneAntialiasing.DISABLED);

        Cylinder cylinder = new Cylinder(5,10);
        cylinder.getTransforms().add(new Translate(10,0,0));
        cylinder.setMaterial(new PhongMaterial(Color.MEDIUMPURPLE));

        Box box = new Box(5,10,10);
        box.getTransforms().add(new Translate(-5,0,0));
        box.setMaterial(new PhongMaterial(Color.RED));

        shapeGroup.getChildren().addAll(cylinder,box);

        PerspectiveCamera pCamera = new PerspectiveCamera(true);
        pCamera.getTransforms().addAll( new Translate(0, 0, -50));
        shapesSub.setCamera(pCamera);

        cylinder.setOnMouseClicked(event -> {
            horizontalSlider.valueProperty().addListener((observable, oldValue, newValue) -> {
                horizontalAngle = horizontalSlider.getValue();
                horizontalRotate.setAngle(horizontalAngle);
            });
            verticalSlider.valueProperty().addListener((observable, oldValue, newValue) -> {
                verticalAngle = verticalSlider.getValue();
                verticalRotate.setAngle(verticalAngle);
            });
            cylinder.getTransforms().addAll(horizontalRotate,verticalRotate);
        });

        box.setOnMouseClicked(event -> {
            horizontalSlider.valueProperty().addListener((observable, oldValue, newValue) -> {
                horizontalAngle = horizontalSlider.getValue();
                horizontalRotate.setAngle(horizontalAngle);
            });

            verticalSlider.valueProperty().addListener((observable, oldValue, newValue) -> {
                verticalAngle = verticalSlider.getValue();
                verticalRotate.setAngle(verticalAngle);
            });
            box.getTransforms().addAll(horizontalRotate,verticalRotate);
        });

        rootNode.getChildren().addAll(shapesSub,horizontalLabel,horizontalSlider,verticalLabel,verticalSlider);
        Scene myScene = new Scene(rootNode, 500,450);
        primaryStage.setScene(myScene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
