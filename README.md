# FreeRTOS 실시간 커널 학습 및 실습 레포지토리

## 개요
본 레포지토리는 "USING THE FREERTOS REAL TIME KERNEL" 문서를 기반으로 FreeRTOS의 핵심 개념을 학습하고 실습하기 위해 구성되었습니다. 모든 실습은 ESP32-WROOM-32D 하드웨어 모듈 환경에서 진행됩니다.

## 참고 문헌
- USING THE FREERTOS REAL TIME KERNEL (FreeRTOS 공식 매뉴얼)

## 대상 하드웨어
- 모듈: ESP32-WROOM-32D
- 아키텍처: Xtensa Dual-Core 32-bit LX6 Microprocessor

## 디렉토리 구조
응용 프로그램 로직(Application Logic)과 하드웨어 추상화 계층(HAL)을 명확히 분리하기 위해 표준 임베디드 디렉토리 구조를 채택합니다.
- `/src` : 애플리케이션 소스 코드
- `/inc` : 헤더 파일
- `/drivers` : ESP32 하드웨어 주변장치 제어 드라이버
- `/bsp` : 보드 지원 패키지 (Board Support Package)

## 주요 학습 목표
1. 태스크 관리 (Task Management): 태스크 우선순위 및 스택 크기의 명시적 할당과 상태 관리 설계.
2. 동기화 및 통신 (Synchronization & Communication): 자원 경쟁(Race Condition) 방지를 위한 뮤텍스(Mutex), 세마포어(Semaphore) 및 큐(Queue)를 활용한 안전한 다중 태스크 제어.
3. 인터럽트 처리 (Interrupt Management): 지연 시간을 최소화하고 자원 소모를 줄이는 짧고 효율적인 인터럽트 서비스 루틴(ISR) 구현.
4. 메모리 관리 (Memory Management): 시스템 안정성을 위한 동적 할당(malloc/free) 지양 및 정적 메모리 할당 중심의 자원 최적화.
5. 시스템 아키텍처 및 안정성: 우선순위 역전(Priority Inversion) 방지 처리, 워치독 타이머(Watchdog Timer) 관리, 복잡한 로직의 유한 상태 기계(FSM) 모듈화.

## 코딩 가이드라인
- MISRA C/C++ 코딩 표준의 엄격한 준수.
- 하드웨어 레지스터 제어 시 비트 마스크 연산 및 `volatile` 키워드의 올바른 사용.
- 공유 메모리 및 자원 접근 시 원자적 연산(Atomic Operation) 필수 적용.
- 하드웨어 메모리 맵 주소값은 `uintptr_t` 또는 `volatile` 포인터로 명확하게 형변환하여 사용.
