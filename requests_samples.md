### sync call

```
curl -X POST http://localhost:10000/ \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id":      "1",
    "method":  "message/send",
    "params": {
      "task_id": "task-123",
      "message": {
        "messageId": "msg-123",
        "role":      "user",
        "parts": [
          {
            "type": "text",
            "text": "Convert 100 USD to EUR"
          }
        ]
      },
      "stream": false
    }
  }'
```

---

### multi turn

##### first call

```
curl -X POST http://localhost:10000/ \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": "2",
    "method": "message/send",
    "params": {
      "task_id": "task-123",
      "message": {
        "messageId": "1",
        "role": "user",
        "parts": [
          {
            "type": "text",
            "text": "How much is the exchange rate for 1 USD?"
          }
        ]
      }
    }
  }'
```

##### second call

```
curl -X POST http://localhost:10000/ \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": "2",
    "method": "message/send",
    "params": {
      "task_id": "task-123",
      "message": {
        "messageId": "2",
        "role": "user",
        "parts": [
          {
            "type": "text",
            "text": "CAD"
          }
        ]
      }
    }
  }'
```

---

### streaming

```
curl -X POST http://localhost:10000/ \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": "1",
    "method": "message/stream",
    "params": {
      "task_id": "task-123",
      "message": {
        "messageId": "msg-123",
        "role": "user",
        "parts": [
          {
            "type": "text",
            "text": "Convert 100 USD to EUR"
          }
        ]
      }
    }
  }'
```