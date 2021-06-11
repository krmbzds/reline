[![Build Status](https://travis-ci.com/ruby/reline.svg?branch=master)](https://travis-ci.com/ruby/reline)

This is a screen capture of *IRB improved by Reline*.

![IRB improved by Reline](https://raw.githubusercontent.com/wiki/ruby/reline/images/irb_improved_by_reline.gif)

# Reline

Reline is compatible with the API of Ruby's stdlib 'readline', GNU Readline and Editline by pure Ruby implementation.

## Usage

### Single line editing mode

See [bin/example](https://github.com/ruby/reline/blob/master/bin/example)

### Multi-line editing mode

```ruby
require "reline"

prompt = 'prompt> '
use_history = true

begin
  while true
    text = Reline.readmultiline(prompt, use_history) do |multiline_input|
      # Accept the input until `end` is entered
      multiline_input.split.last == "end"
    end

    puts 'You entered:'
    puts text
  end
# If you want to exit, type Ctrl-C
rescue Interrupt
  puts '^C'
  exit 0
end
```

```bash
$ ruby example.rb
prompt> aaa
prompt> bbb
prompt> end
You entered:
aaa
bbb
end
```

See also: [test/reline/yamatanooroti/multiline_repl](https://github.com/ruby/reline/blob/master/test/reline/yamatanooroti/multiline_repl)

## License

The gem is available as open source under the terms of the [Ruby License](https://www.ruby-lang.org/en/about/license.txt).

## Acknowledgments for [rb-readline](https://github.com/ConnorAtherton/rb-readline)

In developing Reline, we have used some of the rb-readline implementation, so this library includes [copyright notice, list of conditions and the disclaimer](license_of_rb-readline) under the 3-Clause BSD License. Reline would never have been developed without rb-readline. Thank you for the tremendous accomplishments.
