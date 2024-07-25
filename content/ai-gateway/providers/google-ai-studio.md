---
title: Google AI Studio
pcx_content_type: get-started
---

{{<heading-pill style="beta">}}Google AI Studio{{</heading-pill>}}

[Google AI Studio](https://ai.google.dev/aistudio) helps you build quickly with Google Gemini models.

## Endpoint

`https://gateway.ai.cloudflare.com/v1/{account_id}/{gateway_id}/google-ai-studio`

## What you need

When making requests to Google AI Studio, you will need:

- AI Gateway account ID
- AI Gateway gateway name
- Google AI Studio API key
- Google AI Studio model name

## URL structure

Your new base URL will use the data above in this structure: `https://gateway.ai.cloudflare.com/v1/{account_id}/{gateway_id}/google-ai-studio/`.

Then you can append the endpoint you want to hit, for example: `v1/models/{model}:{generative_ai_rest_resource}`

So your final URL will come together as: `https://gateway.ai.cloudflare.com/v1/{account_id}/{gateway_id}/google-ai-studio/v1//models/{model}:{generative_ai_rest_resource}`.

## Examples

### cURL

```bash
---
header: Example fetch request
---
curl "https://gateway.ai.cloudflare.com/v1/{account_id}/{gateway_name}/google-ai-studio/v1/models/gemini-1.0-pro:generateContent" \
 --header 'content-type: application/json' \
 --header 'x-goog-api-key: {google_studio_api_key}' \
 --data '{
      "contents": [
          {
            "role":"user",
            "parts": [
              {"text":"What is Cloudflare?"}
            ]
          }
        ]
      }'
```

### JavaScript

If you are using the `@google/generative-ai` package, you can set your endpoint like this:

```js
---
header: JavaScript example
---
import { GoogleGenerativeAI } from '@google/generative-ai';

const api_token = env.GOOGLE_AI_STUDIO_TOKEN;
const account_id = "";
const gateway_name = "";

const genAI = new GoogleGenerativeAI(api_token);
const model = genAI.getGenerativeModel(
  { model: 'gemini-1.5-flash' },
  { baseUrl: `https://gateway.ai.cloudflare.com/v1/${account_id}/${gateway_name}/google-ai-studio` },
);

await model.generateContent(["What is Cloudflare?"]);
```