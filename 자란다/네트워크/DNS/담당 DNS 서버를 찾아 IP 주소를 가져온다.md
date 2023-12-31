


```
다음은 DNS 서버에 등록한 정보를 찾아내는 방법입니다
여기에서 중요한 것은 액세스 대상의 웹 서버가 어느 DNS
서버에 등록되어 있는지를 찾아내는 방법입니다

인터넷에는 DNS서버가 수만 대나 있으므로 닥치는대로 뒤지면서 다닐 수는 없습니다. 그래서 다음과 같은 방법을 고안했습니다.
먼저 하위의 도메인을 담당하는 DNS 서버의 IP주소를 그 상위의 DNS 서버에 등록합니다

그리고 상위의 DNS 서버를 또 그 상위의 DNS 서버에 등록하는 식으로 차례대로 등록합니다

즉, lab.glasscom.com이라는 도메인을 담당하는 DNS 서버를 glasscom.com의 DNS 서버에 등록하고, glasscom.com의 DNS 서버를 com 도메인의 DNS 서버에 등록하는 식입니다. 이렇게 하면서 상위의 DNS 서버에 가면 하위의 DNS 서버의 IP 주소를 알 수 있고, 거기에서 조회 메시지를 보낼 수 있습니다.

위의 설멍에서는 com이나 kr라는 도메인(이것을 최상위 도메인이라 함)의 DNS 서버에 하위의 DNS 서버를 등록한 곳에서 끝나는 것처럼 보이지만, 사실은 그렇지 않습니다.

인터넷의 도메인은 com이나 kr의 상위에 또 하나의 루트 도메인이라는 도메인이 있습니다.

루트 도메인에는 com이나 jp라는 도메인명이 없으므로 보통 도메인을 쓸 때는 그것을 생략합니다. 하지만 루트 도메인을 명시적으로 써야 하는 경우에는 www.lab.glasscom.com처럼 끝에 마침표를 찍어서 루트 도메인을 나타내지만, 보통은 그렇게 쓰지 않으므로 루트 도메인의 존재를 알아차리지 못합니다.

이 경우 루트 도메인이 존재하므로 DNS 서버억 com이나 co의 DNS 서버를 등록합니다. 이렇게 해서 하위의 DNS 서버를 상위의 DNS 서버에 등록하여 루트 도메인에서 차례로 아래쪽으로 거슬러 내려갈 수 있습니다.

등록 작업은 한 가지가 더 있습니다. 루트 도메인의 DNS 서버를 인터넷에 존재하는 DNS 서버에 전부 등록하는 것입니다. 이렇게 해서 어느 DNS 서버도 루트 도메인에 액세스할 수 있게 됩니다.

그 결과, 클라이언트에서 어딘가의 DNS 서버에 액세스하면 여기에서부터 루트 도메인을 경유하여 도메인의 계층 아래로 찾아가서 최종적으로 원하는 DNS 서버에 도착합니다.

루트 도메인의 DNS서버에 할당된 IP 주소는 전 세계에 13개 밖에 없고, 좀처럼 변경되지 않으므로 이것을 각 DNS 서버에 등록하는 작업은 어렵지 않습니다. 실제로 루트 도메인의 DNS 서버에 관한 정보는 DNS 서버 소프트웨어와 함께 설정 파일로 배포되어 있으므로 DNS 서버 소프트웨어를 설치하면 자동으로 등록이 완료됩니다.

여기까지가 준비 단계입니다. DNS 서버를 설정할 때여기까지의 등록을 마칩니다. 이로써 DNS 서버는 수만 대 이상 있는 DNS 서버 중에서 원하는 DNS 서버를 찾아낼 수 있는데, 잠시 그 모습을 살펴보죠.


```
