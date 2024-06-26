# PKLot-Detact-Model  
 - 주차장 차량 객체 인식  
## Language  
 - <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/python-icon.svg" alt="icon" width="57" height="57" /></div>  

 I. 개발환경 만들기 
1. PC에서 폴더 만들기  
  
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/a357b6ca-306d-4939-b562-c4a6440ae8d3)  


3. VSCode를 실행하고 터미널에서 conda 가상 환경 인터프리터를 만든다.  
```
conda create -n (인터프리터 명) python=3.9
```

5. VSCode와 가상환경을 연결  
```
CTRL+SHIFT+P
```  
6. 새로운 터미널을 열어서 작업을 시작한다.  

7. git clone로 yolov5 가져오기  
```
git clone https://github.com/ultralytics/yolov5
```
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/ff5462e2-a28a-4ea6-ba16-419258e7aee5)  

8. yolo개발 패키지 설치  
```
cd yolov5
```
```
pip install -r requirements.txt
```
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/9767eeef-b0dd-4f83-a2c4-cec16bc18276)  

II. 데이터세트 준비  
8. 데이터세트 준비   

[roboflow]  
https://public.roboflow.com/  

dataset설치  
YOLO v5 PyTorch  
download zip to computer  
zip으로 다운로드 받아서 yolov5 폴더 아래에 dataSet 폴더를 만들고 dataSet 폴더에 압축을 풀어준다.  

![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/804a6630-291e-4dea-a1ad-c89358fea499)  


9. dataSet 폴더에 있는 data.yaml을 직접 수정 - 폴더의 위치에 집중

![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/0075414c-0778-4c2c-90c4-831ff3d32883)  


학습을 yolov5 폴더에서 할 것이기 때문에 현재 폴더 밑에 ./dataSet이라고 지정을 꼭 하고 저장  
nc : 2 인것을 기억 (custom-yolov5s.yaml에서 사용할 예정)  

10. ./models/폴더에 있는 yolov5s.yaml을 복사해서 custom_yolov5s.yaml로 만들기   
그리고 nc : 2로 바꾼다.  
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/30369b8e-573b-4fb5-b826-a96f0259617f)  


12. dataSet 폴더에 myGlob.py를 만든다.(코랩의 내용을 복사)  

![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/fd1b5a53-d4cc-4aa3-ad94-ca5b795deee5)  


정상 실행 되면  

3개의 txt파일이 만들어 진다.   
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/c5d61f91-6ec7-44af-8d59-95c442dc5cd2)  


이렇게 모든 준비가 끝나면  

III. 학습  
11. data.yaml의 위치가 가장 중요하다.  
```
python train.py --img 416 --batch 16 --epochs 100 --data ./dataSet/data.yaml --cfg ./models/custom_yolov5s.yaml --weights '' --name  PKLot_result --cache
```
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/00704b4e-84d1-4ed7-8680-46c31e40c7d9)  


여기 까지 하게 되면 best.pt를 구할 수 있고 다음은 inference  
주차공간의 빈자리는 0으로 표시되고 주차가 되어있으면 1로 표시된다.

![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/cf60e796-1481-4eda-b0b6-74ebfda8f4a9)  

![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/c8e2384e-5ee8-4f4d-9dc2-c051f4667e31)  






