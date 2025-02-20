{{/* */}}
## Code Examples

<details>
  <summary>Worker - TypeScript</summary>

```ts
export interface Env {
  AI: Ai;
}

export default {
  async fetch(request, env): Promise<Response> {
    const res: any = await fetch("https://cataas.com/cat");
    const blob = await res.arrayBuffer();

    const inputs = {
      image: [...new Uint8Array(blob)],
    };

    const response = await env.AI.run(
      "{{ .Page.Params.model.name }}",
      inputs
    );

    return new Response(JSON.stringify({ inputs: { image: [] }, response }));
  },
} satisfies ExportedHandler<Env>;
```

</details>

<details>
  <summary>curl</summary>

```bash
curl https://api.cloudflare.com/client/v4/accounts/$CLOUDFLARE_ACCOUNT_ID/ai/run/@cf/meta/detr-resnet-50 \
    -X POST \
    -H "Authorization: Bearer $CLOUDFLARE_API_TOKEN" \
    --data-binary "@pedestrian-boulevard-manhattan-crossing.jpg"
```

</details>
