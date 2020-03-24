 # linux 명령어

 ## pwd(print working directory)
 > 현재 작업중인 디렉토리 정보 출력
 ```bash
 $ pwd
 ```

 ## cd(change directory)
 > 경로 이동  
 절대 경로와 상태 경로로 이동 가능.
 > > 절대 경로: 최상위 디렉토리에서 목표 디렉토리까지 전부 기술.  
 상대 경로: 현재 디렉토리에서 목표 디렉토리까지 가는 경로 기술.
```bash
$ cd .. #상위 디렉토리
$ cd - #이전 디렉토리
$ cd / #루트 디렉토리
$ cd ~ #사용자 디렉토리
```


## ls(list)
```bash
$ ls #디렉토리 목록 출력
$ ls -l #디렉토리의 내용을 자세히 출력
$ ls -a #.(숨김파일)을 포함한 모든 파일과 디렉토리 출력
$ ls -al #.(숨김파일)을 포함한 모든 파일과 디렉토리를 자세히 출력
$ ls -R # 현재 디렉토리의 하위 목록까지 전부 출력
```

## cp(copy)
> 파일 혹은 디렉토리를 복사.  
디렉토리를 복사할 때는 -r 옵션을 주어야 함.
```bash
$ ls
testdir/  testfile

$ cp testfile1 testfile_cp
$ ls
testdir/  testfile  testfile_cp

$ cp -r testdir testdir_cp
$ ls
testdir/  testdir_cp/  testfile  testfile_cp
```

## mv(move)
> 파일 혹인 디렉토리를 이동.  
실제로 윈하는 위치로 이동할때도 사용하지만, 이름을 변경하는 용도로도 많이 사용한다.  
cp와 달리 디렉토리를 이동할 때도 옵션이 필요 없다.
```bash
$ ls
testdir/  testfile

$ mv testfile testfile_mv
$ ls
testdir/  testfile_mv

$ mv testfile_mv testdir/
$ ls
testdir/

$ ls testdir/
testfile
```

## mkdir(make directory)
> 디렉토리 생성  
-p옵션을 주면 하위 디렉토리까지 한번에 생성
```bash
$ mkdir testdir
$ ls
testdir/  testfile

$ mkdir -p a/b/c/d/e/
$ ls -R a/
a/:
b/

a/b:
c/

a/b/c:
d/

a/b/c/d:
e/

a/b/c/d/e:
```
## rm(remove)
> 파일이나 디렉토리를 삭제  
디렉토리를 삭제할 대는 -r옵션 추가
-f옵션을 주면 삭제여부를 묻지 않고 바로 삭제  
    *디렉토리를 삭제할 때는 하위까지 삭제되므로 유의
```bash
$ ls
testdir/  testfile1  testfile2

$ rm -f testfile1
$ ls
testdir/  testfile2

$ rm -rf testdir/
$ ls
testfile2
```
## touch
> 파일이나 디렉토리의 최근 업데이트 일자를 현재 시간으로 변경  
파일이나 디렉토리가 존재하지 않으면 생성.
```bash
$ ls -l
total 0
-rw-r--r-- 1 itholic 197121 0 11월  6 22:08 testfile1


$ touch testfile1
$ ls -l
total 0
-rw-r--r-- 1 itholic 197121 0 11월  6 22:43 testfile1


$ touch testfile2
$ ls -l
total 0
-rw-r--r-- 1 itholic 197121 0 11월  6 22:43 testfile1
-rw-r--r-- 1 itholic 197121 0 11월  6 22:44 testfile2
```

## cat(concatenate)
1. 파일의 내용 출력
    ```bash
    $ ls
    file1  file2  file3

    $ cat file1
    1

    $ cat file2
    2

    $ cat file3
    3
    ```
2. 파일 합쳐서 새로운 파일 생성
    ```bash
    $ cat file1 file2 > file1_2
    $ ls
    file1  file1_2  file2  file3

    $ cat file1_2
    1
    2
    ```
3. 기존 한 파일의 내용을 다른 파일에 덧붙이기
    ```bash
    $ cat file1 >> file2
    $ cat file2
    2
    1
    ```
4. 새로운 파일 생성
    ```bash
    $ cat > file4
    hello
    world
    (작성이 끝나면 ctrl +d 로 파일 저장)

    $ cat file4
    hello
    world
    ```
## head
> 파일의 앞부분을 보고 싶은 줄 수 만큼 보여준다(default: 상위 10줄)
 
    ```bash
    head -3 testfile
    head testfile
    ```

## tail
> 파일의 뒷부분을 보고 싶은 줄 수 만큼 보여준다(default: 하위 10줄)

    ```bash
    tail -3 testfile
    tail testfile
    ```
>-F : 파일 내용을 계속 출력, 업데이트되면 갱신하여 출력.  
(실시간 로그파일 모니터링 할 때 이용)

    ```bash
    tail -F testfile
    ```

## find
> 특정 파일이나 디렉토리 검색
> > find [검색경로] -name [파일명]

```bash
$ ls
dir1/  dir3/  file1  file3  picture1.jpg  picture3.jpg
dir2/  dir4/  file2  file4  picture2.jpg  picture4.jpg

$ find ./ -name 'file1'
./file1

$ find ./ -name "*.jpg"
./picture1.jpg
./picture2.jpg
./picture3.jpg
./picture4.jpg
```

> -exec 확장자가 jpg인 파일을 찾아서 바로 삭제

```bash
$ find ./ -name "*.jpg" -exec rm {} \;
$ ls
dir1/  dir2/  dir3/  dir4/  file1  file2  file3  file4
```

> -type : 디렉토리나 파일만 지정해서 검색

```bash
$ find ./ -type d
./
./dir1
./dir2
./dir3
./dir4

$ find ./ -type f
./file1
./file2
./file3
./file4
```

> txt 파일 안의 'hi' 문자열을 'hello'로 변경
```bash
find ./ -name "*.txt" -exec sed -i 's/hi/hello/g' {} \;
```
