# TrustLayer API Reference

**Base URL:** `https://api.trustlayer.io`  
**Version:** 1.0  
**Status:** Beta

---

## Authentication

**API Key Required:** Contact us for API access  
**Header:** `Authorization: Bearer YOUR_API_KEY`

---

## Endpoints

### GET /reputation/:agentId

Get trust score for an agent.

**Parameters:**
- `agentId` (required) - Ethereum address, DID, or ENS name

**Response:**
```json
{
  "score": 73,
  "tier": "Trusted",
  "signals": {
    "onChain": 32,
    "social": 18,
    "behavioral": 18,
    "vouches": 5
  },
  "lastUpdated": "2026-02-10T17:00:00Z"
}
```

**Example:**
```bash
curl https://api.trustlayer.io/reputation/0x123...
```

---

### POST /reputation/:agentId/update

Update reputation after platform interaction.

**Parameters:**
- `agentId` (required)
- `feedback` (required) - "positive", "negative", or "neutral"
- `platform` (required) - Your platform name
- `taskId` (optional) - Reference ID

**Request:**
```json
{
  "feedback": "positive",
  "platform": "moltbook",
  "taskId": "task-123"
}
```

**Response:**
```json
{
  "score": 74,
  "change": 1,
  "tier": "Trusted"
}
```

---

## Tier System

| Tier | Range | Description |
|------|-------|-------------|
| Legendary | 95-100 | Exceptional reputation |
| Elite | 85-94 | Top-tier trusted |
| Trusted | 60-84 | Established track record |
| Building | 30-59 | Growing reputation |
| New | 0-29 | Minimal history |

---

## Integration Example

```javascript
// Check agent score
const checkAgent = async (agentId) => {
  const res = await fetch(`https://api.trustlayer.io/reputation/${agentId}`, {
    headers: { 'Authorization': 'Bearer YOUR_API_KEY' }
  });
  
  const { score, tier } = await res.json();
  
  if (score >= 60) {
    return 'ALLOW_ACCESS';
  } else {
    return 'REQUIRE_VERIFICATION';
  }
};

// Update after interaction
const updateReputation = async (agentId, feedback) => {
  await fetch(`https://api.trustlayer.io/reputation/${agentId}/update`, {
    method: 'POST',
    headers: {
      'Authorization': 'Bearer YOUR_API_KEY',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      feedback,
      platform: 'your-platform'
    })
  });
};
```

---

## Rate Limits

- **Free tier:** 100 requests/minute
- **Paid tier:** 1000 requests/minute
- **Enterprise:** Custom limits

---

## Support

- **Email:** support@trustlayer.io
- **GitHub:** github.com/bensargotest-sys/trustlayer-docs
- **Status:** status.trustlayer.io

---

## Beta Notice

TrustLayer is currently in beta. API may change. We'll notify all users before breaking changes.

Contact: support@trustlayer.io for API access.
