# StatGenRest
This project is a REST API that generates language statistics for organizations using the GitHub API v3.


## Requirements
* Unix shell
* Ruby 2.5.0
* Ruby on Rails 5.1.4
* Bundler 1.16.1 
* cURL 7.58.0
* GitHub account with a valid token (see https://github.com/settings/tokens)


## Steps to get the REST API up and running
```
[yourself@yourpc] cd to/project/dir
[yourself@yourpc] bundle install    # install dependencies
[yourself@yourpc] rails s           # start the server
```


## Tests
```
[yourself@yourpc] cd to/project/dir
[yourself@yourpc] bundle exec rspec spec/controllers/api/languages_controller_spec.rb   # run all tests for this controller
```


## Examples
```
[yourself@yourpc] export ORGANIZATION='replace_with_organization_name'
[yourself@yourpc] export GITHUB_TOKEN='replace_with_token'
[yourself@yourpc] curl -H "Authorization: token $GITHUB_TOKEN" http://127.0.0.1:3000/languages\?format\=json\&organization\=$ORGANIZATION
{
  "Ruby": "20.56%",
  "JavaScript": "16.38%",
  "CoffeeScript": "16.21%",
  "HTML": "16.08%",
  "Java": "15.36%",
  "CSS": "4.75%",
  "PHP": "4.62%",
  "Go": "2.26%",
  "Elixir": "2.11%",
  "Clojure": "1.06%",
  "C": "0.43%",
  "Makefile": "0.1%",
  "Shell": "0.01%"
}
```

## Save data to json files for analyzing
```
[yourself@yourpc] cd to/project/dir/command_line_tool/
[yourself@yourpc] export ORGANIZATION='replace_with_organization_name'
[yourself@yourpc] export GITHUB_TOKEN='replace_with_token'
[yourself@yourpc] ./get-stats.sh $ORGANIZATION $GITHUB_TOKEN
[yourself@yourpc] cat $ORGANIZATION-stats.json
```