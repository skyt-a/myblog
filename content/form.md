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

<form class="form" id="form1" name="contactform" action="thanks" netlify>

  <p class="name">
    <input name="name" type="text" class="validate[required,custom[onlyLetter],length[0,100]] feedback-input" placeholder="Name" id="name" />
  </p>

  <p class="email">
    <input name="email" type="email" class="validate[required,custom[email]] feedback-input" id="email" placeholder="Email" />
  </p>

  <p class="text">
    <textarea name="text" class="validate[required,length[6,300]] feedback-input" id="comment" placeholder="Comment"></textarea>
  </p>


  <div class="submit">
    <input type="submit" value="SEND" id="button-blue"/>
    <div class="ease"></div>
  </div>
</form>
