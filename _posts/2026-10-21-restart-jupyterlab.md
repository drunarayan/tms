---
layout: post
title: "JupyterLab VM Controller"
author: "Chandru Narayan"
categories: resources
tags: [resources]
image: typewriter-type-fast.gif
permalink: /wake-vm/
---

<div style="max-width: 480px; margin: 2rem auto; padding: 25px; border: 1px solid #e1e4e8; border-radius: 8px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <p style="margin-top: 0; color: #444; line-height: 1.5;">Enter the access code to start or stop the JupyterLab GCN Virtual Machine.</p>
  
  <div style="margin-bottom: 20px;">
    <label for="vm-pass" style="display: block; margin-bottom: 8px; font-weight: 600; color: #24292e;">Access Code:</label>
    <input type="password" id="vm-pass" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; font-size: 16px;" placeholder="Enter access password">
  </div>

  <div style="display: flex; gap: 10px;">
    <button id="wake-btn" onclick="controlVm('wake')" style="flex: 1; background-color: #28a745; color: white; border: none; padding: 12px; border-radius: 4px; cursor: pointer; font-weight: 600; font-size: 15px;">
      Wake Up Server
    </button>
    <button id="shutdown-btn" onclick="controlVm('shutdown')" style="flex: 1; background-color: #dc3545; color: white; border: none; padding: 12px; border-radius: 4px; cursor: pointer; font-weight: 600; font-size: 15px;">
      Shutdown Server
    </button>
  </div>

  <div id="response-msg" style="margin-top: 18px; font-weight: 600; text-align: center; line-height: 1.4;"></div>
</div>

<script>
async function controlVm(actionType) {
  const wakeBtn = document.getElementById('wake-btn');
  const shutdownBtn = document.getElementById('shutdown-btn');
  const msg = document.getElementById('response-msg');
  const password = document.getElementById('vm-pass').value;

  const FUNCTION_URL = "https://wake-gcn-vm-574717140851.us-west1.run.app/";

  if (!password) {
    msg.style.color = '#d73a49';
    msg.innerText = "Please enter the password.";
    return;
  }

  wakeBtn.disabled = true;
  shutdownBtn.disabled = true;
  msg.style.color = '#0366d6';
  msg.innerText = actionType === 'shutdown' ? "Sending shutdown command..." : "Sending wake command...";

  try {
    const response = await fetch(FUNCTION_URL, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ password: password, action: actionType })
    });

    const resData = await response.json();

    if (response.ok) {
      msg.style.color = '#28a745';
      msg.innerText = resData.message;
    } else {
      msg.style.color = '#d73a49';
      msg.innerText = resData.message || "Request failed.";
    }
  } catch (err) {
    msg.style.color = '#d73a49';
    msg.innerText = "Connection error. Please try again.";
  } finally {
    wakeBtn.disabled = false;
    shutdownBtn.disabled = false;
  }
}
</script>

