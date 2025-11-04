# Build AI-Powered Apps with OpenAI and Node.js

This repo is a companion to the [Build AI-Powered Apps with OpenAI and Node.js][course] course on Frontend Masters.

[![Frontend Masters](https://static.frontendmasters.com/assets/brand/logos/full.png)][course]

[fem]: https://www.frontendmasters.com
[course]: https://frontendmasters.com/courses/openai-node/


## Errata

**Document QA Query Function Lesson**

A few of the Langchain methods used in this course have been deprecated. Here's an alternative approach:

Install the Langchain community module

```bash
npm i @langchain/community
````

Import the loaders

```javascript
import { PDFLoader } from '@langchain/community/document_loaders/fs/pdf'
import { YoutubeLoader } from '@langchain/community/document_loaders/web/youtube'
import { CharacterTextSplitter } from 'langchain/text_splitter'
```

Create the loaders using the community methods:

In `docsFromYTVideo`:

```javascript
const loader = YoutubeLoader.createFromUrl(video, { language: 'en', addVideoInfo: true, })
  const loadedDoc = await loader.load()
  const splitter = new CharacterTextSplitter({
    separator: ' ',
    chunkSize: 2500,
    chunkOverlap: 200,
  })
  return await splitter.splitDocuments(loadedDoc)
```

In `docsFromPDF`: 

```javascript
const docsFromPDF = async () => { const loader = new PDFLoader('./xbox.pdf')
  const loadedDoc = await loader.load()
  const splitter = new CharacterTextSplitter({
    separator: '. ',
    chunkSize: 2500,
    chunkOverlap: 200,
  })
  return await splitter.splitDocuments(loadedDoc)
```
