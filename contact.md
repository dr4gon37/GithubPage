---
layout: page
title: Contact
description: Do You have any questions? 
permalink: /contact
background: '/img/background/contactMe/Contact-Me.jpg'
---

If you want to contact me, please enter the fields below.


<form id="formaction" method="POST">
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Name</label>
      <input type="text" name="Name" class="form-control" placeholder="Name" id="name">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Email Address</label>
      <input type="email" name="Email" class="form-control" placeholder="Email Address" id="email" required data-validation-required-message="Please enter your email address.">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Phone Number</label>
      <input type="tel" name="Phone Number" class="form-control" placeholder="Phone Number" id="email">
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <div class="control-group">
    <div class="form-group floating-label-form-group controls">
      <label>Message</label>
      <textarea name="Message" rows="5" class="form-control" placeholder="Message" id="message" required data-validation-required-message="Please enter a message."></textarea>
      <p class="help-block text-danger"></p>
    </div>
  </div>
  <br>
  <div id="success"></div>
  <div class="form-group">
    <button type="submit" class="btn btn-primary" id="sendMessageButton">Send</button>
  </div>
  <input type="hidden" name="_next" value="//mywebsite.com/thanks.html" />
</form>

<script>
    var contactform =  document.getElementById('formaction');
	contactform.setAttribute('action', '//formspree.io/' + 'bartekstep' + '@' + 'gmail' + '.' + 'com');
</script>
