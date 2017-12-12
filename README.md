#### 2. Asked 만들기

**1] app.rb 코드 일부 !**

```
require 'sinatra'

get '/' do
  # 질문을 담기 위한 배열 선언
  @q_list = []

  # 파일 읽기
  # Asked 처럼 메인화면에서 질문을 읽기 위한 코드
  File.open("question.txt", "r") do |f|
    f.each_line do |line|
      # line의 한줄 한줄을 q_list 넣겠다.
      @q_list << line
      # 결과값 -> ["질문 테스트", "두번째 질문 테스트"]
    end
  end

  erb :index
end
```

**2] index.erb 코드 일부 !**

```
<html>
  <head>
    <meta charset="utf-8">
    <title>Asked</title>
  <body>
    <h1>질문해주세요</h1>
    <form action="/ask">
      <select name ="id">
        <option value="anonym">익명</option>
        <option value="my_id">아이디</option>
      </select>
      질문하기 : <input type="text" name="question" placeholder="질문을 입력해주세요.">
      <input type="submit" value="등록">
    </form>
    <h3>-------------------------------------------------------------------------</h3>
    <h1>질문 목록</h1>
    <% @q_list.each do |e| %>
      <p><%= e %></p>
    <% end %>
  </body>
  </head>
</html>
```