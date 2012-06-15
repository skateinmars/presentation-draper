!SLIDE 
## Décorer un modèle (depuis un controller) ##

    @@@ ruby
    ArticleDecorator.new(Article.find(params[:id]))
    ArticleDecorator.find(params[:id])

    ArticleDecorator.decorate(Article.all)

!SLIDE smbullets
## Fonctionnalités ##

* `allow/denies` : accès direct aux méthodes du modèle
* Héritage (sous-classes Décorator)
* ApplicationDecorator : méthodes communes aux décorateurs
* `decorates_association` pour chaîner les decorateurs

!SLIDE code
## ApplicationDecorator ##

    @@@ ruby
    class ApplicationDecorator < Draper::Base
      def created_at
        h.content_tag :span, 
                  I18n.l(model.created_at), 
                  :class => 'created_at'
      end
    end

!SLIDE code
<style type="text/css">
.sh_ruby code { font-size: 20px; }
</style>
.notes decorates_association
    @@@ ruby
    class Article < ActiveRecord::Base
      belongs_to :author
    end

    class ArticleDecorator < ApplicationDecorator
      decorates :article
      decorates_association :author
    end

    class AuthorDecorator < ApplicationDecorator
      decorates :author

      def name
        "#{model.first_name} #{model.last_name}"
      end
    end

    @article.author.name


