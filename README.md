# 📩 SecureLink Chat

**SecureLink Chat** je privremena end-to-end enkriptirana chat aplikacija koja omogućuje komunikaciju između korisnika putem web sučelja dostupnog preko privremenog javnog linka. Server se pokreće iz .NET Windows desktop aplikacije, a poruke se čuvaju isključivo u memoriji tijekom trajanja sesije. Kada se server ugasi, svi podaci se nepovratno brišu.

---

## 🔑 Osnovne značajke
- **Privremeni pristup** – pokretanje servera generira privremeni javni link (preko TunnelMole).
- **End-to-End enkripcija** – poruke se šifriraju na klijentskoj strani (Signal Protocol / libsodium).
- **Bez trajnog spremanja** – poruke i podaci se brišu nakon gašenja servera.
- **Cross-platform pristup** – dostupno na mobilnim uređajima i računalima putem web preglednika.
- **Real-time komunikacija** – pomoću SignalR WebSockets veze.
- **Jednostavno pokretanje** – Windows desktop aplikacija s gumbima "Start Server" i "Stop Server".
- **Responsive dizajn** – React frontend prilagođen svim veličinama ekrana.

---

## 🛠 Korištene tehnologije

### **Backend**
- [.NET 8](https://dotnet.microsoft.com/)
- [ASP.NET Core](https://docs.microsoft.com/aspnet/core)
- [SignalR](https://dotnet.microsoft.com/apps/aspnet/signalr) – real-time komunikacija
- [Entity Framework Core InMemory](https://learn.microsoft.com/ef/core/) – privremena baza
- [TunnelMole](https://tunnelmole.com/) – privremeni javni link

### **Frontend**
- [React](https://reactjs.org/) + [Vite](https://vitejs.dev/)
- [Tailwind CSS](https://tailwindcss.com/) – stilizacija
- [libsodium.js](https://libsodium.gitbook.io/) – enkripcija poruka
- [Axios](https://axios-http.com/) – HTTP komunikacija
- [@microsoft/signalr](https://www.npmjs.com/package/@microsoft/signalr) – WebSocket konekcija

### **Desktop kontrola**
- [WPF (.NET)](https://learn.microsoft.com/dotnet/desktop/wpf/)
- `Process.Start` API za pokretanje tunela i servera

---

## 📊 Use Case dijagram (Mermaid)

```mermaid
graph TD
    User[📱 Korisnik] -->|Pristup preko web preglednika| WebApp[🌐 SecureLink Chat Web App]
    Admin[Admin - windows app] -->|Pokreće/zaustavlja server| Server[🖥 ASP.NET Core Server]
    WebApp -->|Real-time komunikacija - SignalR| Server
    User -->|Šalje/Prima poruke - E2EE| WebApp
    Server -->|Privremeno pohranjuje poruke - InMemory DB| DB[🗄 Privremena baza]
