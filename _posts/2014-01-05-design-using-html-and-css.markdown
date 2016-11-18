---
layout: default
title: Design com HTML and CSS
permalink: design-html-css
---

1.Design your header

+ Coloque o seguinte código no fim do arquivo `app/assets/stylesheets/application.css`:

    ```
    .navbar {
        min-height: 38px;
      background-color: #f55e55;
    }
    ```

  Agora recarregue a página e verifique as mudanças. Você pode tentar mudar a cor ou a fonte do topo (header). Você pode checar a referência de cores dessse site: [http://color.uisdc.com/](http://color.uisdc.com/).

    **Coach: ** talk about the property `display`, inline and block element.

+ Agora coloque essas linhas no final:

    ```
    .navbar a.brand { font-size: 18px; }
    .navbar a.brand:hover {
     color: #fff;
     background-color: transparent;
     text-decoration: none;
    }
    ```

    **Treinador(a): ** explique os 4 estados de um link


2. Faça sua tabela

 + Nós vamos usar o [Bootstrap](http://getbootstrap.com/) para
   Melhorar nossa tabela. Ache nessa linha no arquivo
   `app/views/ideas/index.html.erb` e troque: 

   `<table>`

   por

   `<table class="table">`

 + Modifique o tamanho da imagem usando as seguintes linhas:

     ```
     <%= image_tag(idea.picture_url, :width => 600) if idea.picture.present? %>
     ```

     tente mudar a largura e veja o que vai acontecer


 + adicione as seguintes linhas no final do arquivo `app/assets/stylesheets/ideas.css.scss`:

  ```
  .container a:hover {
    color: #f55e55;
    text-decoration: none;
    background-color: rgba(255, 255, 255, 0);
  }
  ```


 + tente usar a propriedade `background-image` para colocar um background,
   veja
   [http://subtlepatterns.com/](http://subtlepatterns.com/) para alguns padrões.


3. Adicione algum estilo ao footer

+ adicione as seguintes linhas no fim do arquivo `app/assets/stylesheets/application.css`:

    ```
    footer {
      background-color: #ebebeb;
      padding: 30px 0;
    }
    ```

    tente colocar mais coisas no`footer`, então ajuste sua posição.

4. Coloque algum estilo no botão

  + Abra
    [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new)
    e procure o botão `Criar Idéia`.

    adicione essas linhas ao `app/assets/stylesheets/ideas.css.scss`

   ```
   .container input[type="submit"] {
      height: 30px;
      font-size: 13px;
      background-color: #f55e55;
      border: none;
      color: #fff;
    }
   ```

   **Treinador(a)** Explique como usar `border` em css, tente modificar o estilo do botão para arrendondá-lo,
   adicione sombra ou cor.
