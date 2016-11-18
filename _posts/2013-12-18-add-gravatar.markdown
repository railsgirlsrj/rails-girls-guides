---
layout: page
title: Adicione imagens de perfil com Gravatar
permalink: gravatar
previous-link: devise
next-link: design-html-css
---

# Adicione imagens de perfil com Gravatar

*Criado por Catherine Jones*

### Importante

Você precisa ter um email registrado no Gravatar para que esse tutorial funcione. Se você não tem, você pode se registrar em [gravatar.com](http://en.gravatar.com/).

## *1.* Adicione a gem Gravtastic

Abre sua gemfile e abaixo da gem `devise` adicione

{% highlight ruby %}
gem 'gravtastic'
{% endhighlight %}

In the terminal run

{% highlight sh %}
bundle install
{% endhighlight %}

Isso vai instalar gem gravtastic. Lembre-se de restartar sua aplicação.

## *2.* Coloque o Gravatar na sua aplicação

Abra `app/models/user.rb`, e adicione as seguintes linhas

{% highlight ruby %}
include Gravtastic
gravtastic
{% endhighlight %}

logo abaixo da primeira linha

## *3.* Configure o Gravatar

Abra `app/views/layouts/application.html.erb` e na seção

{% highlight erb %}
<% if user_signed_in? %>
{% endhighlight %}

mas antes do

{% highlight erb %}
<% else %>
{% endhighlight %}

adicione

{% highlight erb %}
<%= image_tag current_user.gravatar_url %>
{% endhighlight %}

Agora abra a aplicação no seu browser e faça login com um email associado com o Gravatar. Você deve poder ver seu Gravatar. see your Gravatar.
