`html_safe` can lead a potenial security problem. Never trust user's input.

If only a single piece of user-supplied text was rendered without prior
escaping, it enabled XSS attacks like injecting a <script> tag into the view of
another user. Try to use `sanitize` instead
