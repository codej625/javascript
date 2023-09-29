# url속에서 parameter를 찾아보자!

```javascript
const urlParams = new URLSearchParams(window.location.search);
  // const example = urlParams.get('ex') || '';
  const utmSource = urlParams.get('utm_source');
  const utmMedium = urlParams.get('utm_medium'); 
  const utmCampaign = urlParams.get('utm_campaign');
  const utmTerm = urlParams.get('utm_term');
  const utmContent = urlParams.get('utm_content');
  
  const db = {
    utmSource,
    utmMedium,
    utmCampaign,
    utmTerm,
    utmContent 
  };
```