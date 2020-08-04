# yolo-v4-tf.keras
A simple tf.keras implementation of YOLO v4

## Quick Start

1. Download official YOLO v4 pre-trained weights from [github AlexeyAB darknet]()
2. Build tf.keras model and load weights
3. Run prediction

    Example:
    ```python
    from models import Yolov4
    model = Yolov4(weight_path='yolov4.weights', 
                   class_name_path='./coco_classes.txt')
    model.predict('input.jpg')
    ```
    
## Training

1. Generate your annotation files (.XML) in VOC format for each images

    *HINT:* An easily used annotation tool: [labelImg](https://github.com/tzutalin/labelImg)
    
    Example for a 2 object xml file
    ```xml
    <annotation>
        <folder>train_img2</folder>
        <filename>yui.jpg</filename>
        <path>/Users/taipingeric/dataset/train_img2/yui.jpg</path>
        <source>
            <database>Unknown</database>
        </source>
        <size>
            <width>465</width>
            <height>597</height>
            <depth>3</depth>
        </size>
        <segmented>0</segmented>
        <object>
            <name>person</name>
            <pose>Unspecified</pose>
            <truncated>1</truncated>
            <difficult>0</difficult>
            <bndbox>
                <xmin>43</xmin>
                <ymin>41</ymin>
                <xmax>430</xmax>
                <ymax>597</ymax>
            </bndbox>
        </object>
        <object>
            <name>person</name>
            <pose>Unspecified</pose>
            <truncated>1</truncated>
            <difficult>0</difficult>
            <bndbox>
                <xmin>60</xmin>
                <ymin>70</ymin>
                <xmax>20</xmax>
                <ymax>207</ymax>
            </bndbox>
        </object>
    </annotation>
    
    ```

2. Convert all XML files to a single .txt file

    Row format: `img_path BOX0 BOX1 BOX2 ...`
    BOX format: `xmin,ymin,xmax,ymax,class_id`
    
    Example:
    ```
    path/to/img1.jpg 50,60,70,80,0 70,90,100,180,2
    path/to/img2.jpg 10,60,70,80,0
    ...
    ``` 

3. Generate class name file, # of lines == # of classes

    Example: coco_classes.txt
    ```
    person
    bicycle
    car
    motorbike
    aeroplane
    bus
    ...
    ```