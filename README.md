# NCP 관리자

## NCP Admin으로 프론트 엔드와 백 엔드 구성 및 DB 연동 테스트
> NCP Web 관리자단 Frontend + Backend 와 AWS RDS 와의 통신에 초점
<img src="https://github.com/kksung/ssg_CloudDunk/assets/110016279/4c53d03d-df29-412a-bc19-43e4090d36c0" width=870 height=550> <br>



## NCP와 AWS RDS의 연동
- NCP의 BE 서버에서 SSH 터널 설정과 데이터 베이스 연결 설정 코드를 작성
- NCP의 관리자 페이지에서 로그인 및 회원 가입 등이 AWS RDS와 연동
![Untitled](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/08480d68-e52d-4fc1-811d-7dc40966f4c3) <br>



## NCP Admin으로 3 Tier 구성 및 NCP DB 연동 테스트 : db-root 계정 권한 문제

- NCP - BE FLASK —host=0.0.0.0 확인 결과 : 관리자 계정 생성하면 Schema 생성 권한이 없어서 자동으로 Schema 생성 안되는 문제 <br>

![Untitled (3)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/ddef5623-d79b-489b-afa6-3fb49f1127c5) <br>

- NCP에서는 db-root 계정으로 관리자 계정을 생성하면 권한 문제로 Schema가 자동으로 생성이 안됩니다. <br>

![Untitled (1)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/9629a3bf-89bf-4e24-9c34-f97b1ff52a8d) <br>


## NCP db-root 계정 권한 문제 : NCP DB 서버를 AWS RDS로 대체합니다.

AWS는 관리자 계정을 생성하면 Schema가 자동으로 생성됩니다. <br>

AWS ADMIN 계정 권한 <br>
![Untitled (2)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/3d8fda54-4a8b-4b47-91c5-94410554df01) <br>




NCP DB 서버를 삭제하고 AWS RDS 서버 1대로 아키텍처를 구성합니다. <br>

![Untitled (4)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/8ead89b7-c523-4c81-80d8-2455a72866b5) <br>
<NCP 3 Tier> <br>
<br>
<img src="https://github.com/kksung/ssg_CloudDunk/assets/110016279/4c53d03d-df29-412a-bc19-43e4090d36c0" width=870 height=550>
<NCP Admin으로 프론트 엔드와 백 엔드 구성 및 AWS RDS 연동>

<br>
