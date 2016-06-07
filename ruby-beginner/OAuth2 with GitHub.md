OAuth2 with GitHub
https://www.codecademy.com/courses/ruby-beginner-en-pEdhY/0/4?curriculum_id=5122e6618faaada4d20007ed
```
require 'open-uri'

kittens = open('http://placekitten.com/')
response_status = kittens.status
response_body = kittens.read[559, 441]

puts response_status
puts response_body
```

```
require 'open-uri'

kittens = open('http://placekitten.com/200/300')

f = File.open('kittens.jpg', 'w')
kittens.each do |kitten|
  f.write(kitten)
end

f.close
```

```
require 'open-uri'

# Open http://placekitten.com/ for reading on line 4!
kittens = open("http://placekitten.com/")
body = kittens.read[559, 441]

# Add your puts statement below!
puts body
```

```
require 'open-uri'

placekitten = open('http://placekitten.com/')

# Add your code below!
puts placekitten.status

```

```
require "rexml/document"

file = File.open("pets.txt")
doc = REXML::Document.new file
file.close

doc.elements.each("pets/pet/name") do |element|
  puts element
end
```


# Parsing JSON
```
require 'json'

pets = File.open("pets.txt", "r")

doc = ""
pets.each do |line|
  doc << line
end
pets.close

puts JSON.parse(doc)
```

# Requests
```
require 'open-uri'

# Add your code below!
website = open("http://placekitten.com/")
puts website.status
```

# What is OAuth and why do I care?
```
require 'httparty'

token = "1c4b40471046fdb5d0ff81570c7564fe244940c2"

user = HTTParty.get "https://api.github.com/user", 
        :headers => { 
                        "Authorization" => "token #{token}",
                        "User-Agent" => "codecademy"    
                    }

puts "Hi, my username is #{user["login"]}"
```

# Getting into the flow

```
#     +--------+                               +---------------+
#     |        |--(A)- Authorization Request ->|   Resource    |
#     |        |                               |     Owner     |
#     |        |<-(B)-- Authorization Grant ---|               |
#     |        |                               +---------------+
#     |        |                               +---------------+
#     |        |--(C)-- Authorization Grant -->| Authorization |
#     | Client |                               |     Server    |
#     |        |<-(D)----- Access Token -------|               |
#     |        |                               +---------------+
#     |        |                               +---------------+
#     |        |--(E)--      Access Token ------>|    Resource   |
#     |        |                               |     Server    |
#     |        |<-(F)--- Protected Resource ---|               |
#     +--------+                               +---------------+
#     
# Read the full spec at http://tools.ietf.org/html/rfc6749
```


```
require 'httparty'
require 'json'

class GitHub
  include HTTParty
  headers "User-Agent" => "codecademy"
  basic_auth "api-padawan", "GitHubPassw0rd"

  def create_token
    endpoint = "https://api.github.com/authorizations"
    self.class.post endpoint, :body => {}.to_json
  end
end

client = GitHub.new
response = client.create_token

print response.parsed_response
```

Output
```
{
	"id"=>1650019, 
	"url"=>"https://api.github.com/authorizations/1650019", 
	"app"=> {
		"name"=>"GitHub API", 
		"url"=>"http://developer.github.com/v3/oauth/#oauth-authorizations-api"
	}, 
	"token"=>"c8196abdbdcf0e87fcd065d1e07cb2be7ecd682c", 
	"note"=>nil, 
	"note_url"=>nil, 
	"created_at"=>"2013-02-17T00:45:46Z", 
	"updated_at"=>"2013-02-17T00:45:46Z", 
	"scopes"=> []
}
```

https://www.codecademy.com/en/courses/ruby-beginner-en-ifzi3/1/3?curriculum_id=5122e6618faaada4d20007ed

```
require 'httparty'
require 'json'

class GitHub
  API_CLIENT_ID     = '34a57b3c1f20e85a56ab'
  API_CLIENT_SECRET = '89060fce512d1042d168c3e71504ae35208cef1b'
  
  include HTTParty
  headers "User-Agent" => "codecademy"
  basic_auth "api-padawan", "GitHubPassw0rd"

  def create_token
    endpoint = "https://api.github.com/authorizations"
    post_body = {}
    self.class.post endpoint, :body => post_body.to_json
  end
end

client = GitHub.new
response = client.create_token

puts response.parsed_response
```
