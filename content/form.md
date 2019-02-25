+++
comments = true
date = "2015-04-14T22:17:00+00:00"
draft = false
noauthor = true
share = false
title = "お問い合わせ"
type = "page"
[menu.main]
weight = 97

+++

<form name="contact" method="POST" data-netlify-recaptcha="true" data-netlify="true">
  <p>
    <label>Email: <input type="text" name="name" /></label>
  </p>
  <p>
    <label>Message: <textarea name="message"></textarea></label>
  </p>
  <div data-netlify-recaptcha="true"></div>
  <p>
    <button type="submit">Send</button>
  </p>
</form>
