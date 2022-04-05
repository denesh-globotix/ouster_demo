# ouster_demo
This is the instruction set for the ouster demo

## Steps to reproduce the demo
1. Clone the repository
```sh 
git clone https://github.com/fisher-jianyu-shi/yolov5_Ouster-lidar-example && cd yolov5_Ouster-lidar-example && pip install -r requirements.txt 
```

2. Clone the SDK to convert Ouster data to image data for YoloV5
```sh
python3 -m pip install --upgrade pip && python3 -m pip install 'ouster-sdk[examples]' && python3 -m pip list
```

3. Download the following zip file of the car driving on the road into downloads [from this link](https://data.ouster.io/sdk-samples/Rev-06/OS0-128_Rev-06_Urban-Drive_Dual-Returns/OS0-128_Rev-06_Urban-Drive_Dual-Returns.zip) and unzip it

4. Finally visualise the data of the car driving on the road:
```sh
python3 -m ouster.sdk.examples.viz --pcap ~/Downloads/OS0-128_Rev-06_Urban-Drive_Dual-Returns.pcap --meta ~/Downloads/OS0-128_Rev-06_Urban-Drive_Dual-Returns.json
```
5. Pass the data of the car driving on the road into the yolov5 model
```sh
python3 detect_pcap.py --class 0 --weights yolov5s.pt --conf-thres=0.4 --source ~/Downloads/OS0-128_Rev-06_Urban-Drive_Dual-Returns.pcap --metadata-path ~/Downloads/OS0-128_Rev-06_Urban-Drive_Dual-Returns.json --view-img
```
6. Download the [data](https://data.ouster.dev/share/DH414OE1JVYCCGDU) of the 2 people walking: 

7. Pass the data of the 2 peope walking into the yolov5 model:
```sh
python3 detect_pcap.py --class 0 --weights yolov5s.pt --conf-thres=0.4 --source ~/Downloads/Ouster-YOLOv5-sample.pcap --metadata-path ~/Downloads/Ouster-YOLOv5-sample.json --view-img
```

## Reference: 
[Ouster Blog](https://ouster.com/blog/object-detection-and-tracking-using-deep-learning-and-ouster-python-sdk/)