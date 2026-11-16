# પ્રકરણ 3: Team અને integration

## કોને શેના માટે વાપરવું

| કોણ | શું કામ | કેવી રીતે |
|---|---|---|
| **CA/CMA** | નિયમ નક્કી કરે, છેલ્લી sign કરે | દરેક નિયમ "input → સાચો જવાબ" રૂપે test case સાથે લખે; ફક્ત શંકાવાળી entry તપાસે |
| **Software engineer** | Portal, database, queue, Tally/GST portal સાથે જોડાણ | CA ના નિયમને code માં ફેરવે; data security સંભાળે |
| **AI engineer** | AI ની ચોકસાઈ | Prompt, test set, confidence score બનાવે; દર અઠવાડિયે accuracy માપે |
| **AI (LLM)** | ગંદા data ને સાફ કરવો | PDF, invoice, bank statement વાંચી એક format માં મૂકે; draft લખે |
| **AI agents** | એક agent = એક કામ | Reconciliation agent, classification agent, notice-draft agent; દરેક પોતાનું step કરી આગળ મોકલે |

## Team કેવી રીતે બનાવવી

- **નાની ટીમ, ઊંચી ક્ષમતા.** શરૂઆત 3 જણથી: 1 CA/CMA, 1 AI engineer, 1 software engineer. 10 સામાન્ય માણસ કરતાં 3 ઉત્તમ સારા.
- **Degree નહીં, પુરાવો જુઓ.** Interview માં પૂછો: "તમે ઉકેલેલી સૌથી અઘરી સમસ્યા કઈ, અને બરાબર કેવી રીતે ઉકેલી?" જેણે ખરેખર કર્યું હોય તે વિગત આપી શકે.
- **બે બાજુ સમજનાર શોધો.** Code શીખવા તૈયાર CA અને GST સમજવા તૈયાર engineer સૌથી કીમતી છે.
- **Leader પોતે કામ જાણે.** Team lead ફક્ત manage ન કરે; તે જાતે return ભરી શકે અથવા code લખી શકે.

## Pod: department નહીં, નાની ટીમ

દરેક service line માટે ત્રણ જણનો એક pod:

- **1 CA/CMA:** સાચાપણું અને નિયમનો માલિક.
- **1 AI engineer:** extraction, agents અને accuracy testing નો માલિક.
- **1 software engineer:** pipeline, integration અને console નો માલિક.

Pod પહેલા કામ હાથે કરે, પછી પોતાનો જ દુખાવો automate કરે.

## કામ કેવી રીતે વહેંચવું

- **દરેક કામ પર એક નામ.** "Accounts department" નહીં, એક માણસ જવાબદાર. Department ને સવાલ ન પૂછી શકાય, માણસને પૂછી શકાય.
- **Process નહીં, પરિણામ સોંપો.** "આ code લખો" નહીં; "TDS return ની મિનિટ 120 થી 30 કરો."
- **દરેક service નો એક માલિક.** તે output થી client સુધી આખી જવાબદારી લે.

## Integrate કેવી રીતે કરવું

- **સીધી વાત.** Engineer ને સવાલ હોય તો સીધો CA ને પૂછે, manager મારફતે નહીં. સૌથી ટૂંકો રસ્તો એ જ સાચો.
- **બધા સાથે બેસે.** CA એક રૂમમાં અને engineers બીજામાં, એવું નહીં.
- **Engineer એક અઠવાડિયું CA નું કામ હાથે કરે.** દુખાવો જાતે અનુભવે તો જ સાચું automation બને.
- **એક જ scoreboard.** દીવાલ પર ત્રણ આંકડા: કામ દીઠ મિનિટ, ભૂલનો દર, turnaround time.

## ત્રણ નિયમ જે integration ચલાવે

1. **એક ટેબલ, એક માપ.** ત્રણેય જણ "કામ દીઠ મિનિટ" અને "ભૂલનો દર" પર મપાય, પોતપોતાના output પર નહીં.
2. **કાયદો code માં, prompt માં નહીં.** CA નિયમ test case સાથે લખે, engineer code કરે. AI ફક્ત ગંદા input અને draft સંભાળે.
3. **દરેક સુધારો training data છે.** CA output સુધારે એટલે તે નવો test case બને, અને એ ભૂલ પાછી ન આવે.
