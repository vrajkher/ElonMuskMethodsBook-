# પ્રકરણ 2: Architecture

## પાંચ પગથિયાંની pipeline

```
Client portal        →  file upload, status જોવું
      ↓
Data intake          →  AI બધું એક ledger format માં કાઢે
      ↓
Rules engine         →  tax નો કાયદો tested code તરીકે   ←──┐
      ↓                                                      │
AI agents            →  reconcile, classify, draft            │ CA ના સુધારા
      ↓                                                      │ નવા test case બને
CA review console    →  ફક્ત exception approve, sign off  ───┘
```

પહેલું પગથિયું client નું છે. વચ્ચેના ત્રણ software અને AI ચલાવે છે. છેલ્લું CA/CMA ના નિર્ણયનું છે.

## ચાર layer

| Layer | શું કરે | કોણ બનાવે |
|---|---|---|
| **1. Intake** | Client bank statement, invoice, Tally/Zoho export, portal data (GST, TDS, 26AS) upload કરે. AI તેને એક સાફ ledger format માં ફેરવે. | AI engineer + software engineer |
| **2. Rules engine** | Tax અને compliance ના નિયમ tested code તરીકે, prompt તરીકે નહીં. | CA/CMA નિયમ લખે, software engineer code કરે |
| **3. AI agents** | એક agent = એક કામ (reconciliation, classification, notice draft, working papers). દરેક draft સાથે confidence score અને source link આપે. | AI engineer |
| **4. Review console** | CA ને ફક્ત exception અને ઓછા score વાળી entry દેખાય. તે approve કરી sign કરે. | Software engineer + CA/CMA |

## મુખ્ય નિયમ: કાયદો code માં, AI માં નહીં

Tax ની ગણતરી code કરે, કારણ કે code દર વખતે એક જ જવાબ આપે. AI ફક્ત વાંચવા, ગોઠવવા અને draft બનાવવા માટે છે.

## ત્રણ contract જે બધું જોડે

Integration એટલે module વચ્ચેના ત્રણ કરાર. દરેક કરાર બે માણસોને પણ જોડે છે.

| Contract | શું છે | કોણ નક્કી કરે |
|---|---|---|
| **Data schema** | એક standard ledger format: party, GSTIN, invoice, રકમ, tax, source link | Software engineer + CA |
| **Rule spec** | દરેક નિયમ "input → સાચો જવાબ" રૂપે, test case સાથે | CA + software engineer |
| **Confidence score** | AI દરેક જવાબ સાથે score આપે; threshold થી ઓછો હોય તો entry માણસ પાસે જાય | AI engineer + CA |

## કામ system માં કેવી રીતે ફરે

System એક job queue તરીકે ચાલે છે:

1. File આવે અને queue માં જાય.
2. દરેક module પોતાનું step કરે.
3. Result એક database માં લખાય.
4. Job આગળના module ને જાય.
5. શંકાવાળી entry CA ના console માં જાય.
6. CA approve કરે એટલે output તૈયાર.

CA જે સુધારે તે નવો test case બને, એટલે એ ભૂલ ફરી ન થાય.

Module ફક્ત schema મારફતે વાત કરે છે. એટલે એક module બદલો કે સુધારો તો બીજા તૂટતા નથી. નવી service (જેમ કે TDS) માટે intake, queue અને review console ફરી વપરાય; ફક્ત નવા નિયમ ઉમેરવાના.

## શરૂઆતનો tech stack

- Python
- PostgreSQL
- એક job queue
- Extraction માટે LLM API
- સાદો web console

એક કામ શરૂથી અંત સુધી ચાલે નહીં ત્યાં સુધી આનાથી વધારે કંઈ ન બનાવો.

## Data security

Client data ની સુરક્ષા પહેલા દિવસથી system માં હોવી જોઈએ. નહીં તો firms તમને file મોકલશે નહીં.
