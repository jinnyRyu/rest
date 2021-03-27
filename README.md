# rest
REST 방식

##### 서버의 역할이 점점 순순하게 데이터에 대한 처리를 목적으로 하는 형태로 진화하고 있음

|어노테이션|기능|
|------|-------|
|@RestController|Controller 가 rest방식을 처리하기 위한 것임을 알려줌|
|@ResponseBody|일반적인 jsp 같은 뷰로 전달하는 것이 아니라 데이터 자체를 전달하기 위한 용도이다|
|@PathVariable|url 경로에 있는 값을 파라미터로 추출할때 사용|
|@CrossOrigin|Ajax의 크로스 도메인 문제를 해결해주는 어노테이션|
|@RequestBody|json 데이터를 원하는 타입으로 바인딩 처리|


```{.java}
	@GetMapping(value = "/getSample", 
			produces = { MediaType.APPLICATION_JSON_UTF8_VALUE,
			MediaType.APPLICATION_XML_VALUE })
	public SampleVO getSample() {

		return new SampleVO(112, "스타", "로드");

	}
  produces는 생략가능 getSample.json 을 요청하면 json 형식의 데이터를 볼 수 있다
```
![image](https://user-images.githubusercontent.com/59327680/112715333-f232af00-8f22-11eb-8001-453d69a25a4a.png)![image](https://user-images.githubusercontent.com/59327680/112715388-39b93b00-8f23-11eb-819f-44dfd6b054d5.png)

