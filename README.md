# PKLot-Detact-Model  
 - 주차장 차량 객체 인식  
## Language  
 - <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/python-icon.svg" alt="icon" width="57" height="57" /></div>  

 I. 개발환경 만들기 
1. Pc에서 폴더 만들기  
실습환경에 따라 폴더 이름이 다를수 있어요.   
나는 이곳에 만들고 dataSet폴더를 따로 만들었어요.  
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/a357b6ca-306d-4939-b562-c4a6440ae8d3)  


3. VSCode를 실행하고 
4. 터미널에서 conda 가상 환경  yolov5를 만들었어요.

5. VSCode와 가상환경을 연결하세요 CTRL+SHIFT+P  
6. 새로운 터미널을 열어서 작업을 시작합니다.  
7. git clone로 yolo 가져오기  
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/ff5462e2-a28a-4ea6-ba16-419258e7aee5)  

8. yolo개발 패키지 설치  - pip install -r requirements.txt  
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/9767eeef-b0dd-4f83-a2c4-cec16bc18276)  

II. 데이터세트 준비  
8. 데이터세트 준비   
zip으로 다운로드 받아서 yolov5 폴더 아래에 dataset 폴더를 만들고 그곳에 풀어줌   
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/804a6630-291e-4dea-a1ad-c89358fea499)  


9. dataset 폴더에 있는 data.yaml을 직접 수정 - 폴더의 위치에 집중  
![image](https://github.com/jiwon0629/PKLot-Detact-Model/assets/149983498/0075414c-0778-4c2c-90c4-831ff3d32883)  


우리는 학습을 yolov5 폴더에서 할것이기 때문에 현재 폴더 밑에 ./dataSet이라고 지정을 꼭 하고 저장!  
nc : 5 인것을 기억해 놓기 바랍니다. (custom-yolov5s.yaml에서 사용할 예정)

10. ./models/폴더에 있는 yolov5s.yaml을 복사해서 custom_yolov5s.yaml로 만들기  
그리고 nc : 5로 바꾸어 줍니다.

11. dataset 폴더에 myGlob.py를 만든다(코랩의 내용을 복사)

정상 실행 되면  

3개의 txt파일이 만들어 진다 

이렇게 모든 준비가 끝나면  
III. 학습  
11. data.yaml의 위치가 가장 중요하다.  
python train.py  
--img 416 --batch 16 --epochs 100 --data ./dataSet/data.yaml --cfg ./models/custom_yolov5s.yaml --weights '' --name  
_result --cache  

여기 까지 하게 되면 best.pt를 구할 수 있고 다음은 inference

conda create -n (인터프리터 명) python=3.9  
git clone https://github.com/ultralytics/yolov5  
pip install -r requirements.txt  
cd yolov5  
pip install -r requirements.txt  

[roboflow]  
https://public.roboflow.com/  

dataset설치  
YOLO v5 PyTorch  
download zip to computer  
zip으로 다운로드 받아서 yolov5 폴더 아래에 dataset 폴더를 만들고 그곳에 풀어줌  
