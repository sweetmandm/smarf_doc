# Doc Yo Self

An auto documentation for Rails. Pop it into your test suite and watch it amaze.

Current focus is MiniTest. *Probably* will work with Rspec too, but that's not our focus right now.

## Setup

```ruby
DocYoSelf.config do |c|
  c.template     = 'test/template.md.erb'
  c.success_only = true # The Default
  c.output       = 'api_docs.md'
end
```

To run doc generation after every controller spec, put this into your `teardown` method.

```ruby
def teardown
  DocYoSelf.run!
end 
```

Or put it individually into only certain tests...

```ruby
def test_some_api
  get :index, :users
  assert response.status == 200
  DocYoSelf.run!
end
```

## Usage

It will log all requests and responses by default, but you can add some **optional** parameters as well.

### Skipping documentation

```ruby
def test_stuff
  skip_docs
  # Blahhh
end
```

## Adding notes

```ruby
def test_stuff
  doc_notes "This API endpoint does things."
  # Blahhh
end
```
