# IDOR - Trip Access Vulnerability

## 🧠 Description
During testing, it was possible to access another user's trip by reusing the trip URL (ID).
The application does not properly validate ownership before returning the trip data.

---

## 🚨 Vulnerability Type
Insecure Direct Object Reference (IDOR)

---

## 📊 Severity
HIGH

---

## 🔁 Steps to Reproduce

1. Login as User A
2. Create a new trip
3. Copy the trip URL:
   https://dev.app.traveln.ai/trip/<trip_id>/

4. Logout
5. Login as User B
6. Paste the same URL
7. Observe unauthorized access

---

## 🧪 Proof of Concept

### 1. Trip View (User A)
![User A](images/01-userA-trip.png)

### 2. Trip Access from User B
![User B](images/02-userB-access.png)

### 3. Burp Request
![Burp](images/03-burp-request.png)

---

## ⚠️ Impact

- Unauthorized access to user data
- Privacy breach
- Potential account takeover scenarios

---

## 🛠️ Fix Recommendation

- Validate ownership on backend
- Check user_id against trip owner
- Return 403 if unauthorized

---

## 📌 Notes

This vulnerability allows horizontal privilege escalation.
