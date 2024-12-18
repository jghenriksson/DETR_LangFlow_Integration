# README: DETR_LangFlow_Integration

This project features a custom component that integrates an API call to an object detection model (ResNet-50), marks the detected components in the image and passes the message to the chatbot that the image was processed and has been made available to the user. This component is intended for local use.

![alt text](https://github.com/jghenriksson/DETR_LangFlow_Integration/tree/main/example_images/buses.jpg)

### Overview
The MessageImageProcessingComponent is a custom component for LangFlow, designed to process images by detecting objects using the Hugging Face detr-resnet-50 model. The component overlays bounding boxes and labels on detected objects in the input image and outputs a modified image along with a text response.

### Features
Object Detection: Utilizes Hugging Face's API for object detection using the detr-resnet-50 model.
Image Modification: Highlights detected objects with semi-transparent overlays and labels.
Customizable: Allows configuration of API keys, cache directories, and save locations.
Seamless Integration: Processes messages containing both text and image files.

### Inputs
Message (message2): A message containing text and an image file for processing.
HuggingFace API Key (api_key): The API key used to access the Hugging Face object detection model.
Cache Directory (cache_directory): Path to the LangFlow cache directory where files are temporarily stored.
Save Directory (save_directory): Path to the directory where the modified image will be saved.

### Outputs
Processed Message (output_message): A message containing the original text with an explanation of the processed image. The modified image is saved to the specified directory.

### How It Works
The component receives a message containing text and an image file.
The image file is read from the cache directory.
An API call is made to the Hugging Face detr-resnet-50 model for object detection.
Detected objects are highlighted with bounding boxes, labels, and confidence scores if they exceed a defined threshold.
The modified image is saved to the specified save directory.
The text message is updated with an explanation of the image processing.

### Requirements
Dependencies:
- langflow
- requests
- Pillow (PIL)

### Example Usage
Upload an image with your message.
Provide your Hugging Face API key.
Specify the cache and save directories.
The component processes the image, detects objects, and returns an updated message along with a saved modified image.

### Notes
Ensure the Hugging Face API key is valid for accessing the detr-resnet-50 model.
The component assumes the input image is in a compatible format.
The detection threshold is set to 0.8 for filtering low-confidence detections.
