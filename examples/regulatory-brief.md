# Example: Regulatory Brief — Before & After

**Context:** User asks "Does our AI receptionist need to comply with the EU AI Act?"

---

## ❌ Without Epistemic Layer Separator

> Yes, your AI receptionist falls under the EU AI Act as a Limited Risk system, requiring
> transparency obligations. You'll need to inform users they're interacting with an AI.
> Voice assistants are not classified as high-risk. Full compliance required by August 2026.

**What's wrong:** Classification is interpretation, not fact. Timeline may be outdated.
"Not high-risk" is a legal conclusion depending on specific use context.

---

## ✅ With Epistemic Layer Separator

### 🟢 Établi
- L'EU AI Act a été publié au JO de l'UE en juillet 2024 (Règlement 2024/1689)
- L'Article 50 impose d'informer les utilisateurs qu'ils interagissent avec une IA
- Les systèmes à "haut risque" (Annexe III) n'incluent pas explicitement les réceptionnistes IA

### 🟡 Inféré
- Un réceptionniste IA de coordination tombe probablement dans la catégorie Risque Limité
  — lecture de l'Annexe III qui ne mentionne pas ce cas d'usage
- L'obligation d'informer les patients s'appliquera probablement — Article 50(1) est clair
  pour les systèmes conversationnels face à des humains non informés

### 🔴 Spéculatif
- Calendrier d'application précis : les dates varient par obligation, textes nationaux à venir ⚠️
- Si le produit évolue vers du triage médical : la classification de risque peut changer ⚠️

---

### Synthèse

Conformité minimale probable : informer les utilisateurs qu'ils parlent à une IA (Article 50),
documenter le système, assurer des mécanismes de recours humain.

⚠️ **Ceci n'est pas un avis juridique. Validation par un cabinet spécialisé AI Act
indispensable avant tout déploiement commercial dans la santé.**
