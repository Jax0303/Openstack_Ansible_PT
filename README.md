# Ansible Infrastructure Setup
 

## 주요 기능

### 1. 기본 시스템 설정 (Base Role)
- 시스템 타임존 설정
- 기본 패키지 설치 (vim, git, curl 등)
- 보안 설정 (SSH, fail2ban)

### 2. 웹 서버 설정 (Web Role)
- Nginx 설치 및 구성
- 기본 웹 페이지 설정
- 가상 호스트 구성

### 3. 데이터베이스 설정 (DB Role)
- PostgreSQL 설치
- 데이터베이스 생성
- 사용자 권한 설정

### 4. 모니터링 설정 (Monitoring Role)
- Prometheus 설치
- Node Exporter 설정
- Grafana 구성

## 사용 방법

1. 환경 설정 - bash
테스트 환경 구축 (Docker)
docker build -t ansible-test .
docker run -d --name tnode1 -p 2222:22 ansible-test

2. Ansible Vault 설정
ansible-vault create vault.yml
ansible-vault encrypt vault.yml

3. 테스트 환경 접속
ssh -p 2222 root@localhost

4. 테스트 환경 접속 후 테스트 실행

ansible-playbook -i hosts.yml install_packages.yml

ansible-playbook -i hosts.yml web_server.yml

ansible-playbook -i hosts.yml database.yml

ansible-playbook -i hosts.yml monitoring.yml

전체 구성 실행  

ansible-playbook -i inventory/hosts site.yml  

특정 역할만 실행  

ansible-playbook -i inventory/hosts site.yml --tags base  

서비스 상태 확인  
sudo service nginx status  
sudo service postgresql status  
sudo service prometheus status  

## 주의사항
- 실제 운영 환경에 적용하기 전에 반드시 테스트 환경에서 검증하세요
- 민감한 정보는 반드시 Ansible Vault를 사용하여 암호화하세요
- 각 역할의 설정은 환경에 맞게 수정이 필요할 수 있습니다

## 라이선스
MIT License
