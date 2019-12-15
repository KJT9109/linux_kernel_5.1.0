v5.1 커널 스터디 소스 저장소
============================

iamroot 16차 커널 스터디 소스 저장소입니다.

저장소 작업 
---------------
간단한 저장소 관련 작업 예입니다.

1. clone

   ``` bash
   $ git clone git@github.com:iamroot16/linux.git
   ```

2. modify

3. push

   ``` bash
   $ git push --all
   ```

커널 compile
------------

1. toolchain 다운로드

   저는 developer.arm.com 에서 다운 받은 toolchain 을 사용했습니다.

   [gcc-arm-8.3-2019.03-x86_64-aarch64-linux-gnu.tar.xz](https://developer.arm.com/-/media/Files/downloads/gnu-a/8.3-2019.03/binrel/gcc-arm-8.3-2019.03-x86_64-aarch64-linux-gnu.tar.xz?revision=2e88a73f-d233-4f96-b1f4-d8b36e9bb0b9&la=en&hash=167687FADA00B73D20EED2A67D0939A197504ACD)

2. 환경설정
   
   arm64 로 CROSS 컴파일하기 위해 환경설정을 합니다.  
   저는 env.sh 라는 설정 파일을 하나 만들어서 source 명령으로 환경을 가져옵니다.
   
   ``` bash
   $ cat > env.sh
   export ARCH=arm64
   export PATH=/opt/linaro/gcc-arm-8.3-2019.03-x86_64-aarch64-linux-gnu/bin:$PATH
   export CROSS_COMPILE=aarch64-linux-gnu-

   $ source env.sh
   ```

3. 커널 config

	default arm64 config 설정을 가져옵니다.

	``` bash
	$ make defconfig
	```

4. 빌드

	``` bash
	$ make -j8
	```

tag 파일 만들기
---------------

커널 소스 navigation을 위해 tag 파일을 만들수 있습니다.  
지원하는 형식은 tags/TAGS cscope gtags 등이 있습니다.  
tag 파일 빌드시에도 환경설정을 가져온 후에 하여야 arch에 맞는 tag
파일이 만들어지니 주의하세요.

``` bash
$ make cscope
또는
$ make gtags
```

이전 자료 링크
--------------

* ARM 아키텍쳐 관련 자료
  A조 스터디때 차상우님이 올려주신 자료로 ARM64 커널 분석시 꼭
  참고해야할 자료 이므로 꼭 다운 받으시기 바랍니다.

  https://github.com/iamroot16a/study/tree/master/참고자료

* vscode 관련 

  https://github.com/iamroot16a/study/tree/master/.vscode

