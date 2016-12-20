To find out how many lines of code in your app folder, just use this command:

`find app -iname "*.rb" -type f -exec cat {} \;| wc -l`


The command `bundle exec rake stats` show all information about your code:
lines, lines of code, classes, methods, lines of code/ method, ...


Based on this statistic, you can decide when and where to refactor code.
