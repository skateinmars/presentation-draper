!SLIDE 
### Exemple de méthode de classe : `options_for_select` ###

    @@@ ruby
    # app/decorators/author_decorator.rb
    class AuthorDecorator < ApplicationDecorator
      decorates :author

      def self.choices_for_select
        Author.
          order('last_name DESC').
          all.
          collect {|p| [ p.last_name, p.id ] }
      end
    end

    # app/views/articles/_form.html.erb
    <%= form.select 
            :author_id, 
            AuthorDecorator.choices_for_select %>
