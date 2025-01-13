document.getElementById('sendBtn').addEventListener('click', async function() {
    let userMessage = document.getElementById('chatInput').value;
    document.getElementById('messages').innerHTML += `<p>User: ${userMessage}</p>`;
    
    // Gửi yêu cầu API đến ChatGPT
    const response = await fetch('/chat', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({ message: userMessage })
    });

    const data = await response.json();
    document.getElementById('messages').innerHTML += `<p>ChatGPT: ${data.reply}</p>`;
});
