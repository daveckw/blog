# README
# Blog

#Generate Welcome Controller with index html
rails generate controller Welcome index

#Generate Articles Controller
$ bin/rails generate controller Articles

#Set the ROUTES
Rails.application.routes.draw do
  get 'welcome/index'
  resources :articles
  root 'welcome#index'
end

#Define new Action
class ArticlesController < ApplicationController
  def new
  end
end

#Create New file the Action
app/views/articles/new.html.erb

#The first form
<%= form_with scope: :article, url: articles_path, local: true do |form| %>
  <p>
    <%= form.label :title %><br>
    <%= form.text_field :title %>
  </p>

  <p>
    <%= form.label :text %><br>
    <%= form.text_area :text %>
  </p>

  <p>
    <%= form.submit %>
  </p>
<% end %>
<%= link_to 'Back', articles_path %>

#Define CREATE Action
class ArticlesController < ApplicationController
  def new
  end

  def create
  end
end

#Generate Article Model
$ bin/rails generate model Article title:string text:text

#RUN Migration
$ bin/rails db:migrate

#Saving the new article
def create
  @article = Article.new(article_params)

  @article.save
  redirect_to @article
end

private
  def article_params
    params.require(:article).permit(:title, :text)
  end

#Define SHOW ACTION
class ArticlesController < ApplicationController
  def show
    @article = Article.find(params[:id])
  end

 #show.html.erb
  <p>
    <strong>Title:</strong>
    <%= @article.title %>
  </p>

  <p>
    <strong>Text:</strong>
    <%= @article.text %>
  </p>
