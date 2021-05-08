---
title: jupyter notebook 커널오류
categories: [School]
comments: true
---

# 문제상황

 jupyter notebook에서 커널에러가 뜸.  
 에러 내용
 ```
 filenotfounderror: [winerror 2] 지정된 파일을 찾을 수 없습니다
 ```

그리고 numpy 를 import하면 import error가 뜨고 에러메세지의 맨 끝에 이런 메세지가 뜬다.  
또한 python파일 또한 실행이 안된다.  
```
 please note and check the following: 
 * the python version is: python3.7 from "c:\src\anaconda\envs\homl2\python.exe" 
 * the numpy version is: "1.19.5" and make sure that they are the versions you expect. 
 please carefully study the documentation linked above for further help. original error was: dll load failed: 지정된 모듈을 찾을 수 없습니다.
 ```
 문제는 아나콘다 프롬프트에서 numpy를 import하면 잘 된다는 점.  
<br/>
<br/>
<br/>

# 해결방법

PATH 확인도 해주고 anaconda를 지웠다 다시 깔아보고 터미널에 conda init 도 해봐도 결과는 똑같았다.  
그런데!! 
<br/>

주피터 노트북 커널이 잘못된 경로에 있는 파이썬을 가리키고 있는게 문제였다.  
아나콘다 프롬프트에서 다음을 입력하여 파이썬 환경의 커널 경로를 확인한다.  
```
jupyter kernelspec list
```

나 같은 경우는 아래와 같은 절대경로가 출력됬다.  
```
C:\Users\jeonj\AppData\Roaming\jupyter\kernels\python3
```
해당 경로로 이동 후 kernel.json 파일을 열고 argv 에 적힌 절대경로를 "python.exe" 로 바꾼다.  
그리고 다시 쥬피터 노트북을 들어갔더니 커널에러가 사라져있고 numpy도 잘 돌아간다.

 
