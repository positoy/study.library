# 유니스 프로그래밍

## man 페이지
- 각 번호로 동일한 명령에 대한 범주화를 갖고 있다
- bash(1), system call(2), api(3), others(5)
- man 1 printf : bash printf 에 대한 설명
- man 3 printf : c printf api 에 대한 설명
- man -a {command} 로 관련된 모든 페이지 조회
- man -k {command} 로 관련된 모든 manual 조회

### 정적링크
- 컴파일타임에 결합
- /lib, /usr/lib, /usr/local/lib/.a
- -static 옵션이 없으면 기본적으로 동적링크로 컴파일
- ar(archive) 유틸리티를 통해서 (object).o 파일들을 합쳐 (archive).a 파일을 만듦
- ar tv {libxx.a} 로 오브젝트 파일 확인 가능
- lipo -info {libxx.a} 로 오브젝트 파일의 target architecture 확인가능

### 동적링크
1. 동적링크
- 프로그램이 로드되면 바로 연결 (printf)
2. 동적로드
- 프로그램 실행 중 자유자재로 로드
- dlopen으로 so(shared object) 파일을 로드하고
- dlsym으로 함수포인터에 동작을 로드해서 사용
- dlclose로 종료

### 심볼스코프
- 라이브러리를 이용할 때 기존 심볼과 api가 유효한지 확인하는 것은 중요하다
- static 이나 scope 기호를 이용해서 심볼의 유효스코프를 제한할 수 있다
- nm -g {library.a} 명령을 통해서 외부에 공개된 심볼을 확인할 수 있다

## pkg-config
- gcc {source code} `pkg-config glib-2.0 --cflags --libs`
- --list-all 설치된 모든 라이브러리 확인
- --cflags는 include directory 표시
- --libs는 library 지정
- \`\` 작은 따옴표는 명령행 실행 전 내부 명령을 실행하여 결과를 치환한다

## doxygen

## gdb

## 시스템콜

# 라이브러리

## ImageMagick
- ImageMagick 으로 pkg-config 컴파일 옵션을 참조하면 core 라이브러리만 연결되어 링킹에러가 발생
- MagickWand 를 사용해야한다

## GUI 프레임워크
- GTK+(Gnome), Qt(KDE), FLTK 등
- gtk-demo 명령으로 구성요소 확인 가능
- GTK+에는 이미처리 라이브러리로 GDK(GIMP Drawing Kit) pixbuf 가 포함돼있다.
- 그 밖에 GLib, Cairo, gdk pixbuf, ATK, Pango, ... 등으로 구성돼있음
- 객체지향 GtkObject<-GtkWidget<-GtkContainer<-GtkBin<-GtkButton
