# પ્રકરણ 1: First principles અને reverse engineering

## ખર્ચ ખરેખર ક્યાં છે?

CA/CMA નું કામ અઘરું છે એટલે મોંઘું નથી. તે કલાકોને લીધે મોંઘું છે: data ભેગો કરવો, type કરવો, મેળવવો, તપાસવો અને client પાછળ દોડવું.

- એક engagement નો આશરે 70–80% ભાગ આવું હાથનું કામ છે.
- ફક્ત 20–30% ભાગ સાચો નિર્ણય (judgment) છે.

એટલે 50% ભાવ ત્યારે જ શક્ય બને જ્યારે હાથના કલાકો લગભગ 80% ઘટે. માણસોને 10% ઝડપી બનાવવાથી તે નહીં થાય.

## First principles: CA નું કામ ખરેખર શું છે?

પરંપરા કાઢી નાખો તો દરેક કામ આ ચાર ભાગનું બનેલું છે:

**Data આવે → નિયમ લાગે → શંકાવાળી entry પર માણસ નિર્ણય લે → sign થયેલું output**

એટલે ચાર જ મશીન જોઈએ:

1. ગંદા documents ને સાફ data માં ફેરવવાની રીત.
2. કાયદાને code તરીકે લાગુ કરવાની રીત.
3. માણસને ફક્ત શંકાવાળી entry બતાવવાની રીત.
4. Filing અથવા report બનાવવાની રીત.

બાકીનું બધું આદત છે, અને આદત કાઢી શકાય.

## Reverse engineering: output થી પાછળ ચાલો

Architecture ઉપરથી નીચે design ન કરો. છેલ્લા sign થયેલા output થી શરૂ કરો અને દર વખતે પૂછો: "આના માટે શું જોઈએ?"

### ઉદાહરણ: GST 2B reconciliation

1. **Output:** matched/unmatched report અને ITC claim નો આંકડો, CA ની sign સાથે.
2. **એના માટે શું જોઈએ?** દરેક purchase invoice પર tag: matched, mismatched, અથવા missing.
3. **એના માટે શું જોઈએ?** Purchase register અને 2B data એક જ format માં.
4. **એના માટે શું જોઈએ?** Tally export, Excel, PDF અને portal JSON માંથી data કાઢવો.

દરેક જવાબ એક module બને છે. Output ને જે ન જોઈએ તે module ક્યારેય ન બનાવો.

## આગળ

આ module ને layer માં કેવી રીતે ગોઠવવા તે [પ્રકરણ 2](02-architecture.md) માં છે.
