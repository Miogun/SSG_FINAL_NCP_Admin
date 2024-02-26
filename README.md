# NCP 관리자

## NCP Admin으로 3 Tier 구성 및 DB 연동 테스트
> NCP Web 관리자단 Frontend + Backend 와 AWS RDS 와의 통신에 초점
<img src="https://github.com/kksung/ssg_CloudDunk/assets/110016279/4c53d03d-df29-412a-bc19-43e4090d36c0" width=870 height=550>

<br>

## NCP와 AWS RDS의 연동
- NCP의 BE 서버에서 SSH 터널 설정과 데이터 베이스 연결 설정 코드를 작성
- NCP의 관리자 페이지에서 로그인 및 회원 가입 등이 AWS RDS와 연동
![Untitled](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/08480d68-e52d-4fc1-811d-7dc40966f4c3)

<br>

## NCP db-root 계정 권한 문제
- NCP에서는 db-root 계정으로 관리자 계정을 생성하면 권한 문제로 Schema가 자동으로 생성이 안됩니다.
![Untitled (1)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/9629a3bf-89bf-4e24-9c34-f97b1ff52a8d)

<br>
- NCP - BE FLASK —host=0.0.0.0 확인 결과 : 관리자 계정 생성하면 Schema 생성 권한이 없어서 자동으로 Schema 생성 안되는 문제
![Untitled (3)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/ddef5623-d79b-489b-afa6-3fb49f1127c5)

<br>



## NCP db-root 계정 권한 문제 : AWS RDS로 대

AWS는 관리자 계정을 생성하면 Schema가 자동으로 생성됩니다.

AWS ADMIN 계정 권한
![Untitled (2)](https://github.com/Miogun/SSG_FINAL_NCP_Admin/assets/75124706/a1d6a796-680a-4116-9a81-a6c92d5aec19)

<br>

NCP DB 서버를 삭제하고 AWS RDS 서버 1대로 아키텍처를 구성합니다.
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6e2230-a696-4d89-8ed2-49e57082f5f1/ca19e7c6-339e-4ee5-8091-79fb99125e2a/Untitled.png)
<br>
