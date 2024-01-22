# MyoHMI Android App
A mobile Android application used to implement SFSU ICE lab Myo Human Machine Interface Gesture Recognition Algorithms.

This application is to be paired with either Thalmic Labs Myo Armband, a low cost emg/imu wearable sensor, or to a microcontroller with Bluetooth Low Energy (BLE) capabilities. The app connects to the device via BLE and reads EMG data in real time. EMG signals are subjected to time domain feature extraction and passed to Machine Learning algorithms with the help of the SMILE Java Machine Learning libraries. Deep Learning algorithms implemented using TensorFlow Lite may also be used in which case, time domain feature extraction is optional. After proper training, the app can predict most hand gestures.

This application allows for the user to load and finetune an already-trained neural network model to the mobile device to allow for on-device training using deep learning. While the app stored on this repository already has the trained deep learning model, the user may generate a new one if they wish to customize the characteristics of the network. To do this, the user must first train a deep learning model on their PC by running the program "TensorFlowPC/generate_tflite_model.py" on any Python IDE. The program currently trains a 2-layer CNN on the NinaPro Dataset, though this can be changed. Note that the user must have TensorFlow already installed. The program will generate a "model.tflite" file which contains the trained model. The user must store this file in "/app/src/main/assets/model/". If "CNN" is selected from the classifier list in the mobile app, the user may begin finetuning the loaded model by performing the gestures prompted on-screen. This allows the model to learn the user's specific sEMG signature rather than making predictions based on the NinaPro dataset alone. After finetuning is complete, the app will print predictions generated by the neural network.

This app may also connect to a BLE-equipped microcontroller rather than only connecting to the Myo Armband as was done in previous versions. Unlike with the Myo Armband, a custom microcontroller can be used to sample data from any number of sensors (such as Myoware Muscle Sensors) at any frequency allowed by the BLE module's bandwidth. Therefore, the app shall accomodate this variability by allowing the user to select the number of channels to be sampled, and which of these channels shall be plotted.

NOTE: The app is preconfigured with a pretrained CNN model; you can directly use this app.