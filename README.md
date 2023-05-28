# button
wallet connect

<!DOCTYPE html>
<html>
<head>
  <title>Wallet Connect Button Example</title>
  <script src="https://cdn.jsdelivr.net/npm/@walletconnect/browser@1.4.1/dist/walletconnect.min.js"></script>
</head>
<body>
  <button id="connectButton">Connect Wallet</button>

  <script>
    // Initialize WalletConnect
    const connector = new WalletConnect({
      bridge: 'https://bridge.walletconnect.org', // Replace with your desired bridge server
    });

    // Connect Wallet Button
    const connectButton = document.getElementById('connectButton');
    connectButton.addEventListener('click', () => {
      if (!connector.connected) {
        connector.createSession().then(() => {
          // Show QR Code for user to scan with their mobile wallet
          connector.qrcode(); 
          
          // Subscribe to connection events
          connector.on('connect', () => {
            console.log('Wallet Connected!');
            // Perform actions after successful connection
          });
        });
      }
    });
  </script>
</body>
</html>
