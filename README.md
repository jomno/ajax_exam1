AJAX RAILS 1
=
ajax 기본 요청
## 준비 사항
* bash
```bash
rails g controller home index
rails g model comment body
rake db:migrate
```
* config/routes.rb
```ruby
[...]
  root 'home#index'
  post 'home/new'
[...]
```
* app/controllers/home_controller.rb
```ruby
[...]
def index
    @comments=Comment.all
end
def new
    Comment.create(body: params[:body])
    redirect_to :back
end
[...]
```
## 요청하기
* app/views/home/index.html.erb
```html
<h1>Ajax 아작내기 1</h1>
<p>ajax 기초편</p>
<form action="/home/new" method="POST" data-remote="true">
    <input type="text" name="body">
    <input type="submit">
</form>
<% @comments.each do |c| %>
    <%= c.body%>
    <hr>
<% end %>
[...]
```
완성!! 응답하기는 다음 [git repo](https://github.com/jomno/ajax_rails2)에 작성되어있습니다.
## Reference post
[괜찮은 블로그](http://wantknow.tistory.com/71)