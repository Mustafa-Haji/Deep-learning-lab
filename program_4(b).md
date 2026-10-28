
# Program 4(b): Region-Based Image Classification Using VGG16

**Aim:** To generate candidate regions in an image, classify them using the pretrained VGG16 model, and remove overlapping detections using Non-Maximum Suppression (NMS).

**Dataset Used:** User-uploaded traffic image (`traffic 3.jpg`). No separate dataset is used.

**Results:** The program displays the traffic image with green bounding boxes, predicted ImageNet class labels, and confidence scores. It identifies vehicle-related regions, although some bounding boxes or classifications may be inaccurate because VGG16 classifies image regions rather than performing dedicated object detection.
