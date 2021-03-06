# Docker and K8s
Docker와 Kubernetes에 대해 간략하게 정리한 내용입니다.

# Docker
Docker는 리눅스 컨테이너를 만들고 사용할 수 있도록 하는 컨테이너화 기술입니다. <br/>

### Docker가 언제 쓰이는가?
우리가 개발을 하기 위해서는 로컬 머신(컴퓨터)과 서비스에 맞는 다양한 개발환경을 세팅해야 합니다. 개발에 필요한 프로그램이나 언어들을 사용가능하도록 다운받고, 버전들을 맞추고 그것들을 결합해야 하죠. <br/>
Front-End를 예로 들면 Visual Studio Code를 설치하고, node, yarn, react.js, jest.. 등등 이와 같은 것들을 일일이 설치하고 세팅해주어야 합니다. <br/> <br/>
그런데 만약 개발을 해야하는 컴퓨터가 바뀌거나, 새로운 개발환경에서 똑같은 서비스를 진행해야한다면 저희는 처음부터 그것들을 모두 다운받고 세팅해야 합니다.  <br/>
그런 번거로운 문제들을 Docker를 활용하여 해결할 수 있습니다. <br/> <br/>
Docker는 앞서 언급한 개발환경에 필요한 환경장비들을 각각, 혹은 그것들이 연결되고 조립된 형태 그대로를 복사할 수 있습니다. 이 복사한 자료들은 우리가 깃 허브를 사용하듯 Docker 허브란 곳에 저장하고, 언제, 어디서든 쉽게 다운받아 설치할 수 있습니다. <br/>
내가 세팅한 개발환경을 쉽게 어디든 설치할 수 있을 뿐만 아니라, 개발환경에 문제가 생기더라도 고칠 필요없이 새로 다운받아서 사용할 수 있는 것입니다. <br/> <br/>
만약 서비스 중인 기존 서버를 새로운 서버로 이전 하거나, 트래픽이 많아져서 서버 수를 늘리게 된다면 똑같은 환경을 서버마다 일일이 세팅하고 설치해 주어야하죠.  <br/>
하지만 Docker를 사용하면 그러한 수고와 시간을 줄이면서 더 효율적으로 환경을 세팅할 수 있게 되는 것입니다.<br/> <br/>
또 개인 컴퓨터인 윈도우 OS에서 개발한 서버를 회사 서버컴퓨터인 우분투에서 돌리는 경우에도 Docker를 활용하면 다른 환경에서 쉽게 동일한 서비스를 세팅하고 돌릴 수 있습니다.  <br/>
### 컨테이너?
Docker에서 개발 환경들은 컨테이너라는 공간에 설치가 되는데, 이 컨테이너들은 같은 물리적공간에서도 독립된 환경을 구축할 수 있도록 해줍니다. <br/> <br/>
이렇게 컨테이너를 활용하여 독립적인 환경을 구축하는 작업이 왜 필요할까요? 예를 들어 서버 하나에서 A서비스와 B서비스를 돌린다고 가정해봅시다. A서비스는 node 4버전을 사용하고, B서비스는 node 7 버전을 사용한다면, 충돌이 날 수 있겠죠. 충돌이 생기는 부분들을 일일이 설정해 주어야합니다. <br/>
이러한 문제를 해결하기 위해 Docker는 컨테이너 단위로 독립적인 개발환경을 제공하면서도, 필요한 부분들은 연결하고 자원도 공유하는 등 효율적인 서비스를 지원합니다. <br/> <br/>
서버를 돌리고 서비스를 진행하다 보면 새로운 요소를 업데이트 해야하거나, 서버에 문제가 생겨서 일부를 수정해야하는 경우가 있을 수 있습니다. 그런 경우 Docker를 사용하지 않는다면, 일일이 현재 동작중인 요소들을 정지하고 수정을 해야합니다. Docker의 경우 새로 수정된 컨테이너로 통째로 교체 하면, 서비스를 중단하지 않고도 업데이트가 가능한 장점이 있습니다. <br/> <br/>
> 가상 컴퓨팅과의 비교 : 가상 컴퓨팅은 실제 물리적인 공간과 자원을 분할해서 사용하기 때문에 성능에 한계가 있습니다. 하지만 Docker는 Docker엔진을 활용하여 실행 환경만을 독립적으로 분할하고 자원은 공유하기 때문에, 로컬 머신에 직접 요소들을 설치한 것과 비슷한 성능을 낼 수 있습니다. 또한 이것저것 설정하거나 설치해야하는 과정이 생략되기 때문에 훨씬 가볍고 빠르게 환경을 구축할 수 있는 것이지요.
