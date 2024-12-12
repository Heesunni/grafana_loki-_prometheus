# Grafana Loki Prometheus

## 프로젝트 개요
이 프로젝트는 **Grafana**, **Loki**, **Prometheus**를 활용하여 모니터링 및 로깅을 구현하는 데 중점을 둡니다. 
효율적인 데이터 시각화 및 로깅 솔루션을 제공하며, 애플리케이션의 상태를 실시간으로 모니터링할 수 있습니다.

이 프로젝트는 grafana-prometheus-rdbms 소스를 기반으로 응용하여 개발되었습니다.
---

## 주요 기능

1. **Grafana 대시보드**
   - 실시간 데이터 시각화
   - 커스텀 가능한 위젯 및 차트
   - 다양한 데이터 소스 통합 지원

2. **Loki를 이용한 로깅**
   - 분산 환경에서 로그 집계
   - 간단하고 빠른 로그 쿼리

3. **Prometheus를 이용한 메트릭 수집**
   - 애플리케이션 및 서버 메트릭 수집
   - 경고 설정 및 알림 시스템

4. **Exporter 통합**
   - **mysqld_exporter**: MySQL 데이터베이스 메트릭 수집
   - **node_exporter**: 서버 및 시스템 메트릭 수집
   - **promtail**: Loki와 통합하여 로그 수집 및 전송

---

## 기술 스택

- **Backend:** Prometheus, Loki
- **Frontend:** Grafana
- **Containerization:** Docker, Docker Compose
- **Languages:** YAML (for configuration)

---

## 설치 및 실행 방법

1. **리포지토리 클론**
   ```bash
   git clone https://github.com/Heesunni/grafana_loki_prometheus.git
   cd grafana_loki_prometheus
   ```

2. **Docker Compose 실행**
   ```bash
   docker-compose up -d
   ```

3. **Grafana에 접속**
   - 브라우저에서 `http://localhost:3000`에 접속
   - 기본 로그인 정보:
     - 사용자 이름: `admin`
     - 비밀번호: `admin`

4. **Prometheus 및 Loki 설정**
   - Prometheus: `http://localhost:9090`
   - Loki: 로그 소스 및 Grafana 데이터 소스로 추가

---

## 폴더 구조

```
├── docker-compose.yml       # Docker Compose 설정 파일
├── grafana/                 # Grafana 설정 파일 및 데이터
├── prometheus/              # Prometheus 설정 파일
├── loki/                    # Loki 설정 파일
└── README.md                # 프로젝트 설명 문서
```

---

## 사용 사례

- 애플리케이션 성능 모니터링
- 로그 분석 및 문제 디버깅
- 시스템 경고 및 알림 설정

---

## Prometheus 설정 예시

아래는 Prometheus에서 **mysqld_exporter**, **node_exporter**, **promtail**을 사용하는 예제 설정 파일입니다:

```yaml
# prometheus.yml

global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']

  - job_name: 'mysqld_exporter'
    static_configs:
      - targets: ['localhost:9104']

  - job_name: 'promtail'
    static_configs:
      - targets: ['localhost:9080']
```

위 설정에서는 각 exporter가 로컬 호스트에서 실행 중인 것으로 가정합니다. 필요에 따라 IP 주소나 포트를 수정하세요.

