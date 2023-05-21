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
