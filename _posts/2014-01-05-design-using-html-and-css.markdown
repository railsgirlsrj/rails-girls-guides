---
layout: page
title: Design com HTML e CSS
permalink: design-html-css
previous-link: gravatar
next-link: testing-rspec
---

# Design com HTML e CSS

## 1. Melhore seu cabeçalho

+ Coloque o seguinte código no fim do arquivo `app/assets/stylesheets/application.css`:

{% highlight css %}
.navbar {
  min-height: 38px;
  background-color: #f55e55;
}
{% endhighlight %}

Agora recarregue a página e verifique as mudanças. Você pode tentar mudar a cor ou a fonte do topo (header). Você pode checar a referência de cores dessse site: [http://color.uisdc.com/](http://color.uisdc.com/).

**Treinadores**: fale sobre a propriedade `display`, sobre `inline` e `block element`.

+ Agora coloque essas linhas no final:

{% highlight css %}
.navbar a.brand {
  font-size: 18px;
}
.navbar a.brand:hover {
  color: #fff;
  background-color: transparent;
  text-decoration: none;
}
{% endhighlight %}

**Treinadores**: explique os 4 estados de um link

## 2. Faça sua tabela

 + Nós vamos usar o [Bootstrap](http://getbootstrap.com/) para
   Melhorar nossa tabela. Ache nessa linha no arquivo
   `app/views/ideas/index.html.erb` e troque:

{% highlight html %}
<table>
{% endhighlight %}

   por

{% highlight html %}
<table class="table">
{% endhighlight %}

 + Modifique o tamanho da imagem usando as seguintes linhas:

{% highlight html %}
<%= image_tag(idea.picture_url, :width => 600) if idea.picture.present? %>
{% endhighlight %}

tente mudar a largura e veja o que vai acontecer

+ Adicione as seguintes linhas no final do arquivo `app/assets/stylesheets/ideas.css.scss`:

{% highlight css %}
.container a:hover {
  color: #f55e55;
  text-decoration: none;
  background-color: rgba(255, 255, 255, 0);
}
{% endhighlight %}

+ Tente usar a propriedade `background-image` para colocar um background, veja
[http://subtlepatterns.com/](http://subtlepatterns.com/) para alguns padrões.

3. Adicione algum estilo ao footer

+ Adicione as seguintes linhas no fim do arquivo `app/assets/stylesheets/application.css`:

{% highlight css %}
footer {
  background-color: #ebebeb;
  padding: 30px 0;
}
{% endhighlight %}

tente colocar mais coisas no`footer`, então ajuste sua posição.

4. Coloque algum estilo no botão

+ Abra [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new) e procure o botão `Criar Ideia`.

adicione essas linhas ao `app/assets/stylesheets/ideas.css.scss`

{% highlight css %}
.container input[type="submit"] {
  height: 30px;
  font-size: 13px;
  background-color: #f55e55;
  border: none;
  color: #fff;
}
{% endhighlight %}

**Treinadores**: Explique como usar `border` em css, tente modificar o estilo do botão para arrendondá-lo,
adicione sombra ou cor.
