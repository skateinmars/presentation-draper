!SLIDE code
## Rspec ##

    @@@ ruby
    # spec/decorators/author_decorator_spec.rb
    require 'spec_helper'

    describe AuthorDecorator do
      context "given a new Author" do
        subject { 
          AuthorDecorator.decorate(
            FactoryGirl.build(:author, 
              :first_name => "Dupond")) 
        }
        
        it "displays its first_name" do
          subject.first_name.should == "Dupond"
        end
      end
    end
