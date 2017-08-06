# 스팀잇에서 누가 나랑 가장 친할까? 👪 steemfriend 개발일지 #1

이전 이야기: 스팀잇에서 누가 나랑 가장 친할까? 👪 steemfriend 개발시작? 🚀
(https://steemit.com/kr/@jeongmincha/steemfriend)

![](https://steemitimages.com/0x0/https://steemitimages.com/DQmXYoCFPhnX2etF7xu25i3gZw6ipocDrYuBoy4nBDqgseA/unnamed.jpg)
(출처: vonvon)

지난 번에 steemfriend 를 개발 시작하려고 도메인도 사고 간단하게 아이디어 정리를 해서 글을 올렸었는데요. 이번주 주중에는 다른 일들에 치여서 보지 못하고 있다가 주말이 되서야 살금살금 보기 시작했습니다.

## 개발하면서 첫번째 난관 봉착
저번까지 특정 사용자가 작성한 모든 글의 permlink 를 가져오는 것은 성공하였었습니다. 그 뒤로 각 permlink 들에 대해서 ` getActiveVotes() ` 및 ` getContentReplies() ` 와 같은 함수를 써서 사용자별 보팅, 댓글에 대한 Counter 오브젝트를 구하려고 했습니다. 그런데, asynchronous한 방식으로 처리를 해서 배열이나 오브젝트에 원소를 추가하였더니 얻은 오브젝트 변수에 대해서 원소들이 제대로 추가되지가 않더군요. 추가 후 로그를 찍어보면 로그 상에서는 추가된 데이터를 볼 수 있는데 그 이후 코드에서 핸들링이 안되는 문제가 발생하더라고요 😭

## 대안책
우선 steemjs 말고 다른 쪽을 써야 겠다고 생각했습니다. 데이터 핸들링할 때는 확실히 파이썬이 편해서 파이썬에서 RESTful API 를 써서 불러들이는 식으로 하고 싶은데 그런 식으로 API를 제공해주는 곳이 찾기가 힘들더라구요.. api.steemjs.com 이 있긴 한데, 얘는 web socket이나 steemjs에서 가져온 데이터랑 다른 데이터를 return 해주는 경우가 있어서 쓰지 않기로 마음 먹었습니다;;;

우선은 shell script로 web socket을 다루는 쪽으로 결정했습니다. 자바스크립트로 응용 프로그램이 아닌 데이터 핸들링을 위한 코드는 거의 처음 짜본 경험이었는데, 역시나 언어는 그에 맞는 목적에 맞게 써야 한다는 것을 깨달았습니다 ㅡㅡ;; 

결국 기능상 진척된 건 거의 없는데 저 스스로 삽질을 많이 한 하루였네요.

JS 특성상 어쩔 수 없는 장벽 -> RESTful API 제공해주는 데 없나... -> api.steemjs.com 한 번 시도해보자 -> 같은 쿼리에 대해서 다른 서비스들과는 다른 데이터 반환... -> 그냥 웹소켓 직접 쓰자...

일단 오늘은 졸려서 여기까지 하고 내일 하던지 해야겠네요. 으으...

![](https://img1.steemit.com/480x0/https://steemitimages.com/DQmUdNLJKzrFrZNgsc1c5UkZWHkTwPZj8KXApQcs6deGDK5/follow%20image-min.png)
