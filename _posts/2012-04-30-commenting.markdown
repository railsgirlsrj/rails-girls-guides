---
layout: default
title: Permita Comentários no seu App
permalink: adicione-comentarios
---
# Permita Comentários no seu App
*Criado por Janika Liiv, [@janikaliiv](https://twitter.com/janikaliiv)*

Nós vamos adicionar a possibilidade de comentar em idéias na sua aplicação.

## *1.*Crie o scaffold para Comentários

Crie um scaffold para Comentários, com o nome de quem está comentando, o corpo (body) do comentário e com a referência para a tabela de idéias. (`idea_id`).

{% highlight sh %}
rails g scaffold comment user_name:string body:text idea_id:integer
{% endhighlight %}

Isso vai criar um arquivo de migração que avisa ao seu banco de dados sobre a nova tabela de comentários. Rode a migração usando:

{% highlight sh %}
rake db:migrate
{% endhighlight %}

## *2.*Adicione relationamentos aos modelos

Você precisa ter certeza de que o Rails conhece o relationamento entre os objetos (idéias e comentários).
Como uma idéia pode ter muitos comentários nós temos que ter certeza de que o modelo de Idéias (idea), sabe disso isso.

Abre o arquivo app/models/idea.rb e depois da linha
{% highlight ruby %}
class Idea < ActiveRecord::Base
{% endhighlight %}
adicione
{% highlight ruby %}
has_many :comments
{% endhighlight %}

O comentário também precisa saber que pertence a uma Idéia. Então abra o arquivo `app/models/comment.rb` e depois da linha
{% highlight ruby %}
class Comment < ActiveRecord::Base
{% endhighlight %}

adicione a linha
{% highlight ruby %}
belongs_to :idea
{% endhighlight %}

## *3.*Renderize o formulário de comentários e os formulários existentes

Abra o arquivo app/views/ideas/show.html.erb e depois da image_tag
{% highlight erb %}
<%= image_tag(@idea.picture_url, :width => 600) if @idea.picture.present? %>
{% endhighlight %}

adicione
{% highlight erb %}
<h3>Comentários</h3>
<% @comments.each do |comment| %>
  <div>
    <strong><%= comment.user_name %></strong>
    <br />
    <p><%= comment.body %></p>
    <p><%= link_to 'Delete', comment_path(comment), method: :delete, data: { confirm: 'Você tem certeza?' } %></p>
  </div>
<% end %>
<%= render 'comments/form' %>
{% endhighlight %}

Em `app/controllers/ideas_controller.rb` adicione na ação "show":
{% highlight ruby %}
@comments = @idea.comments.all
@comment = @idea.comments.build
{% endhighlight %}

Abra o arquivo `app/views/comments/_form.html.erb` e depois do código
{% highlight erb %}
  <div class="field">
    <%= f.label :body %><br />
    <%= f.text_area :body %>
  </div>
{% endhighlight %}

adicione a linha
{% highlight erb %}
<%= f.hidden_field :idea_id %>
{% endhighlight %}

então, remova
{% highlight erb %}
<div class="field">
  <%= f.label :idea_id %><br>
  <%= f.number_field :idea_id %>
</div>
{% endhighlight %}

E é isso. Agora vamos ver uma Idéia que você inseriu na sua aplicação e lá você deve ver o formulário para inserir um comentário assim como para deletar comentários antigos.
