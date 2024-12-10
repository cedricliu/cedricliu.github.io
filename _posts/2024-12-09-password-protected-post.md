---
title: "Password Protected Post"
layout: post
---

<div id="protected-content" style="display:none;">
  <!-- Your protected content goes here -->
  This is a password-protected post.
</div>

<div id="password-form">
  <label for="password">Enter Password:</label>
  <input type="password" id="password">
  <button onclick="checkPassword()">Submit</button>
</div>

<script>
  function checkPassword() {
    var password = document.getElementById('password').value;
    if (password === 'abc123!@#') {
      document.getElementById('protected-content').style.display = 'block';
      document.getElementById('password-form').style.display = 'none';
    } else {
      alert('Incorrect password');
    }
  }
</script>