# Jokes API

A simple and fun RESTful API to deliver joy to the world with jokes!

---

## 🟢 Base URL

```
http://localhost:3000
```

---

## 📖 Endpoints

### `GET /random`

Get a **random joke**.

**Example Request:**

```bash
curl --location 'http://localhost:3000/random/'
```

**Example Response:**

```json
{
  "id": 43,
  "jokeText": "What did one ocean say to the other ocean? Nothing, they just waved.",
  "jokeType": "Wordplay"
}
```

---

### `GET /jokes/:id`

Get a **specific joke** by ID.

**Example Request:**

```bash
curl --location 'http://localhost:3000/jokes/2'
```

**Example Response:**

```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
  "jokeType": "Puns"
}
```

---

### `GET /filter?type=<type>`

Get all jokes filtered by **jokeType**.

**Example Request:**

```bash
curl --location 'http://localhost:3000/filter?type=Puns'
```

**Example Response:**

```json
[
  {
    "id": 2,
    "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
    "jokeType": "Puns"
  },
  {
    "id": 3,
    "jokeText": "I told my wife she was drawing her eyebrows too high. She looked surprised.",
    "jokeType": "Puns"
  },
  ...
]
```

---

### `POST /jokes`

Add a **new joke**.

**Body Parameters (URL-encoded):**

- `text` (string): The joke text.
- `type` (string): The category/type of joke.

**Example Request:**

```bash
curl --location --request POST 'http://localhost:3000/jokes' \
--data-urlencode 'text=Iamonthemoonandthereisnowheretogetabeer. Thereisnospacebar.' \
--data-urlencode 'type=Science'
```

**Example Response:**

```json
{
  "id": 101,
  "jokeText": "Iamonthemoonandthereisnowheretogetabeer. Thereisnospacebar.",
  "jokeType": "Science"
}
```

---

### `PUT /jokes/:id`

**Replace** an existing joke completely.

**Body Parameters:**

- `text` (string): New joke text.
- `type` (string): New joke type.

**Example Request:**

```bash
curl --location --request PUT 'http://localhost:3000/jokes/2' \
--data-urlencode 'text=Why did the scarecrow win a prize? Because he was outstanding in his field.' \
--data-urlencode 'type=Science'
```

**Example Response:**

```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win a prize? Because he was outstanding in his field.",
  "jokeType": "Science"
}
```

---

### `PATCH /jokes/:id`

**Edit** an existing joke.

**Body Parameters (optional):**

- `text` (string)
- `type` (string)

**Example Request:**

```bash
curl --location --request PATCH 'http://localhost:3000/jokes/2' \
--data-urlencode 'type=Agriculture'
```

**Example Response:**

```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win a prize? Because he was outstanding in his field.",
  "jokeType": "Agriculture"
}
```

---

### `DELETE /jokes/:id`

Delete a **specific joke** by ID.

**Example Request:**

```bash
curl --location --request DELETE 'http://localhost:3000/jokes/2'
```

**Example Response:**

```text
OK
```

---

### `DELETE /jokes/all`

⚠️ Delete **all jokes**.

**Authentication:** Requires an admin key.

**Example Request:**

```bash
curl --location --request DELETE 'http://localhost:3000/all'
```

**Example Response:**

```text
OK
```

---

## ⚠️ Notes

- All endpoints return `200 OK` on success.
- All IDs are numeric and auto-incremented.
- Joke types are case-insensitive when filtering.
- Ensure body parameters are correctly URL-encoded for `POST`, `PUT`, and `PATCH`.

---

## 💡 Enjoy the jokes and spread the laughter!
