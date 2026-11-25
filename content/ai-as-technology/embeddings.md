+++
date = '2026-11-25T21:20:44+11:00'
draft = false
title = 'What is an embedding?'
+++

An embedding is a way of turning text (or images, audio, etc.)into a list of numbers, called a vector, so that things with similar meanings end up with similar numbers.

For example, "I forgot my login credentials" and "How do I reset my password"  share almost no words but their embeddings point in nearly the same direction. A keyword search would miss the match, while embedding search finds it.


### Why it matters?
Enbeddings power:
- **Semantic Search**: finding results by meaning, not exact words
- **Recommendation Systems**: suggesting similar contents and products
- **Retrieval Augmented Generation**: an AI looks up relevant documents before answering

### Key Takeaway
**Meaning becomes geometry**. Closeness between the vectors, often measured by cosine similarity, stands in for closeness in meaning.

### Example
1. Meeting was cancelled
2. The gathering was called off
3. The session didnt go ahead

An embedding model would place theese close together because it has seen "meeting", "gathering" and "session" used in similar contecrt, andd "cancelled", "calledoff", and didn't go ahead" all describe the same outcome. The vectors for all there point nearly the same direction, so their cosine similarity is high..