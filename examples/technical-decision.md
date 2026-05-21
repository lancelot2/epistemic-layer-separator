# Example: Technical Decision — Before & After

**Context:** User asks "Should we use Supabase or self-hosted Postgres?"

---

## ❌ Without Epistemic Layer Separator

> For a SaaS at your stage, Supabase is clearly the better choice. It handles auth, storage,
> and real-time out of the box, saving weeks of setup. It scales well to millions of rows.
> Self-hosted Postgres makes sense only for very large companies. Cost: ~€50–200/month.

**What's wrong:** "Clearly better" without knowing constraints. Cost estimate fabricated.
"Scales well" without knowing the workload.

---

## ✅ With Epistemic Layer Separator

### 🟢 Établi
- Supabase est un BaaS sur Postgres avec auth, storage, real-time, Edge Functions (docs officielles)
- Supabase a un free tier et des plans payants à partir de $25/mo (vérifier supabase.com/pricing)
- Self-hosted Postgres donne un contrôle total sur la configuration et la localisation des données

### 🟡 Inféré
- Pour une équipe sans DevOps dédié, Supabase réduit significativement la charge opérationnelle
  — pattern observable dans des centaines de retours d'équipes early-stage
- Si tu es déjà sur Supabase, la migration n'a de sens que si une contrainte spécifique l'exige

### 🔴 Spéculatif
- Coût mensuel à ton échelle : impossible sans tes métriques (requêtes, volume, bandwidth) ⚠️
- Performance pour ton workload : "scale bien" est vide sans connaître ton schéma et tes SLAs ⚠️
- Implications RGPD précises : dépendent de ton secteur et de ton DPA ⚠️

---

### Synthèse

Supabase est probablement le bon choix si tu n'as pas de contrainte spécifique.
Avant de conclure : projette ta facture à 12 mois avec tes métriques, valide la
localisation EU si tu as des données sensibles, teste les perfs sur ton schéma réel.
