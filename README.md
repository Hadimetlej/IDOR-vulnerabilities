# 🔐 IDOR - Trip Access Vulnerability

This repository documents a real-world Insecure Direct Object Reference (IDOR) vulnerability discovered during authorized security testing.

The application fails to properly enforce access control on trip resources, allowing an attacker to access another user's trip by reusing or modifying the trip identifier.

---

## 📌 Key Issue

- Missing authorization validation on backend
- Direct access to sensitive resources via predictable IDs
- No ownership check before returning data

---

## ⚠️ Impact

- Unauthorized access to user data
- Privacy violation
- Horizontal privilege escalation

---

## 🛠️ Root Cause

- Weak access control implementation
- Trusting user-supplied identifiers
- Lack of server-side authorization checks

---

## ✅ Recommendation

- Validate resource ownership on every request
- Implement proper access control mechanisms (RBAC / ABAC)
- Return 403 for unauthorized access attempts
