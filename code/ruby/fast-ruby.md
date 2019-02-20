# Fast Ruby

From: [fast-ruby](https://github.com/JuanitoFatas/fast-ruby)

This is a comparation between ruby methods.

-| Faster | Slower|
---|----|---|
Array | Array[0], Array[-1] | Array.first, Array.last|
Array | bsearch | find |
Array | unshift | insert |
Array | length, size | count |
Array | sample | shuffle.first |
Date | iso8601(string) | parse(string) |
Enumerable | map | each { push } |
Enumerable | each | for .. in |
Enumerable | while index < ARRAY.size | each_with_index |
Enumerable | ARRAY.inject(:+) , ARRAY.inject(&:+) | inject {\|a,i\| a + i}|
Enumerable | ARRAY.flat_map {\|e\| [e,e]} | ARRAY.map {\|e\| [e,e]}.flatten |
Enumerable | ARRAY.reverse_each {\|x\| x} | ARRAY.reverse.each ... |
Enumerable | ARRAY.detect {} | ARRAY.select {}.first |
Enumerable | sort_by(&:name), sort_by {\|e\| e.name} | sort {\|a,b\| a.name <=> b.name} |
Enumerable | min_by {\|x\| x.succ} | sort_by {\|x\| x.succ}.first |
General | a, b, c = 1, 2, 3 | a = 1, b = 2, c = 3 |
General | respond_to? | begin - rescue |
General | NUM.round(2).to_s | format('%.2f', NUM), '%.2f' % NUM |
General | while true | loop do |
Hash | Hash[HASH] | HASH.dup |
Hash | HASH_WITH_SYMBOL[:fast] | HASH_WITH_STRING["fast"] |
Hash | dig | [:a][:b][:c] |
Hash | sort_by {\|k, v\| k}.to_h | sort.to_h |
Hash | each_key | keys.each |
Hash | key? KEY, value? KEY | keys.include?, values.include? |
Proc and block | Symbol#to_proc: map(&:to_s) | map {\|i\| i.to_s} |
String | match?(/boo/) | =~ /boo/, match(/boo/) |
String | "#{foo} #{bar}", 'foo' 'bar' | 'foo'.concat 'bar', 'foo' + 'bar' |
String | end_with?, start_with? | match?(/regex/), =~ |
String | sub | gsub |
String | tr | gsub |
String | remove extra space: squeeze(" ") | gsub(/ +/, " ") |
String | delete_suffix | chomp, sub |





