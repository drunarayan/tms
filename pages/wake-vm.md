---
layout: page
title: Wake GCN VM
permalink: /wake-vm/
---

<div style="max-width: 480px; margin: 2rem auto; padding: 25px; border: 1px solid #e1e4e8; border-radius: 8px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <p style="margin-top: 0; color: #444; line-height: 1.5;">If the GCN VM is offline, enter the student access code below to boot it up for homework sessions.</p>
  
  <div style="margin-bottom: 20px;">
    <label for="vm-pass" style="display: block; margin-bottom: 8px; font-weight: 600; color: #24292e;">Access Code:</label>
    <input type="password" id="vm-pass" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; font-size: 16px;" placeholder="Enter shared password">
  </div>

  <button id="wake-btn" onclick="triggerVmWake()" style="background-color: #0366d6; color: white; border: none; padding: 12px 20px; border-radius: 4px; cursor: pointer; width: 100%; font-weight: 600; font-size: 16px;">
    Wake Up GCN Server
  </button>

  <div id="response-msg" style="margin-top: 18px; font-weight: 600; text-align: center; line-height: 1.4;"></div>
</div>

<script>
async function triggerVmWake() {
  const btn = document.getElementById('wake-btn');
  const msg = document.getElementById('response-msg');
  const password = document.getElementById('vm-pass').value;

  // PASTE YOUR CLOUD FUNCTION URL HERE:
  const FUNCTION_URL = "https://wake-gcn-vm-574717140851.us-west1.run.app";

  if (!password) {
    msg.style.color = '#d73a49';
    msg.innerText = "Please enter the password.";
    return;
  }

  btn.disabled = true;
  btn.style.opacity = '0.7';
  btn.innerText = "Sending wake command...";
  msg.innerText = "";

  try {
    const response = await fetch(FUNCTION_URL, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ password: password })
    });

    const resData = await response.json();

    if (response.ok) {
      msg.style.color = '#28a745';
      msg.innerText = resData.message;
      btn.innerText = "Server Waking Up...";
    } else {
      msg.style.color = '#d73a49';
      msg.innerText = resData.message || "Failed to start server.";
      btn.disabled = false;
      btn.style.opacity = '1.0';
      btn.innerText = "Wake Up GCN Server";
    }
  } catch (err) {
    msg.style.color = '#d73a49';
    msg.innerText = "Connection error. Please try again.";
    btn.disabled = false;
    btn.style.opacity = '1.0';
    btn.innerText = "Wake Up GCN Server";
  }
}
</script>