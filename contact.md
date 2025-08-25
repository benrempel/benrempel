---
layout: default
title: Contact
class: narrow-page
---

## contact

benrempelmusic@gmail.com  
instagram: <a href="https://instagram.com/ben.remp" target="_blank" rel="noopener">@ben.remp</a>

### email list sign-up:

<form id="signup-form" action="https://formspree.io/f/mpwlvvez" method="POST" class="signup-form" onsubmit="return false;">
  <input type="email" name="email" placeholder="you@example.com" required>
  
  <!-- Simple spam trap (honeypot). Leave blank. -->
  <input type="text" name="_gotcha" style="display:none">
  
  <button type="submit">submit</button>
</form>

<p id="form-response" class="form-response"></p>

<script>
  const form = document.getElementById('signup-form');
  const response = document.getElementById('form-response');

  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    response.textContent = 'submitting…';

    const data = new FormData(form);
    try {
      const r = await fetch(form.action, {
        method: form.method,
        body: data,
        headers: { 'Accept': 'application/json' }
      });

      if (r.ok) {
        response.textContent = 'submission received.';
        form.reset();
      } else {
        response.textContent = 'something went wrong. please try again.';
      }
    } catch (err) {
      response.textContent = 'network error. please try again.';
    }
  });
</script>