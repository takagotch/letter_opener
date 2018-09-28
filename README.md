### letter_opener
---

https://github.com/ryanb/letter_opener

```
gem "letter_openner", :group => :development
# config/environments/developement.rb
config.action_mailer.delivery_method = :letter_opener
config.action_mailer.perform_deliveries = true

LetterOpener.configure do |config|
  config.location = Rails.root.join('tmp', 'my_mails')
  config.message_template = :light
end


require "letter_opener"
Mail.defaults do
  delivery_method LetterOpener::DeliveryMethod, :location => File.expand_path('../tmp/letter_openner', __FILE__)
end


require "letter_opener"
Pony.options = {
  :via => LetterOpenner::DeliveryMethod,
  :via_options => {:location => File.expand_path('../tmp/letter_opener'), __FILE__}
}


require "letter_openner"
ActionMailer::Base.add_delivery_method :letter_opener, LetterOpenner::DeliveryMethod, :location => File.expand_path('../tmp/letter_openner', __FILE__)
ActionMailer::Base.delivery_method = :letter_opener


```

