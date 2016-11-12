---
layout: default
title: Criando thumbnails com Carrierwave
permalink: thumbnails
---

# Criando thumbnails com Carrierwave

*Criado por Miha Filej, [@mfilej](https://twitter.com/mfilej)*

__Coach__: Explique a diferença entre usar o atributo width no HTML e diminuir as imagens no servidor.

## *1.*Instalando o ImageMagick

* OS X: escreva `brew install imagemagick` no Terminal e pressione enter. Se você não possui o comando brew, você pode [instalar o Homebrew aqui][in-homebrew].
* Windows: baixe e rode o [instalador do ImageMagick][im-win] (use o primeiro link de
  *download*).
* Linux: No Ubuntu e no Debian, rode `sudo apt-get install imagemagick`. Use o gerenciador de pacotes equivalente em outras distribuições.

  [im-win]: http://www.imagemagick.org/script/binary-releases.php?ImageMagick=vkv0r0at8sjl5qo91788rtuvs3#windows
  [in-homebrew]: http://mxcl.github.io/homebrew/

__Coach__: O que é o ImageMagick e como ele difere das libraries/gems que usamos antes?

Abra o `Gemfile` no projeto e adicione

{% highlight ruby %}
gem 'mini_magick', '3.8.0'
{% endhighlight %}

abaixo da linha

{% highlight ruby %}
gem 'carrierwave'
{% endhighlight %}

No Terminal rode:

{% highlight sh %}
bundle
{% endhighlight %}

## *2.*Dizendo pra nossa aplicação para criar thumbnails quando uma imagem é enviada

Abra `app/uploaders/picture_uploader.rb` e procure a linha que se parece com isso:

{% highlight ruby %}
  # include CarrierWave::MiniMagick
{% endhighlight %}

Remova o `#`.

__Coach__: Explique o conceito dos comentários no código.

Abaixo da linha que você modificou, adicione:

{% highlight ruby %}
version :thumb do
  process :resize_to_fill => [50, 50]
end
{% endhighlight %}

As imagens enviadas daqui pra frente devem ser alteradas, mas as que já temos não foram afetadas. Então edite uma das idéias existentes e adicione uma nova imagem.

## *3.*Mostrando os thumbnails

Para ver se a imagem enviada foi alterada, abra
`app/views/ideas/index.html.erb`. Mude a linha

{% highlight erb %}
<td><%= idea.picture %></td>
{% endhighlight %}

para

{% highlight erb %}
<td><%= image_tag idea.picture_url(:thumb) if idea.picture? %></td>
{% endhighlight %}

Dê uma olhada na lista de idéias no browser para ver se o thumbnail está lá.
