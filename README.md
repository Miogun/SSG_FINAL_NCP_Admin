# NCP 관리자

## NCP Admin으로 3 Tier 구성 및 DB 연동 테스트
> NCP Web 관리자단 Frontend + Backend 와 AWS RDS 와의 통신에 초점
<img src="https://github.com/kksung/ssg_CloudDunk/assets/110016279/4c53d03d-df29-412a-bc19-43e4090d36c0" width=870 height=550>
<br>

## NCP와 AWS RDS의 연동
- NCP의 BE 서버에서 SSH 터널 설정과 데이터 베이스 연결 설정 코드를 작성
- NCP의 관리자 페이지에서 로그인 및 회원 가입 등이 AWS RDS와 연동
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6e2230-a696-4d89-8ed2-49e57082f5f1/f5df12ec-801b-4f90-91ae-4928f8bc1b30/Untitled.png)
<br>

## 트러블 슈팅 :  NCP db-root 계정 권한 문제
- NCP에서는 db-root 계정으로 관리자 계정을 생성하면 권한 문제로 Schema가 자동으로 생성이 안됩니다.
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6e2230-a696-4d89-8ed2-49e57082f5f1/5f84f27a-b50e-4e28-acb7-f9b49d177040/Untitled.png)
<br>

## 트러블 슈팅 : 결론

AWS는 관리자 계정을 생성하면 Schema가 자동으로 생성됩니다.

AWS ADMIN 계정 권한
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6e2230-a696-4d89-8ed2-49e57082f5f1/45839245-4e1c-45ad-9501-5db96c27dd62/Untitled.png)
<br>

NCP DB 서버를 삭제하고 AWS RDS 서버 1대로 아키텍처를 구성합니다.
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6e2230-a696-4d89-8ed2-49e57082f5f1/ca19e7c6-339e-4ee5-8091-79fb99125e2a/Untitled.png)
<br>
  
    여러 인스턴스를 번갈아가면서 metric을 당겨오게 되는 문제
  
  - scail-out 된다면 대시보드에서 ASG Instance 하나를 고정적으로 모니터링 수행이 불가
  - scail-out 전 ASG Instance 1개에 대해서는 안정적으로 모니터링 수행 가능

> 따라서 Basic Backend Instance 2개만큼은 안정적으로 모니터링 진행
