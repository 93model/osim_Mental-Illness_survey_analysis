## MENTAL  ILLNESS Machine Learning Analysis

## ❓ 데이터 소개
OSMI : 개발자 중심의 정신 질환 연구 및 조사 단체

## 🛠 문제
데이터 사이언티스트는 개발자 인가? 라는 의문에서 출발

### 직장의 요인과 관련한 정신질환 정신 질환 치료 경험 (Yes , No) 분류 문제 

## 🧹 데이터 전처리
### feature
| Timestamp               | 시간                                                     |
| ----------------------- | ------------------------------------------------------ |
| Age                     | 나이                                                     |
| Gender                  | 성별                                                     |
| Country                 | 나라                                                     |
| state                   | 미국에 살고 있을시, 살고 있는 주                                    |
| self\_employed          | 자영업자 인가?                                               |
| family\_history         | 정신병력의 가족력이 있는가                                         |
| #treatment#               | #정신 건강 상태에 대한 치료를 받으셨습니까?#                               |
| work\_interfere         | 정신 건강 문제가 있는 경우, 그것이 업무에 방해가 된다고 느끼십니까?                |
| no\_employees           | 몇 명의 직원이 있는 회사에서 일하고 있습니까?(회사의 규모)                     |
| remote\_work            | 시간의 50% 이상을 원격으로(사무실 외부에서) 일하십니까?                      |
| tech\_company           | 주로 기술(Tech) 회사/조직에서 일하는지 여부                            |
| benefits                | 회사에서 정신 건강 관련 혜택을 제공합니까?                               |
| care\_options           | 회사에서 제공하는 정신 건강 관리 옵션을 알고 계십니까?                        |
| wellness\_program       | 직원 건강 프로그램의 일환으로 정신 건강에 대해 논의한 적이 있습니까?                |
| seek\_help              | 회사에서 정신 건강 문제와 도움을 구하는 방법에 대해 자세히 알아볼 수 있는 리소스를 제공합니까? |
| anonymity               | 정신 건강 또는 약물 남용 치료 자원을 이용하기로 선택한 경우 익명이 보호됩니까?          |
| leave                   | 정신 건강 문제로 병가를 내는 것이 용이합니까?                             |
| mentalhealthconsequence | 회사와 정신 건강 문제를 논의하는 것이 부정적인 결과를 초래할 것이라고 생각합니까?         |
| physhealthconsequence   | 회사와 신체 건강 문제를 논의하는 것이 부정적인 결과를 초래할 것이라고 생각합니까?         |
| coworkers               | 동료들과 정신 건강 문제를 논의할 의향이 있습니까?                           |
| supervisor              | 상사와 정신 건강 문제를 논의할 의향이 있습니까?                            |
| mentalhealthinterview   | 면접에서 회사에게 정신 건강 문제를 이야기하시겠습니까?                         |
| physhealthinterview     | 면접에서 회사에게 신체 건강 문제를 이야기하시겠습니까?                         |
| mentalvsphysical        | 회사가 정신 건강을 신체 건강만큼 중요하게 생각한다고 생각하십니까?                  |
| obs\_consequence        | 직장에서 정신 건강 문제가 있는 동료에 대한 부정적인 결과에 대해 듣거나 관찰한 적이 있습니까?  |
| comments                | 추가적 사항 |

- 다양한 성별 결과( Male, Female, Others 로 줄임)
- 국적을 대륙별로 구분
- 연령 대 Feature 을 추가( 0-20, 21-30, 31-65, 66~ )

- Feature Importance 결과,work_interfere 변수의 영향력 너무 크게 나타남 -> 삭제


## 🛠 한계
데이터의 절대적 수가 부족 OSMI Mental Health in Tech Survey : 약 1200개 
미국 중심 : 정신 질환에 대한 개방 정도가 한국과 다름
스스로 실시한 설문조사 : 정신 질환에 관심이 있어서  찾아온 사람들, 치료 비율 높음

## ✔️ 결과
머신러닝 방식 적용 !
RandomForest  + RandomizedSearchCV 사용
하이퍼 파라미터의 최적값 적용. 
적은 데이터의 개수를 극복하기 위해  n_iter=20,  cv=10,사용
최적의 임계값 찾기 idx: 34 , threshold: 0.5542227788687464

![캡처](/img/f1_score.png)

## 🔍 결과 
관측치를 예측하는 특성
![캡처](/img/feature_importance.png)
 
family_history (가족력)
care_options ( 회사에서 제공하는 정신 건강 관리 옵션 )
