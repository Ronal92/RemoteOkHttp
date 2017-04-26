					------------------Today's Topic -----------------
								(1) RemoteOkHttp

					-------------------------------------------------

 - 프로젝트 명 : [RemoteOkHttp]

 - 내용 : OkHttp 라이브러리를 사용하여 웹통신을 합니다.[RemoteOkHttp]


#1. RemoteOkHttp


--> 이번 시간에는 OkHttp 라이브러리를 사용해서 웹과 통신해 보겠습니다.

>> HttpUrlConnection이 있는데 왜 OkHttp를 사용할까????

>> 저처럼 궁금해하는 사람들을 위해 아래 그림으로 보여드리겠습니다. 둘다 www.daum.net의 소스 데이터를 가져오는 작업입니다. 하지만! HttpUrlConnection과는 달리 OkHttp 라이브러리를 사용하면 소스코드를 훨씬 적게, 단순하게 구현할 수 있습니다. 

![](http://i.imgur.com/BzQjUro.png)

#1.1 OkHttp 라이브러리

--> 먼저 OkHttp 라이브러리를 안드로이드 app gradle에 추가합니다. 

			compile 'com.squareup.okhttp3:okhttp:3.6.0'

#1.2 코드 사용법

(1) OkHttp 인스턴스를 생성합니다.

						OkHttpClient client = new OkHttpClient();

(2) request 개체를 생성합니다.

						Request request = new Request.Builder().url(url).build();

(3) client  인스턴스에 request를 담아 보냅니다. 즉 서버쪽으로 요청합니다.

						Response response = client.newCall(request).execute();

(4) Response 참조변수 통해 JSON 문자열을 가져올 수 있습니다.

						return response.body().string();

>> 정리 :
>     OkHttp 라이브러리는 HttpUrlConnection 을 쉽게 사용할 수 있게 해줍니다.
    하지만 Thread 처리가 되어 있지 않기 때문에
    Thread 를 사용하는 다른 Api 와 함께 사용해야만 합니다.