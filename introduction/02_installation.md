!SLIDE bullets
# Installation #

* Ajouter "`draper`" au Gemfile
* `bundle`
* `rails generate decorator nomdumodele`

!SLIDE code
## Exemple ##

    @@@ ruby
    class ArticleDecorator < ApplicationDecorator
      decorates :article
      allows :description

      def title
        article.title.upcase
      end
    end

!SLIDE code
## Exemple ##

    @@@ ruby
    article = ArticleDecorator.find(1)
    article.title #=> "MON ARTICLE"
    article.description #=> "Ma description"
    article.created_at #=> NoMethodError
