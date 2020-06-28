---
layout: post
title: "[GCP] Cloud Interconnect"
excerpt_separator: "<!--more-->"
categories:
  - Google Cloud Platform
tags:
  - GCP
  - Cloud
---

## Cloud Interconnect
-  Google Network와 온프레미스를 연결하는 서비스

-  Dedicated(전용선)과 Shared(공유)로 나뉘고, Layer2와 Layer3로 구별할 수 있다.

## Interconnect
: RFC1918의 가상 IP 주소를 사용하여 직접 연결하고, SLA 99.9%~99.99%를 보장한다.

: Layer 2 연결, VLAN 사용

: Low Latency 및 High Availability

: 온프레미스와 VPC네트워크 간 IP 대역이 중첩되면 안된다.


**1. Dedicated Interconnect**

 -  온프레미스-Google Network 간 물리적 직접 연결
    (10Gbps x 8링크, 100Gbps x 2링크)

 -  네트워크끼리 대량의 데이터를 전송 가능, 비용 효율적

 -  Colocation facility에서 Google Network와 소유한 라우터 사이의 교차 연결을 준비해야한다.
    (colocation facility는 별도 확인 필요)

 -  또한, BGP 라우팅을 통해 세션을 구성해야한다.

 -  온프레미스쪽 라우팅 장비를 제공해야함 (BGP 사용)

**2. Partner Interconnect**

 -  온프레미스-VPC네트워크를 Service Provider를 통해 연결
    (50Mbps~10Gbps*8링크)
    (service provider는 별도 확인 필요)

 -  Dedicated interconnect colocation facility와 멀거나 필요없을 경우에 사용한다.

 -  페어링 키 사용 - 민감 정보 공유없이 특정 VLAN연결을 식별하기 위한 고유 식별자

## Peering
: 공인 IP를 사용하여 구글 서비스(유튜브, G Suite, Google Cloud APIs)에 접근 제공. (SLA 미보장)


**1. Direct Peering**

-  Google의 광범위한 Edge Network 위치들 중 한 곳과 내 네트워크의 트래픽을 주고 받는다.

-  BGP를 사용한다. 연결이 된 이후에는 Google 및 GCP의 전체 서비스에 연결할 수 있다. 

-  링크당 10Gbps

**2. Carrier Peering**

-  Google의 Peering 요구사항 충족시키지  못하는 경우, Service Provider를 통해 내 네트워크와 구글 서비스를 연결한다.

-  Service Provider 마다 링크당 용량 다름.



