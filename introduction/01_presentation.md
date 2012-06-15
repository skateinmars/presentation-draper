!SLIDE
# Draper #

## View Models for Rails ##

!SLIDE bullets
# Le problème #

* helpers : simples collections de fonctions
* bouts de vues dans les modèles

!SLIDE code
# Helper #

    @@@ ruby

    module ProductsHelper
      def formatted_price(product)
        number_with_precision
          (product.price_without_taxes/100.0),
          :precision => 2
      end
    end

!SLIDE code
# Bloated Model #

    @@@ ruby

    class Product
      def formatted_price_without_taxes
        Object.new.extend(
            ActionView::Helpers::NumberHelper)
            .number_with_precision(
              (price_without_taxes / 100.0),
                :precision => 2)
        )
      end
    end

!SLIDE smbullets
## Solution : decorators/presenters ##

* Decorator, Presenter, Exhibit, Composite : OO Design patterns
* Ajouter des fonctionnalités (méthodes) à un objet
* Déléguer des méthodes à son objet lié


!SLIDE smbullets
## Draper ##

* Remplace les helpers par des classes/objets
* "Enrobe" les modèles Rails
* Interface entre un modèle et les vues





