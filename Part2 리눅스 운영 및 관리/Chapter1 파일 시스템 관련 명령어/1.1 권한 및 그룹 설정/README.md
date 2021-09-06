## 1.1 권한 및 그룹 설정(1)

### 퍼미션(Permission)  
파일에 어떠한 권한들을 설정할 수 있는지에 대해 살펴보도록 한다.
```
# ls -l
-rw-rw-r-x  1 icbs  project 1024  Aug 13  10:10 client.c
```
* r : read(읽기 가능)
* w : write(쓰기 가능)
* x : execute(실행 가능)  

### 사용자 구분
위 예와 같이 하나의 파일은 rwx 3개를 가지는데, 이것은 각각 **앞에서부터 owner, group, other** 사용자에게 적용되는 권한을 나타낸다.
위 예에서 **icbs는 이 파일의 owner**가 되고 다음에 나오는 **project가 이 파일의 group**이 된다.   
사용자가 파일에 접근할 때 **id가 icbs이면 첫 번째 권한**을 가지고, 사용자가 **project group에 속해 있다면 두 번째 권한**을 가지게 되고, **두 가지 경우가 아니면 other로서 세 번째 권한**을 가진다.

## 권한 및 그룹 설정(2)
### 권한 및 그룹 설정 관련 명령어
#### chmod(파일 권한 바꾸기)
각각의 파일에 주어진 접근권한을 바꿀 때 사용하는 명령어

* 서식
```
chmod [options] mode[,mode] file1[file2...]
chmod [options] 8진수mode[,]
```

* 주요 옵션  

|옵션|의미|
|------|---|
|-c, --changes|권한 변경이 올바른 파일들만 자세히 보여준다.|
|-f, --quite|중요한 오류가 아니라면 보여주지 않는다.|
|-v, --verbose|작업 진행상태를 자세하게 설명해준다.|
|**-R, -recursive**|**디렉터리 안에 있는 파일을 모두 변경한다.**|
|--version|버전 정보를 보여준다.|
|--help|도움말을 보여준다.|  

* 사용예 
```
# ls -l client.c
-rw-r--r--  1 icbs  project 1024  Aug 22  01:22 client.c
# chmod 777 client.c
# ls -l cleint.c
-rwxrwxrwx  1 hsi proeject  1024  Aug 22  01:22 client.c
# chmod u+x cleint.c
# ls -l cleint.c
-rwxr--r--  1 icbs  project 1024  Aug 22  01:22 client.c
```
