## 1. Building all the files
- [ ] `embeddings.py` → takes text, returns embedding vector
- [ ] `redis_cache.py` → store and retrieve the latest few messages
- [ ] `pinecone_store.py` → store embeddings in Pinecone & fetch similar ones using semantic search
- [ ] `responder.py` → takes context + input, gets LLM response
- [ ] `retriever.py` → uses Pinecone to pull old relevant conversations

---

## 2. Connecting all the files
- [ ] In `crew_flow.py`, define CrewAI agents & workflow
- [ ] In `main.py`, handle user input → pass to CrewAI → get reply
- [ ] After each reply, store conversation in Redis (short-term) and Pinecone (long-term)

---

## 3. Testing
- [ ] Talk to the bot and check if Redis remembers the last few messages
- [ ] Test if Pinecone can recall older chats when reference is given to them

---

## 4.Optional
- [ ] Adding a summarizer before storing chats(for less storage)

## File Structure(For Now)

```bash
crew-bot/
│
├── main.py                 # Entry point for running the bot
├── crew_flow.py            # CrewAI orchestration logic
│
├── agents/
│   ├── responder.py        # Generates bot responses
│   ├── retriever.py        # Gets relevant past chats from Pinecone
│
├── services/
│   ├── redis.py      # Redis caching
│   ├── pinecone.py   # Store/retrieve chat embeddings from Pinecone
│   ├── embeddings.py       # Generate embeddings from text
│
├── config.py               # API keys
├── requirements.txt
└── README.md

```
