 

### **1. Obyekt uchun Type yaratish**  
Shunday TypeScript `type` yaratingki, u **kitob** haqidagi quyidagi ma'lumotlarni saqlasin:  
- **nomi** (`string`)  
- **muallifi** (`string`)  
- **sahifalar soni** (`number`)  

---

### **2. Interfeys yaratish va undan foydalanish**  
Shunday `interface` yozingki, u **foydalanuvchi** haqidagi quyidagi ma'lumotlarni saqlasin:  
- **ism**  
- **email**  
- **parol (ixtiyoriy)**  

Keyin shu interfeys asosida yangi obyekt yarating.  

---

### **3. Funksiya uchun Type yozish**  
Shunday TypeScript funksiya yozingki, u **ikkita son qabul qilib**, ularning yig‘indisini qaytarsin.  
Funksiyaning **argumentlari va natijasi uchun Type yozing**.  

---

### **4. Generic Funksiya**  
Shunday **generic** funksiya yozingki, u har qanday turdagi (`T`) qiymatni qabul qilib, **array** ko‘rinishida qaytarsin.  

---

### **5. Array bilan ishlash**  
Quyidagi arrayni oladigan funksiya yozing va undan faqat **juft sonlarni** qaytaradigan qilib tuzing:  

```ts
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```

---

### **6. Type bilan ishlash**  
Shunday `type` yaratingki, u quyidagi **uch xil turdagi mashinalarni** o‘z ichiga olsin:  
- `"sedan"`  
- `"suv"`  
- `"truck"`  

Keyin undan foydalangan holda yangi o‘zgaruvchi yarating.  

---

### **7. Tuple bilan ishlash**  
Shunday **Tuple** (`[string, number]`) yaratingki, u **talabaning ismi va yoshi** ni saqlasin.  

---

### **8. Enum bilan ishlash**  
Quyidagi **hafta kunlarini** o‘z ichiga oladigan `enum` yarating:  
- `Dushanba`, `Seshanba`, ..., `Yakshanba`  

Keyin undan foydalangan holda yangi o‘zgaruvchi yarating.  

---

### **9. Type Merging (birlashtirish)**  
Shunday **ikki xil turdagi obyekt** yarating va ularni **birlashtirib yangi obyekt** hosil qiling.  
