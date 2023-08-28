# Disable Pause
### Disables the teacher's pause button
1. Open DevTools
2. Select this:
   
   ![image](https://github.com/Inglan2/stile-hacks/assets/117789688/4003da64-8abb-48e0-83e5-662f77dd09eb)
4. Create a new rule and set the url to
   ```
   stileapp.com/api/au/v3/activities/*/mob/*/pauseState*
   ```
   ![image](https://github.com/Inglan2/stile-hacks/assets/117789688/f9339e19-2a1d-4553-a052-ff2412eba241)
5. Speedrun your lesson!

Javascript version coming soon, though this might work:
```
// Store the original fetch function
const originalFetch = window.fetch;

// Override the fetch function
window.fetch = function(url, options) {
  // Check if the URL matches the desired pattern
  if (url.match(/stileapp\.com\/api\/au\/v3\/activities\/.*\/mob\/.*\/pauseState.*/)) {
    // Block the request by returning a rejected Promise
    return Promise.reject(new Error('Blocked request'));
  }

  // Forward the request if it doesn't match the pattern
  return originalFetch.apply(this, arguments);
};
```
Bookmarklet:
```
javascript:(function() {
  const originalFetch = window.fetch;
  window.fetch = function(url, options) {
    if (url.match(/stileapp\.com\/api\/au\/v3\/activities\/.*\/mob\/.*\/pauseState.*/)) {
      return Promise.reject(new Error('Blocked request'));
    }
    return originalFetch.apply(this, arguments);
  };
})();
```
Thanks ChatGPT for the JavaScript
