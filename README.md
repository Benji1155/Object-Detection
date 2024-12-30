
![Object Detection](https://i.imgur.com/enwNE8u.png)

# Object Detection

[![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/Benji1155/Object-Detection)](https://img.shields.io/github/v/release/Benji1155/Object-Detection)
[![GitHub last commit](https://img.shields.io/github/last-commit/Benji1155/Object-Detection)](https://img.shields.io/github/last-commit/Benji1155/Object-Detection)
[![GitHub issues](https://img.shields.io/github/issues-raw/Benji1155/Object-Detection)](https://img.shields.io/github/issues-raw/Benji1155/Object-Detection)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/Benji1155/Object-Detection)](https://img.shields.io/github/issues-pr/Benji1155/Object-Detection)
[![GitHub](https://img.shields.io/github/license/Benji1155/Object-Detection)](https://img.shields.io/github/license/Benji1155/Object-Detection)

**Introduction**

This project focuses on detecting road vehicles across various scenarios. The goal is to develop an application that can accurately detect, categorize, and count vehicles in videos. This has real-world applications in areas like traffic monitoring, autonomous driving, and urban planning. Detecting vehicles can also be applied to object recognition in general. Challenges include processing the videos into usable data and classifying vehicles into categories such as cars, trucks, and buses.

**Images**

![K-Longo](https://i.imgur.com/gV3sTVu.png)

![K-Longo](https://i.imgur.com/enwNE8u.png)

**Project Brief**

The main objective is to create an application that can ingest videos, process them into frames, and detect vehicles. After detection, the application will analyze the results to evaluate accuracy. I found that the model sometimes struggles with accuracy and consistency, which required adjustments during development.
Programming Environment

For this project, I used Jupyter Notebook as the integrated development environment (IDE), which is well-suited for experimentation and data analysis. The entire application was developed in Python due to its vast library support and my personal familiarity with the language. Key libraries used in this project include:

- Pandas and NumPy for data manipulation.
- Tkinter for creating the graphical user interface (GUI) and displaying results.
- Matplotlib for plotting vehicle count results.
- OpenCV (cv2) for handling video processing and managing CSV files.
- Torch for utilizing deep learning models.

To speed up processing, I also leveraged CUDA to enable GPU acceleration.
Dataset Description

The dataset consists of 42 videos of vehicles, each accompanied by corresponding text files containing tracking data. This dataset is ideal for this project because it includes real-world examples of traffic, making it perfect for vehicle detection. Some of the videos were shaky, but this did not affect the results. Additionally, I filmed 5 videos in my local area to test the model further.

For frame extraction, I used OpenCV and extracted every 2nd frame to speed up the processing time.
Implementation Methodology

The core of the vehicle detection is the YOLO (You Only Look Once) model, chosen for its speed, accuracy, and ability to detect a wide range of objects. I configured the model to detect cars, buses, trucks, people, and fire hydrants. The process followed these key steps:

**Initial Setup:**

This served as a baseline to show how the final result should look.

**Training the YOLO Model:**
After understanding the tracking data, I used YOLOv5 to detect vehicles in the videos. I configured YOLO to detect the following objects:
        
- 0 = person
- 2 = car
- 3 = bus
- 5 = motorcycle
- 7 = bicycle
- 10 = fire hydrant

**Adjusting Model Parameters:**
I set a skip rate of 2, meaning every 2nd frame was analyzed to speed up the process. However, I found that this reduced accuracy, so I switched back to processing every frame for better results. For consistency, I applied a buffer to smooth out vehicle count data.

Results Analysis and Key Insights

The results showed accurate tracking of vehicles, with the detection threshold set to 0.5. This threshold ensured that only objects with high confidence were detected, improving accuracy. A lower threshold (0.25) detected smaller, more distant vehicles but resulted in unstable detection.

For example, in the Honda Civic 2018 purple video, the accuracy of the Intersection Over Union (IoU) was:

- With a threshold of 0.5: IoU accuracy = 65.27%
- With a threshold of 0.25: IoU accuracy = 65.28%

The results show that a threshold of 0.5 provided more stable counts, but did not detect distant vehicles, while a threshold of 0.25 detected more distant vehicles but was more variable in detection.
Conclusion

**In conclusion,** I used the YOLOv5 model to detect vehicles in videos. The project required several iterations and adjustments to balance speed, accuracy, and sensitivity. By tweaking the detection threshold and adjusting model parameters, I found that the model can be tailored for different use cases depending on the required sensitivity and accuracy. This application is a good foundation for vehicle detection and could be extended for more complex scenarios or additional object detection.
