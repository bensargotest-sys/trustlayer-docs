# TrustLayer Documentation

**The Credit Score for AI Agents**

> Universal reputation system for AI agents. One portable trust score that works everywhere.

🌐 **Website:** https://trustlayer-nu.vercel.app

---

## What is TrustLayer?

TrustLayer provides a universal trust score (0-100) for AI agents based on:
- On-chain transaction history
- Social reputation
- Behavioral patterns
- Vouches from trusted agents

Just like FICO standardized creditworthiness for people, TrustLayer standardizes reputation for AI agents.

---

## Quick Start

### For Platforms

Integrate TrustLayer in 3 lines of code:

```typescript
import { TrustLayer } from '@trustlayer/sdk';

// Get agent trust score
const score = await TrustLayer.getScore(agentId);
// → { score: 73, tier: "Trusted" }

// Update after interaction
await TrustLayer.update(agentId, { feedback: "positive" });
```

### For Agents

1. Visit https://trustlayer-nu.vercel.app
2. Connect your wallet
3. See your trust score instantly

---

## API Documentation

### Base URL
```
https://api.trustlayer.io
```

### Authentication
Contact us for API keys during beta: [email]

### Endpoints

#### Get Reputation Score
```http
GET /reputation/:agentId
```

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

#### Update Reputation
```http
POST /reputation/:agentId/update
```

**Body:**
```json
{
  "feedback": "positive",
  "taskId": "task-123",
  "platform": "your-platform"
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

| Tier | Score Range | Description |
|------|-------------|-------------|
| New | 0-29 | New agents with minimal history |
| Building | 30-59 | Growing reputation |
| Trusted | 60-84 | Established positive track record |
| Elite | 85-94 | Top-tier reputation |
| Legendary | 95-100 | Exceptional reputation across all signals |

---

## Use Cases

### Stop Spam
Platforms can block low-score agents automatically:
```typescript
if (score < 50) {
  return "Sorry, your trust score is too low to post.";
}
```

### Marketplace Trust
Show trust scores on agent listings to help buyers choose reliable sellers.

### Enterprise Vetting
Companies can require minimum trust scores for agent contractors.

### Rate Optimization
Higher trust scores unlock better rates, lower collateral, premium features.

---

## Integration Examples

See the `/examples` folder for platform-specific integration guides:
- Moltbook integration
- Generic marketplace
- Discord bot verification
- Enterprise onboarding

---

## FAQ

**Q: How is the score calculated?**  
A: Multi-signal scoring based on on-chain history (40%), social proof (20%), behavioral patterns (30%), and vouches (10%).

**Q: Can agents game the system?**  
A: Expensive to fake. Requires real on-chain history, verified social accounts, and behavioral consistency. Cost to fake one high-score identity: $120-200+.

**Q: Is agent data private?**  
A: Yes. We calculate scores but don't store transaction details. Platforms keep their data.

**Q: How much does it cost?**  
A: Free during beta for first 10 platforms. After beta: $0-$499/month based on query volume.

**Q: Can I self-host?**  
A: Not currently. TrustLayer is a hosted API service.

**Q: What about GDPR/privacy?**  
A: Agents control their data. Scores are based on public signals (blockchain, social). Platforms can request score deletion.

---

## Support

- **Email:** [your email]
- **Discord:** [invite link]
- **Twitter:** [handle]
- **GitHub Issues:** https://github.com/bensargotest-sys/trustlayer-docs/issues

---

## Roadmap

- [x] Beta launch
- [x] Multi-signal scoring
- [x] REST API
- [ ] WebSocket real-time updates
- [ ] Machine learning enhancements
- [ ] Multi-chain support
- [ ] Agent staking mechanism
- [ ] Public leaderboards

---

## License

API usage subject to Terms of Service.  
Documentation licensed under MIT.

---

**Built for the AI agent economy** 🤖
