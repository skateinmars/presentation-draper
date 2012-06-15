!SLIDE bullets
# ModelDecorator #

* `app/decorators/model_decorator.rb`
* Lié à un modèle Rails (ActiveModel)
* Contient les méthodes utilisables dans les vues
* Accès au modèle et aux helpers rails depuis ces méthodes

!SLIDE code
## Exemple ##

    @@@ ruby
    class ArticleDecorator < ApplicationDecorator
      def author_name
        article.author.first_name +
          " " +
          article.author.last_name
      end

      def excerpt
        h.truncate article.body
      end
    end
