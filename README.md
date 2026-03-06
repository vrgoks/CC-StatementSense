# CC-StatementSense

**A browser-based HDFC credit card statement analyser. No server. No login. No data leaving your tab.**

Upload your HDFC TataNeu Infinity credit card statement (XLS or XLSX) and get an instant breakdown of where your money went — with your NeuCoins, rewards, and merchant intel baked in.

---

## What it does

- **Parses your statement** — detects cardholder name, card number, and statement period automatically from the file header
- **Dashboard with stat cards** — Total Spend, Largest Transaction, Total Payments, Total NeuCoins, Top Category, and a Reward Rate KRI (NeuCoins per ₹100 spent)
- **Spending by Category** — donut chart, clickable segments drill into transactions
- **Top Merchants** — horizontal bar chart, click any bar to see that merchant's full transaction history
- **Spend Pattern** — daily or weekly bar chart of your spending across the statement period
- **UPI breakdown** — grouped by payee, each row expandable to show individual transactions
- **Anomaly detection** — flags transactions that are 3× or more above your average spend
- **Rewards Program Points Summary** — parses the bonus NeuCoins table directly from your statement; each program row (Add_Titan_Tanishq, NeuCoins_on_UPI_Acc, etc.) maps to the transactions that likely generated it, with an estimated point calculation
- **Merchant remapping** — rename any merchant to something human-readable, reassign its category; propagates across all matching transactions; 41 common HDFC/Coimbatore merchants pre-loaded
- **Custom categories** — add your own spending categories beyond the defaults
- **PDF export** — full dashboard export with all collapsed sections auto-expanded before capture

---

## Privacy

Everything runs inside your browser tab.

- File is read locally — never transmitted anywhere
- No accounts, no logins, no servers, no tracking
- Close the tab and everything disappears
- Card number and name are masked in the UI

---

## How to use

1. Download your HDFC TataNeu Infinity CC statement as XLS or XLSX from NetBanking
2. Open `StatementSense.html` in any modern browser
3. Upload the file
4. That's it

> **Note:** If you've opened your statement in Excel before uploading, some data may have been quietly reformatted. Use the file directly as downloaded from your bank portal for best results.

---

## Rewards mapping

StatementSense maps your Rewards Program Points Summary to individual transactions using rules from the TataNeu Infinity Card T&Cs:

| Program | Rule | Rate |
|---|---|---|
| Add_Titan_Tanishq | Merchant contains Titan / Tanishq | 3.5% additional |
| Add_TataPayment | Merchant contains Tata Pay | 3.5% additional |
| Add_BigBasket | Merchant contains BigBasket | 3.5% additional |
| Base_Grocery | Category = Groceries, non-UPI | 1.5% base |
| NeuCoins_on_Telecom | Category = Telecom | 1.5% base |
| Neucoins_on_Utility | Category = Utilities | 1.5% base |
| NeuCoins_on_UPI_Acc | UPI-tagged transactions | 0.5% base |
| Retail Spends Greater50K | Milestone bonus | Not transaction-mappable |

Estimates are directional — HDFC's actual calculation uses Merchant IDs and Terminal IDs that aren't in your statement file. The UI says so, clearly.

---

## Tech

Single HTML file. No framework. No build step. No dependencies to install.

External libraries loaded from CDN (requires internet on first load):
- [SheetJS](https://sheetjs.com/) — XLSX parsing
- [Chart.js](https://www.chartjs.org/) — charts
- [html2canvas](https://html2canvas.hertzen.com/) + [jsPDF](https://github.com/parallax/jsPDF) — PDF export

---

## Limitations

- Built and tested against **HDFC TataNeu Infinity CC** statements only
- Other HDFC card formats may or may not parse correctly
- Multi-bank support is on the roadmap

---

## Roadmap

- [ ] Multi-bank support (ICICI, Axis, SBI)
- [ ] Month-on-month comparison — load two statements, diff by category
- [ ] Recurring transaction detection
- [ ] Budget envelopes — set category limits, track progress
- [ ] Export transactions to CSV

---

*Built as a personal finance tool. Not affiliated with HDFC Bank or Tata Neu.*
