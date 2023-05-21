# find Approximate location of a user based on IPadress

# for frontend
```js
// Make an API request to an IP geolocation service
fetch('https://ipapi.co/json/')
  .then(response => response.json())
  .then(data => {
    // Extract the approximate location details from the response
    const { city, region, country_name } = data;

    // Use the location details as needed
    console.log(`Approximate location: ${city}, ${region}, ${country_name}`);
  })
  .catch(error => {
    console.error('Error retrieving location:', error);
  });

```


# for backend 


```js
const geoip = require('geoip-lite');

// Get IP address of the user
const ipAddress = req.headers['x-forwarded-for'] || req.connection.remoteAddress;

// Retrieve the approximate location based on the IP address
const location = geoip.lookup(ipAddress);

if (location) {
  const { city, region, country } = location;
  console.log(`Approximate location: ${city}, ${region}, ${country}`);
} else {
  console.log('Location not found.');
}

```
