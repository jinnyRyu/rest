# REST

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




```{.java}
	@GetMapping(value = "/getMap")
	public Map<String, SampleVO> getMap() {

		Map<String, SampleVO> map = new HashMap<>();
		map.put("First", new SampleVO(111, "그루트", "주니어"));

		return map;

	}
	map을 이용하는 경우 key에 해당하는 데이터는 xml로 변환되는 경우 태그의 이름이 된다
```
![image](https://user-images.githubusercontent.com/59327680/112715583-615cd300-8f24-11eb-8396-0aa7eacee6dc.png)



### @PathVariable

```{.java}
	@GetMapping("/product/{cat}/{pid}")
	public String[] getPath(@PathVariable("cat") String cat, @PathVariable("pid") Integer pid) {

		return new String[] { "category: " + cat, "productid: " + pid };
	}
```
파라미터로 전달(ex ?)된던 데이터들이 rest방식에서는 경로의 일부로 보내어지는 경우가 많다 <br>
rest 방식에서는 최대한 많은 정보를 url에 담으려하기 때문

요청 :  http://localhost:8080/sample/product/book/11   
결과 : ![image](https://user-images.githubusercontent.com/59327680/112716454-f0201e80-8f29-11eb-82bf-908c4759e077.png)




