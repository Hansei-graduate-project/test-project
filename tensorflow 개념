텐서플로우(TensorFlow)는 데이터플로우 그래프(Data flow graph)를 사용하여 수치 연산을 하는 소프트웨어로 ,
그래프의 노드(Node)는 수치연산을 나타내고 엣지(edge)는 노드사이를 이동하는 다차원 데이터 배열(tensor)를 나타내준다.

텐서플로우를 사용하기 위한 언어는 파이썬이 대표적이며
수기 숫자 분류와 이미지인식, 워드 임베딩(Word Embedding), RNN(Recurrent Neural Network), 
기계번역을 위한 (Sequence to Sequence)모델, 자연어처리 , PDE(Partial Differential Equation)기반의 
시뮬레이션에 대한 애플리케이션 등이 포함 되어있음

일반버전과 GPU 가속 버전 두가지가 공개 되어 있으며 , 일반버젼은 어떤 컴퓨터에서든 실행할 수 있고, 
GPU가속버전은 GPGPPU를 사용 대량 연산을 빠르게 수행할수 있습니다 .
단 NVIDIA의 GPGPU 언어인 CUDA를 사용하기 때문에 NVIDIA 그래픽카드에서만 작동됩니다.
그외 구글의 자사 서비스를 위한 내부버전은 AI 가속 하드웨어인 TPU(Tensor Processing Unit)에서 동작되어 타사보다 최대30배 더 빠르다고 합니다 .

일반버전: 어느 컴퓨터에서 사용가능
gpu가속버전: gpgppu를 사용 대량연산을 빠르게 수행 단 NVIDIA그래픽카드에서만 작동

텐서플로우(TensorFlow)는 graph로 연산(computation)을 나타내는 프로그래밍 시스템 
graph에 있는 노드는 작업 op(operation)라고 부름
작업은 0개 혹은 그이상의 Tensor를 가질 수 있고 연산도 수행하며 0개 혹은 그 이상의 Tensor를 만들어 내기도 함.

TensorFlow에서 Tenser는 정형화된 다차원 배열
TensorFlow에서 graph는 연산을 표현해 놓은 것이라서 연산을 하려면 graph가 Session 상에 실행 되어야 함
Session은 graph의 작업을 CPU나 GPU같은 Device에 배정하고 실행을 위한 메서드들을 제공

Tensor 	원래 의미는 2차원 이상의 배열이지만 여기 에서는 임의의 차원을 가진 배열을 뜻합니다.
텐서플로우는 방향성 있는 그래픽 구조로써 모델을 구성 하는데 이때 그래프는 0이상의 입출력을 갖는 노드들의 연결체 입니다 .
Operation	임의의 계산을 수행하는 것으로 다양한 속성 값(attribute) 을 가질수 있습니다.

텐서플로우 파이썬 API는 파이썬 2.7과 3.3+을 지원 합니다 .

-용어정리-
 Pip : 파이썬 패키지를 설치하고 관리하는 패키지 매니저 프로그램 
 Virtualenv:  각기 다른 파이썬 프로젝트에서 필요한 패키지들의 버젼이 충돌되지 않도록 다른 공간에서 운영할수 있는 툴로 기존 패키지들을 덮어쓰지 않게 됩니다 .
 아나콘다(Anaconda): 아나콘다는 여러 수학, 과학, 패키지를 기본적으로 포함하고 있는 파이썬 배포판 입니다 .
Anaconda는 "conda" 패키지 매니저를 사용하여 Virtualenv와 유사한 환경 시스템을 제공 합니다 .
 도커 (Docker): 로컬 컴퓨터에서 컨테이너로 리눅스 운영체제를 운영할 수 있는 시스템 입니다 .
 소스에서 설치: 텐서플로우를 pip wheel을 이용하여 빌드하고 설치 합니다 .

