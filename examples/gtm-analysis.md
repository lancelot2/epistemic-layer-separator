# Example: GTM Analysis — Before & After

**Context:** User asks "What GTM strategy should we use to launch Cala in France?"

---

## ❌ Without Epistemic Layer Separator

> Cala should target Series A and B SaaS companies in France. This segment has the highest
> willingness-to-pay and the shortest sales cycles. The French AI market is estimated at €1.2B.
> A PLG motion combined with developer-first positioning will be most effective.
> Pricing in the €500–2000/month range aligns with comparable tools.

**What's wrong:** Every claim sounds equally confident. The €1.2B figure is likely fabricated.
"Highest willingness-to-pay" has no source. "Shortest sales cycles" is inference as fact.

---

## ✅ With Epistemic Layer Separator

### 🟢 Établi
- Cala expose une API de knowledge graph avec un MCP server fonctionnel
- La France compte ~4 000 startups tech actives (Bpifrance 2024)
- Les entreprises françaises ont une sensibilité documentée à la souveraineté des données (textes CNIL)

### 🟡 Inféré
- Les équipes produit série A/B sont probablement le meilleur segment — par analogie avec
  Segment, Retool, Airbyte qui ont trouvé leur PMF dans cette bande
- Un positionnement developer-first semble adapté : Cala expose une API, donc les acheteurs
  sont des CTOs/lead engineers → oriente vers un motion PLG ou bottoms-up
- La friction RGPD chez les concurrents US est un levier différenciateur réel

### 🔴 Spéculatif
- Toute estimation de taille de marché sans source nommée ⚠️
- La fourchette de pricing sans données sur les premiers deals ⚠️
- "Sales cycle court en série A" — pattern général, peut ne pas tenir pour l'infrastructure knowledge graph ⚠️

---

### Synthèse

Un lancement France logique cible les équipes produit série A/B via un motion developer-first.
Le levier RGPD est réel et sous-exploité.

**Ce qui reste à valider :** données des premiers clients, pricing (tester sur les prospects),
taille de marché calculée depuis le bas plutôt que top-down.
