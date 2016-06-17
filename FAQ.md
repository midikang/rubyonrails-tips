# FAQ

## PendingMigrationError

Cannot render console from 211.160.167.138! Allowed networks: 127.0.0.1, ::1, 127.0.0.0/127.255.255.255

ActiveRecord::PendingMigrationError (

Migrations are pending. To resolve this issue, run:

        bin/rake db:migrate RAILS_ENV=development

):
  activerecord (4.2.6) lib/active_record/migration.rb:392:in `check_pending!'
  
**Solution**  
```
bundle exec rake db:migrate RAILS_ENV=development
```
## Field value not saved to datase
Keyword: Unpermitted parameter

Check the log
```
Started POST "/tickets" for 211.160.167.137 at 2016-06-14 10:46:31 +0800
Cannot render console from 211.160.167.137! Allowed networks: 127.0.0.1, ::1, 127.0.0.0/127.255.255.255
Processing by TicketsController#create as HTML
  Parameters: {"utf8"=>"✓", "authenticity_token"=>"7U/KFMnK4M0g/hIBVzldI//GHJQ7gVkSRkRfeAeQZPGfGOVV48EwN4Uby/hFsU52OcpiS+HzHYKG6/jgMlYnNQ==", "ticket"=>{"name"=>"Talent show", "seat_id_seq"=>"LA", "address"=>"Pudong", "price_paid"=>"280", "email_address"=>"midi_kang@gmail.com", "phone_number"=>"13472863981"}, "commit"=>"Create Ticket"}
Unpermitted parameter: phone_number
   (0.3ms)  begin transaction
  SQL (1.4ms)  INSERT INTO "tickets" ("name", "seat_id_seq", "address", "price_paid", "email_address", "created_at", "updated_at") VALUES (?, ?, ?, ?, ?, ?, ?)  [["name", "Talent show"], ["seat_id_seq", "LA"], ["address", "Pudong"], ["price_paid", 280.0], ["email_address", "midi_kang@gmail.com"], ["created_at", "2016-06-14 02:46:31.627873"], ["updated_at", "2016-06-14 02:46:31.627873"]]
   (18.1ms)  commit transaction
Redirected to https://rails-midikang.c9users.io/tickets/1
Completed 302 Found in 40ms (ActiveRecord: 19.8ms)
```

### Solution
Add field to params method in controller

```
def ticket_params
      params.require(:ticket).permit(:name, :seat_id_seq, :address, :price_paid, :email_address, :phone_number)
end
```