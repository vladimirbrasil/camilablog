# camilablog

## Known bugs

### Substituir textos revisados pela IA

Busca por semelhança, pode substituir parágrafo errado algum dia (raro, mas pode).

### Adicionar título

Adiciona acima da "hero" image, quando não há título ainda.

### Hero Image duplicada no texto

A confusão de adicionar título acima da hero Image ainda não sanou tudo, então a hero image até é detectada mesmo após o título, mas também é tratada como imagem no corpo do texto (após o título). Verificar "processDocumentContent".

### Imagem gerada pela IA insiste em conter texto

Mesmo mudando o prompt, a imagem gerada pela IA frequentemente tem texto.

```js
function createImagePrompt({ title, html }) {
  let prompt = "Create a hero image for a blog post header. ";
  if (title) {
    prompt += `The blog post title is: "${title}". `;
  }
  prompt += `The content is about: ${html.substring(0, 500)}. `;

  prompt += "Image requirements: ";
  prompt += "Do NOT include any text, letters, logos, signs, banners, watermarks, or words of any kind in the image. ";
  prompt += "The image must be completely free of any visible text or written characters. ";
  prompt += "Imagine it will have a title placed over it later. ";

  prompt += "Style: Realistic photograph, possibly with people, emotional expression is welcome. ";
  prompt += "Layout: Horizontal, wide-angle composition. Not crowded. ";
  prompt += "Color: Use a soft and harmonious color palette that works well with text overlays. ";
  prompt += "Quality: High resolution, sharp focus, professional visual. ";
  return prompt;
}
```