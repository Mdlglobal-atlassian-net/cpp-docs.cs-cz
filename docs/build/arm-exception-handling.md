---
title: Zpracování výjimek ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: 8a2bae8e42ac6a624bebe7c185ac7e0ade8d5491
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476939"
---
# <a name="arm-exception-handling"></a>Zpracování výjimek ARM

Windows na ARM používá stejné strukturovaného zpracování mechanismus pro asynchronní výjimky generované hardwaru a synchronní výjimky generované softwarových výjimek. Obslužné rutiny výjimek specifické pro jazyk jsou postavené na Windows zpracování s použitím jazyka pomocné funkce strukturovaných výjimek. Tento dokument popisuje zpracování výjimek v Windows na ARM a pomocné rutiny jazyka, používané kódu, který je generován assembler Microsoft ARM a kompilátorem MSVC.

## <a name="arm-exception-handling"></a>Zpracování výjimek ARM

Používá Windows na ARM *parsovat kódy unwind* řídit během odvíjení zásobníku [strukturované zpracování výjimek](/windows/desktop/debug/structured-exception-handling) (SEH). Unwind kódy jsou posloupnost bajtů, které jsou uložené v části .xdata spustitelné bitové kopie. Popisují operace kód prologu a epilogu funkce abstraktní způsobem tak, aby efekty prologu funkce může být v rámci přípravy odvíjení rámce zásobníku volajícího vrátit zpět.

EABI ARM (vložené aplikace binary interface) určuje parsovat kódy unwind odvíjení model výjimek, který používá, ale nepostačuje pro SEH odvíjení ve Windows, které musí zpracovat asynchronní případech, kdy procesor je uprostřed prologu nebo epilogu funkce. Windows také odděluje odvíjení řízení na odvíjení úrovni funkcí a uvolnění oboru specifické pro jazyk, který unified v ARM EABI. Z těchto důvodů Windows na ARM Určuje další podrobnosti pro data a procedura odvíjení.

### <a name="assumptions"></a>Předpoklady

Spustitelné Image pro Windows na ARM, použijte formát Portable Executable (PE). Další informace najdete v tématu [formátech Microsoft PE a COFF specifikace](http://go.microsoft.com/fwlink/p/?linkid=84140). Informace o zpracování výjimek je uložen v částech .pdata a .xdata bitové kopie.

Mechanismus zpracování výjimek určitých předpokladů o kód, který následuje na ARM ABI pro Windows:

- Když dojde k výjimce v těle funkce, nezáleží, jestli jsou prologu operace vrátit zpět nebo epilogu operace se provádějí v dopředné způsobem. Jak by měl vytvářet identické výsledky.

- Prologů a epilogů mají tendenci k sobě navzájem zrcadlení. To lze použít ke snížení velikosti metadata potřebná k popisu uvolnění.

- Funkce bývají poměrně malý. Několik optimalizací spoléhat na to pro efektivní balení data.

- Pokud je podmínka je umístěn na epilogu, vztahuje stejnou měrou na každou instrukci v epilogu.

- Pokud ukazatel zásobníku (SP) je uložen v beze změny tak, aby může být kdykoli obnoven původní SP v celém funkci, jiný registr v prologu, které musí zůstat registru.

- Není-li této uložené Procedury se uloží do jiného zaregistrovat, musí všechny manipulace výhradně nastat do během prologu a epilogu.

- K provedení operace unwind jiné rámce zásobníku, jsou požadovány tyto operace:

  - Upravit r13 (SP) v přírůstcích po 4 bajty.

  - Vyvolat přes POP jeden nebo více celočíselné registry.

  - Vyvolat přes POP VFP jeden nebo více (virtuální s plovoucí desetinnou čárkou) zaregistruje.

  - Zkopírujte hodnotu libovolného registru r13 (SP).

  - Pomocí operace malé po snížení zatížení SP ze zásobníku.

  - Analyzovat, jeden z několika typů jasně definovaných rámce.

### <a name="pdata-records"></a>.pdata Records

Záznamy .pdata formátu PE obrázku jsou uspořádaného pole pevnou délkou položek, které popisují každý manipulace s zásobníku funkce. Funkce typu list, které jsou funkce, které nevyžadují další funkce, nevyžadují .pdata záznamy při jejich nedochází zásobníku. (To znamená, se nevyžadují žádné místní úložiště a nemáte k uložení nebo obnovení registrů stálé.). Záznamy pro tyto funkce lze vynechat z části .pdata pro úsporu místa. Operace unwind z jednoho z těchto funkcí můžete stačí zkopírovat zpáteční adresu z na odkaz zaregistrovat (LR) k čítači programu (PC) na vypracovat tak, aby volající.

Každý záznam .pdata pro ARM je 8 bajtů. Obecný formát záznamu umístí relativní virtuální adresu (RVA) zahájení funkce v první slovo 32-bit, za nímž následuje druhý slova, která obsahuje buď ukazatelem na blok .xdata proměnné délky, nebo sbalené aplikace word popisující kanonické funkce odvíjení pořadí, jak je uvedené v této tabulce:

|Posun aplikace Word|Bity|Účel|
|-----------------|----------|-------------|
|0|0-31|*Funkce spuštění RVA* je adresa RVA 32-bit zahájení funkce. Pokud funkce obsahuje kód pro thumb, musí být nastavena s nízkou bit tuto adresu.|
|1|0-1|*Příznak* je 2 bitové pole, která určuje, jak interpretovat zbývajících 30 bitů druhý .pdata slova. Pokud *příznak* je 0, pak zbývající bity formulář *RVA informace o výjimce* (s nízkou dva bity implicitně 0). Pokud *příznak* je nenulová, zbývající bity formuláře *zabaleny Unwind Data* struktury.|
|1|2-31|*Informace o výjimce RVA* nebo *zabaleny Unwind Data*.<br /><br /> *Informace o výjimce adresu RVA* je adresa struktury výjimky proměnné délky informace uložené v části .xdata. Tato data musí být zarovnaná na 4 bajty.<br /><br /> *Provedené zabalené Unwind Data* je komprimovaný popis operace nutné k provedení operace unwind z funkce, za předpokladu, že kanonickém tvaru. V tomto případě žádný záznam .xdata je povinný.|

### <a name="packed-unwind-data"></a>Provedené zabalené Unwind Data

Pro funkce, jejíž prologů a epilogů postupujte mapovými kanonický tvar je popsáno níže, vrátit se zpět lze data. To eliminuje potřebu záznam .xdata a taky výrazně snižuje prostor potřebný k poskytování unwind data. Canonical prologů a epilogů jsou navržené ke splnění běžných požadavků jednoduchou funkci, která nevyžaduje, aby obslužná rutina výjimky a provádí operace jeho nastavení a jejich vyřazování z provozu v standardní pořadí.

Tato tabulka zobrazuje ve formátu sady .pdata záznam, který obsahuje balené unwind dat:

|Posun aplikace Word|Bity|Účel|
|-----------------|----------|-------------|
|0|0-31|*Funkce spuštění RVA* je adresa RVA 32-bit zahájení funkce. Pokud funkce obsahuje kód pro thumb, musí být nastavena s nízkou bit tuto adresu.|
|1|0-1|*Příznak* je 2 bitové pole, která má tyto význam:<br /><br />-00 = sbalené unwind dat nepoužívá; zbývající bity odkazují na záznam .xdata.<br />-01 = sbalené unwind data.<br />-10 = sbalené unwind dat, ve kterém funkce předpokládá, že je mít žádné prologu. To je užitečné pro popis funkce fragmentů, které jsou nesousedících s spuštění funkce.<br />-11 = rezervované.|
|1|2-12|*Funkce délka* je 11bitový pole, která poskytuje délka celou funkci v bajtech, děleno 2. Pokud funkce je větší než 4 kB, záznam úplné .xdata musí použít.|
|1|13-14|*Staré* je 2 bitové pole, která určuje, jak funkce vrátí:<br /><br />-00 = vrátit přes pop {pc} ( *L* bit příznaku musí být nastavena na hodnotu 1 v tomto případě).<br />-01 = vrátit pomocí větev 16 bitů.<br />-10 = vrátit pomocí 32bitové větve.<br />-11 = žádná epilogu vůbec. To je užitečné pro popis fragmentu nesousedících funkce, která může obsahovat jenom prologu, ale jehož epilogu je jinde.|
|1|15|*H* je 1-bit příznaku, která určuje, zda funkce "homes" parametr celé číslo registruje (r0 – r3) podle jejich ukládání na začátku funkce a uvolní 16 bajtů zásobníku před vrácením. (0 = není domácí registrů, 1 = registrů nemovitostí.)|
|1|16-18|*Reg* 3 bitové pole, která určuje index posledního uložení register není typu volatile. Pokud *R* bit na hodnotu 0, pak se ukládají pouze celočíselné registry a předpokládá, že jsou v rozsahu r4 rN, kde N je rovna 4 + *Reg*. Pokud *R* bit na hodnotu 1 a pak se ukládají pouze s plovoucí desetinnou čárkou registry a předpokládá, že jsou v rozsahu d8 – rozlišující název, kde N je rovna hodnotě 8 + *Reg*. Speciální kombinací *R* = 1 a *Reg* = 7 znamená, že jsou uloženy žádné Registry.|
|1|19|*R* je 1-bit příznaku, která označuje, jestli jsou uložené registry stálé celočíselné registry (0) nebo s plovoucí desetinnou čárkou registrů (1). Pokud *R* je nastavena na hodnotu 1 a *Reg* je nastaveno na hodnotu 7, byly nabídnuty žádné registry není typu volatile.|
|1|20|*L* je 1-bit příznaku, která určuje, zda funkce uloží a obnoví LR, spolu s jinými registry indikován *Reg* pole. (0 = nelze uložit/obnovit, 1 = nemá uložit/obnovit.)|
|1|21|*C* je 1bitový příznak, který značí, zda funkce obsahuje další pokyny k nastavení řetěz snímků pro rychlé stack walking (1) nebo ne (0). Pokud je tento bit nastaven, r11 implicitně přidá do seznamu celé číslo bez registry uložit. (Zobrazit omezení pod if *C* příznak se používá.)|
|1|22-31|*Stack – upravit* je 10 bitové pole, která určuje počet bajtů zásobníku, které jsou přiděleny pro tuto funkci hodnotou 4. Nicméně je možné přímo kódovat pouze hodnoty mezi hodnotu 0x000 0x3F3. Funkce, které přidělit víc než 4044 bajtů zásobníku musí používat úplnou .xdata záznam. Pokud *upravit zásobníku* pole je 0x3F4 nebo větší, pak nízké bity 4 mají zvláštní význam:<br /><br />-Služba bits 0-1 určit počet slova zásobníku úpravy (1 – 4) odečte 1.<br />-Bit 2 je nastavena na hodnotu 1, pokud prologu kombinovat tato úprava do jeho pomocí operace push.<br />-Bit 3 je nastavena na hodnotu 1, pokud epilogu kombinovat tato úprava do jeho operace pop.|

Z důvodu možných redundance ve výše uvedené kódování platí tato omezení:

- Pokud *C* je příznak nastaven na hodnotu 1:

   - *L* musí také být nastaven příznak na hodnotu 1, protože řetězení rámce vyžaduje r11 a LR.

   - R11 nesmí být součástí sadu registrů, popsaného *Reg*. To znamená, pokud jsou vloženy r4 r11, *Reg* by měl pouze popisují r4 r10, protože *C* příznak značí r11.

- Pokud *Ret* je nastaveno na hodnotu 0, *L* příznak musí být nastavena na hodnotu 1.

Porušení těchto omezení způsobí, že Nepodporovaná pořadí.

Pro účely diskuse níže jsou dva příznaky pseudo odvozeny z *upravit zásobníku*:

- *PF* nebo "prologu skládání" znamená, že *upravit zásobníku* 0x3F4 nebo sadu větší a bit. 2.

- *EF* nebo "epilogu skládání" znamená, že *upravit zásobníku* 0x3F4 nebo sadu 3 větší a bit.

Prologů pro kanonické funkce může mít až 5 pokyny (Všimněte si, že se vzájemně vylučují 3a a 3b):

|Instrukce|OpCode se předpokládá, že k dispozici pokud:|Velikost|Operační kód|Parsovat kódy unwind|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*==1|16|`push {r0-r3}`|04|
|2|*C*== 1 nebo *L*== 1 nebo *R*== 0 nebo PF == 1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*== 1 a (*L*== 0 a *R*== 1 a PF == 0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*== 1 a (*L*== 1 nebo *R*== 0 nebo PF = 1)|32|`add r11,sp,#xx`|FC|
|4|*R*== 1 a *Reg* ! = 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Upravit zásobníku* ! = 0 a PF == 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instrukce 1 je vždy k dispozici Pokud *H* bit nastaven na hodnotu 1.

Nastavení řetězení rámce, je k dispozici 3a instrukce nebo 3b Pokud *C* bit nastaven. Je 16 bitů `mov` Pokud ne, vložení registrů než r11 a LR; v opačném případě je 32-bit `add`.

Pokud není zadána a regulovat složeny, instrukce 5 je úprava explicitní zásobníku.

Pokyny, 2 a 4 jsou nastaveny podle toho, jestli je požadovaná oznámení. Tato tabulka shrnuje, která registruje se ukládají na základě *C*, *L*, *R*, a *PF* pole. Ve všech případech *N* rovná *Reg* + 4, *E* rovná *Reg* + 8, a *S* je rovno (~*Zásobníku upravit*) a 3.

|C|L|R|PF|Celočíselné registry vloženo|Zaregistruje VFP vloženo|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|r4-r*N*|žádná|
|0|0|0|1|r*S*-r*N*|žádná|
|0|0|1|0|žádná|d8-d*E*|
|0|0|1|1|r*S*-r3|d8-d*E*|
|0|1|0|0|r4-r*N*, LR|žádná|
|0|1|0|1|r*S*-r*N*, LR|žádná|
|0|1|1|0|LR|d8-d*E*|
|0|1|1|1|r*S*-r3, LR|d8-d*E*|
|1|0|0|0|r4-r*N*, r11|žádná|
|1|0|0|1|r*S*-r*N*, r11|žádná|
|1|0|1|0|r11|d8-d*E*|
|1|0|1|1|r*S*-r3, r11|d8-d*E*|
|1|1|0|0|r4-r*N*, r11, LR|žádná|
|1|1|0|1|r*S*-r*N*, r11, LR|žádná|
|1|1|1|0|r11, LR|d8-d*E*|
|1|1|1|1|r*S*-r3, r11, LR|d8-d*E*|

Epilogů slovem kanonické funkce podobné formuláře, ale v opačném pořadí a některé další možnosti. Epilogu mohou být dlouhé až 5 pokyny a jeho formuláře výhradně závisí formu prologu.

|Instrukce|OpCode se předpokládá, že k dispozici pokud:|Velikost|Operační kód|
|-----------------|-----------------------------------|----------|------------|
|6|*Upravit zásobníku*! = 0 a *EF*== 0|16/32|`add   sp,sp,#xx`|
|7|*R*== 1 a *Reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*== 1 nebo (*L*== 1 a *H*== 0) nebo *R*== 0 nebo *EF*== 1|16/32|`pop   {registers}`|
|9a|*H*== 1 a *L*== 0|16|`add   sp,sp,#0x10`|
|9b|*H*== 1 a *L*== 1|32|`ldr   pc,[sp],#0x14`|
|10a|*Staré*== 1|16|`bx    reg`|
|10b|*Staré*== 2|32|`b     address`|

Instrukce 6 je úpravy explicitní zásobníku, pokud je zadáno úpravy se není přeložen. Protože *PF* je nezávislý na *EF*, je možné mít pokyn k dispozici bez instrukce 6 5 nebo naopak.

Pokyny 7 a 8 používají stejnou logikou jako prologu k určení, která registruje se obnoví ze zásobníku, ale s tyto dvě změny: první, *EF* je použito místo *PF*; druhý, pokud *Ret*  = 0, LR nahradí PC v seznamu registr a končí epilogu okamžitě.

Pokud *H* je nastavena, pak instrukce 9a nebo 9b je k dispozici. 9a instrukcí se používá při *L* je 0 označuje, LR není v zásobníku. V takovém případě je ručně upraveno zásobníku a *Ret* musí být 1 nebo 2 zadat explicitní vrátit. 9b instrukcí se používá při *L* 1, k označení předčasné ukončení epilogu a vraťte se a upravit zásobníku ve stejnou dobu.

Pokud epilogu nebyla již byla ukončena, pak buď instrukce 10a nebo 10b je k dispozici, k označení 16bitové nebo 32bitové větev, na základě hodnoty z *Ret*.

### <a name="xdata-records"></a>.xdata Records

Když sbalené unwind formátu není dostatečná k popisu odvíjení funkce, je nutné vytvořit záznam proměnné délky .xdata. Adresa tento záznam je uložen v druhé slovo .pdata záznamu. Formát .xdata je sbalené proměnné délky sadu slov, která má čtyři části:

1. Hlavička 1 nebo 2 slova, která popisuje celkovou velikost struktury .xdata a poskytuje klíčové funkce data. Druhý slovo je k dispozici pouze pokud *epilogu počet* a *slova kódu* obě pole jsou nastaveny na hodnotu 0. Pole se uvádějí v této tabulce:

   |Word|Bity|Účel|
   |----------|----------|-------------|
   |0|0-17|*Funkce délka* je 18 bitové pole, která určuje celková délka funkce v bajtech, děleno 2. Pokud funkce je větší než 512 KB, musí k popisu funkce používá více záznamů .pdata a .xdata. Podrobnosti najdete v části rozsáhlé funkce v tomto dokumentu.|
   |0|18-19|*Ver* je 2 bitové pole, která popisuje verzi zbývající xdata. Pouze verze 0 je aktuálně definován; hodnoty 1-3 jsou vyhrazené.|
   |0|20|*X* je 1bitové pole, která určuje (1) přítomnosti nebo absenci (0) data výjimky.|
   |0|21|*Elektronické* je 1bitové pole, která označuje, že je informace, které popisují jeden epilogu obsahuje záhlaví (1) namísto toho, aby další obor slova novější (0).|
   |0|22|*F* je 1bitové pole, která označuje, že tento záznam popisuje fragment – funkce (1) nebo úplné – funkce (0). Fragment znamená, že neexistuje žádná prologu a zda mají být ignorovány veškeré zpracování v prologu.|
   |0|23-27|*Počet epilogu* je 5 bitové pole, která má dvě význam, v závislosti na stavu *E* bit:<br /><br /> -Pokud *E* je 0, toto pole je počet celkový počet výjimek obory, které je popsáno v oddílu 3. Pokud existuje více než 31 oborů ve funkci a pak toto pole a *slova kódu* pole musí obě být nastaveno na hodnotu 0 označující, že je vyžadována word rozšíření.<br />-Pokud *E* 1, toto pole určuje index první unwind kód, který popisuje pouze epilogu.|
   |0|28-31|*Kód slova* je 4 bitové pole, která určuje počet slov 32-bit musí obsahovat všechny kódy unwind sekce 4. Pokud se více než 15 slova jsou povinné pro více než 63 unwind kód bajtů, toto pole a *epilogu počet* pole musí obě být nastaveno na hodnotu 0 označující, že je vyžadována word rozšíření.|
   |1|0-15|*Rozšířené epilogu počet* je 16 bitů pole, která poskytuje více místa pro kódování neobvykle velký počet epilogů. Slovo rozšíření, která obsahuje toto pole je k dispozici pouze pokud *epilogu počet* a *slova kódu* obě pole v první slovo záhlaví jsou nastaveny na hodnotu 0.|
   |1|16-23|*Rozšířené slova kódu* je 8 bitů pole, která poskytuje více místa pro kódování neobvykle velký počet slov kód unwind. Slovo rozšíření, která obsahuje toto pole je k dispozici pouze pokud *epilogu počet* a *slova kódu* obě pole v první slovo záhlaví jsou nastaveny na hodnotu 0.|
   |1|24-31|Vyhrazeno|

1. Po data výjimky (Pokud *E* bitu v hlavičce byl nastaven na hodnotu 0) je přehled informací o epilogu obory, které jsou zabaleny z nich se má u slov velká a uloženy v pořadí podle zvýšení počáteční posun. Každý obor obsahuje tato pole:

   |Bity|Účel|
   |----------|-------------|
   |0-17|*Posun Start epilogu* je 18 bitové pole, který popisuje posun epilogu v bajtech, děleno 2, vzhledem k začátku funkce.|
   |18-19|*Res* je 2 bitového pole vyhrazené pro budoucí rozšíření. Hodnotou musí být 0.|
   |20-23|*Podmínka* je 4 bitové pole, která poskytuje podmínku, pod kterým je spuštěn epilogu. Nepodmíněný epilogů by měla být nastavena na 0xE, což znamená "always". (Epilogu musí být zcela podmíněný nebo zcela Nepodmíněný a v režimu Thumb-2 epilogu začíná první instrukce po IT operační kód.)|
   |24-31|*Start Index epilogu* je 8 bitů pole, která určuje bajtový index první unwind kódu, který popisuje toto epilogu.|

1. Po vstupu do seznamu oborů epilogu pole bajtů, které obsahují kódy unwind, které jsou podrobně popsány v části kódy Unwind v tomto článku. Toto pole je, aby bylo vytvořeno po uplynutí na nejbližší hranici úplné slovo. Bajty jsou uloženy v pořadí little endian, takže může být přímo načíst v režimu little endian.

1. Pokud *X* pole v záhlaví je 1, kód bajtů unwind následuje informace o výjimce obslužné rutiny. To se skládá z jednoho *RVA obslužné rutiny výjimek* , který obsahuje adresu obslužnou rutinu výjimky, okamžitě následován (proměnné délky) množství dat nutnému obslužnou rutinou výjimky.

Záznam .xdata je navržený tak, aby je možné načíst první 8 bajtů a výpočetní na plnou velikost záznamu, nezahrnuje délka data výjimky proměnlivé velikosti, který následuje. Tento fragment kódu vypočítá velikost záznamu:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = (Xdata[0] >> 23) & 0x1f;
        UnwindWords = (Xdata[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    if (!(Xdata[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

I když prologu a epilogu každý index do kódy unwind, je mezi nimi sdílet v tabulce. Není, že můžou všechny sdílet stejné kódy unwind. Doporučujeme vám, že autorům optimalizovat pro tento případ, protože nejvyšší index, který se dá nastavit je 255 a, který omezí se celkový počet kódy unwind možné pro konkrétní funkci.

### <a name="unwind-codes"></a>Parsovat kódy unwind

Pole kódy unwind je fond instrukce sekvence, které popisují, jak přesně vrátit zpět účinky prologu v pořadí, ve kterém musí být operace vrátit zpět. Kódy unwind jsou mini instrukční sadu, kódovaný jako řetězec bajtů. Po dokončení provádění zpětná adresa pro volání funkce je v registru LR a obnoví všechny stálé registrů se jejich hodnoty v době, kdy byla volána funkce.

Pokud výjimky bylo zaručeno, že dojde k vždy jen v rámci těla funkce, a nikdy v prologu nebo epilogu, pak pouze jeden unwind pořadí bude nezbytné. Model odvíjení Windows ale vyžaduje schopnost vrátit zpět z v rámci částečně prováděnou prologu nebo epilogu. Aby tento požadavek jsou kódy unwind pečlivě navržené pro jednoznačné přímé mapování na každý relevantní operační kód prologu a epilogu. To má vliv na několik:

- Je možné vypočítat délku prologu a epilogu určovat počet kódy unwind. To je možný i s proměnnou délkou pokyny Thumb-2, protože existují různé mapování pro 16bitové a 32bitové operační kódy.

- Podle počtu pokynů po spuštění epilogu oboru, je možné přeskočit ekvivalentní počet kódy unwind a provést zbývající části sekvence dokončit částečně spouštěné unwind fungování epilogu.

- Podle počtu pokynů před koncem prologu, je možné přeskočit ekvivalentní počet kódy unwind a provést zbývající části sekvence vrátit pouze ty části prologu, které se dokončí.

V následující tabulce jsou uvedeny mapování kódy unwind operační kódy. Nejběžnější kódy jsou jenom jeden bajt, zatímco méně běžné těmi, které vyžadují dvě, tři nebo dokonce čtyři bajty. Každý z kódů je uložená v nejvýznamnější bajt nejméně významný bajt. Struktury unwind kód se liší od kódování, je popsáno v ARM EABI, protože tyto kódy unwind jsou navržené tak, aby mapování 1: 1 operační kódy v prologu a epilogu umožňující uvolnění z částečně provedeny prologů a epilogů.

|1 bajt|Bajtů 2|Bajtů 3|Bajtů 4|Opsize|Vysvětlení|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x7F) \* 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> kde LR záznam není vyjmut Pokud kód & 0x2000 a r r0 – 12 jsou odebrány-li odpovídající bit nastaven v 0x1FFF & kódu|
|C0-CF||||16|`mov   sp,rX`<br /><br /> kde X je 0x0F & kódu|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> kde X je (kód & 0x03) + 4 a LR záznam není vyjmut Pokud 0x04 & kódu|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> kde X je (kód & 0x03) + 8 a LR záznam není vyjmut Pokud 0x04 & kódu|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> kde X je (kód & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> kde X je (kód & 0x03FF) \* 4|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> kde LR vyjmut, pokud kód & 0x0100 a r0 – r7 jsou odebrány-li odpovídající bit nastaven v 0x00FF & kódu|
|EE|00-0F|||16|specifické pro společnost Microsoft|
|EE|10-FF|||16|K dispozici|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> kde X je (kód & 0x000F) \* 4|
|EF|10-FF|||32|K dispozici|
|F0-F4||||-|K dispozici|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> Pokud je S (kód & 0x00F0) >> 4 a E je 0x000F & kódu|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> Pokud je S ((Code & 0x00F0) >> 4) + 16 a E je (kód & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFF) \* 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFFFF) \* 4|
|FB||||16|Nop (16 bitů)|
|FC||||32|Nop (32bitová verze)|
|FD||||16|end + 16bitová nop v epilogu|
|FE||||32|end + 32-bit nop v epilogu|
|FF||||-|end|

To ukazuje rozsah šestnáctkové hodnoty pro každý bajt v kód unwind *kód*, spolu s velikostí operační kód *Opsize* a odpovídající původní interpretace instrukce. U prázdných buněk označení kratší kódy unwind. Nejvýznamnější bity pokyny, které mají velké hodnoty, které pokrývají více bajtů, jsou uloženy nejprve. *Opsize* pole zobrazuje velikost implicitní operační kód související s každou operaci Thumb-2. Pozná duplicitní položky v tabulce s jiné kódování se používají k rozlišení mezi operační kód různých velikostí.

Kódy unwind jsou navržené tak, aby první bajt kód říká celková velikost v bajtech kódu a velikost odpovídající operační kód ve službě stream instrukce. Pro výpočet velikosti prologu nebo epilogu podrobné vysvětlení kódy unwind od samého začátku pořadí až do konce a použijte vyhledávací tabulky nebo podobné metody k určení, jak dlouho je odpovídající kód.

Unwind kódy 0xFD a jsou ekvivalentní kód konce regulárního 0xFF, ale účet pro jeden operační kód navíc nop v případě epilogu 16bitové nebo 32bitové 0xFE. Pro prologů jsou přesně odpovídá kódů 0xFD, 0xFE a 0xFF. To účty pro běžné konce epilogu `bx lr` nebo `b <tailcall-target>`, které nemají ekvivalentní prologu instrukce. To zvýší pravděpodobnost, že unwind pořadí je možné sdílet mezi prologu a epilogů.

V mnoha případech by měl být možné použít stejnou sadu kódy unwind prologu a všechny epilogů. Pro zpracování odvíjení částečně prováděnou prologů a epilogů, pravděpodobně však mít více unwind sekvencí kódu, které se liší v řazení nebo chování. To je důvod, proč každý epilogu má svůj vlastní index pro pole unwind a zobrazit, kde spusťte skript.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Odvíjení částečné prologů a epilogů

Nejběžnější odvíjení jsou když dojde k výjimce v těle funkce od prologu a všechny epilogů. V tomto případě unwinder provede kódy unwind začátku pole v indexu 0 a pokračuje, dokud se zjistí operační kód ukončení.

Když dojde k výjimce při prologu nebo epilogu provádí, je pouze částečně vytvořen rámec zásobníku a unwinder musíte určit přesně co bylo provedeno aby bylo možné správně zpět.

Představte si třeba tato sekvence prologu a epilogu:

```asm
0000:   push  {r0-r3}         ; 0x04
0002:   push  {r4-r9, lr}     ; 0xdd
0006:   mov   r7, sp          ; 0xc7
...
0140:   mov   sp, r7          ; 0xc7
0142:   pop   {r4-r9, lr}     ; 0xdd
0146:   add   sp, sp, #16     ; 0x04
0148:   bx    lr
```

Vedle každé operační kód je vhodné unwind kódu k popisu tuto operaci. Sekvence prologu kódy unwind je zrcadlový obraz kódy unwind epilogu, výčtu nebudou započteny poslední instrukce. Tento případ je běžný a z důvodů, proč kódy unwind prologu jsou vždy předpokládá, že mají být uloženy v obráceném pořadí z pořadí zpracování prologu. Tento produkt nám nabízí společnou sadu kódy unwind:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Kód 0xFD je speciální kód na konci sekvenci, která znamená, že epilogu je jedna instrukce 16bitové delší než prologu. To umožňuje větší sdílení kódy unwind.

V příkladu Pokud dojde k výjimce při provádění tělo funkce mezi prologu a epilogu odvíjení začíná epilogu malá a velká, na posunu 0 v rámci Kód epilogu. To odpovídá posun 0x140 v příkladu. Unwinder provede úplnou unwind pořadí, protože se neprovedlo žádné čištění. Pokud místo toho k výjimce dochází jedna instrukce po zahájení Kód epilogu, můžete unwinder úspěšně unwind přeskočením první kód unwind. Zadané mapování 1: 1 mezi operačních kódů a vrátit se zpět kódy, pokud návrat zpět z instrukce *n* v epilogu, přeskočte unwinder první *n* parsovat kódy unwind.

V opačném pořadí pro prologu lze použít podobnou logiku. Návrat zpět z posunu 0 v prologu, nic se má být proveden. Pokud uvolnění z jedné instrukce v pořadí unwind by měl spustit jeden kód unwind od konce, protože prologu unwind kódy jsou uložené v obráceném pořadí. V tomto obecném případě, pokud návrat zpět z instrukce *n* v prologu, uvolnění by měl spustit provedení *n* kódy od konce seznamu kódy unwind.

Prologu a epilogu kódy unwind nejsou vždy přesně shodné. V takovém případě může mít unwind kódu tak, aby obsahovala několik pořadí kódy. Pokud chcete určit posun začala zpracovat kódy, použijte tuto logiku:

1. Pokud návrat zpět z v rámci těla funkce, spusťte skript kódy unwind na pozici 0 a pokračovat, dokud nenastane opcode koncovým.

2. Pokud návrat zpět z v rámci epilogu, pomocí počáteční index epilogu specifické podle oboru, epilogu k dispozici. Vypočítejte, kolik bajtů v počítači je od samého začátku epilogu. Přeskočte dopředu prostřednictvím kódy unwind, dokud všechny už provedli pokyny jsou zahrnuté. Spusťte unwind pořadí spouštění v daném okamžiku.

3. Pokud návrat zpět z v rámci prologu, začněte od indexu 0 v kódy unwind. Vypočítat délku kódu prologu z pořadí a pak vypočítat, kolik bajtů v počítači je od konce prologu. Přeskočte dopředu prostřednictvím kódy unwind, dokud všechny odvolat pokyny jsou zahrnuté. Spusťte unwind pořadí spouštění v daném okamžiku.

Kódy unwind prologu musí být vždy první pole. Navíc se kódy používané k provedení operace unwind v tomto obecném případě odvíjení z v rámci těla. Postupujte podle jakékoli sekvencí kódu epilogu konkrétní ihned po sekvence kódu prologu.

### <a name="function-fragments"></a>Fragmenty – funkce

Optimalizace kódu může být vhodné rozdělit funkce do nesousedících částí. Když to uděláte, každý fragment funkce vyžaduje vlastní samostatný .pdata – a případně .xdata – záznam.

Za předpokladu, že prologu funkce je na začátku funkce a nelze rozdělit, existují čtyři funkce fragment případy:

- Prologu. všechny epilogů v další části.

- Prologu a jeden nebo více epilogů; Další epilogů v další části.

- Žádné prologu nebo epilogů; prologu a jeden nebo více epilogů v další části.

- Epilogů pouze; prologu a případně dalších pokusů epilogů v další části.

V prvním případě musí být popsány pouze prologu. To můžete udělat v podobě compact .pdata, obvykle popisující prologu a určením *Ret* hodnotu 3, která určuje žádné epilogu. Ve formuláři úplné .xdata to můžete udělat jako obvykle poskytují kódy unwind prologu na pozici 0 a určením epilogu počet 0.

Druhou možností je stejně jako normální funkce. Pokud existuje jenom jeden epilogu ve fragmentu, a je na konci fragment, můžete použít záznam compact .pdata. V opačném případě musí být použita záznam úplné .xdata. Mějte na paměti, která posuny zadané pro počáteční epilogu jsou relativní vzhledem k začátku fragment, nikoli původní spuštění funkce.

Třetí a čtvrtý případech jsou variantní hodnoty z prvního a druhého případů, s výjimkou neobsahují prologu. V těchto situacích se předpokládá, že je kód před jeho začátkem epilogu a bude považován za součást tělo funkce, která by obvykle zachytila podle vrácení zpět účinky prologu. Tyto případy proto nutné kódovat s pseudo prologu, který popisuje, jak vrátit zpět z v rámci textu, ale které je považováno za 0-length, při určování, jestli se má provádět částečné vrátit se zpět na začátek fragmentu. Můžete také mohou být označena tento pseudoelement prologu pomocí stejné kódy unwind jako epilogu, protože pravděpodobně provádějí ekvivalentními operacemi.

V případech třetí a čtvrtá přítomnost pseudo prologu zadána buď nastavením *příznak* compact .pdata záznamu na 2, nebo tak, že nastavíte *F* příznak v hlavičce .xdata na hodnotu 1. V obou případech je kontrola pro částečné prologu unwind bude ignorována a všechny jiné epilogu unwinds jsou považovány za úplné.

#### <a name="large-functions"></a>Rozsáhlé funkce

Fragmenty lze použít k popisu funkce, které jsou větší než 512 KB omezení stanovené bitových polí v záhlaví .xdata. K popisu velmi velké funkce, stačí ho rozdělte na fragmenty menší než 512 KB. Každý fragment je třeba upravit tak, aby se rozdělí epilogu není na více částí.

Pouze první fragment funkci obsahuje prologu; Další fragmenty jsou označené jako s žádné prologu. V závislosti na počtu epilogů každý fragment může obsahovat nula nebo více epilogů. Uvědomte si, že každý obor epilogu v fragment Určuje počáteční posun vzhledem k začátku fragment, nikoli začátku funkci.

Pokud fragment žádné prologu a epilogu žádná, i nadále vyžaduje vlastní .pdata – a případně .xdata – záznam, který popisuje, jak vrátit zpět z v rámci těla funkce.

#### <a name="shrink-wrapping"></a>Shrink-wrapping

Je složitější zvláštní případ – funkce fragmenty *shrink-wrapping*, techniku pro odložené register uloží od samého začátku funkce, která se později ve funkci, optimalizace pro jednoduché případy, které nevyžadují uložením registru. To lze popsat jako vnější oblast, která přiděluje místo v zásobníku, ale uloží minimální sadu registrů a vnitřní oblasti, který uloží a obnoví dalších registrů.

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatiles
    sub    sp, sp, #0x100    ; A: allocate all stack space up front
    ...                      ; A:
    add    r0, sp, #0xE4     ; A: prepare to do the inner save
    stm    r0, {r5-r11}      ; A: save remaining non-volatiles
    ...                      ; B:
    add    r0, sp, #0xE4     ; B: prepare to do the inner restore
    ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C:
```

Pečlivě zabaleny funkce obvykle předem přidělte místo pro další registr ukládá pravidelných prologu a pak provést uložení registrů pomocí `str` nebo `stm` místo `push`. Všechny ukazatel zásobníku manipulace se takto zachová v původní prologu funkce.

Pečlivě zabaleny ukázkovou funkci musí dělí na tři oblasti, které jsou označeny jako A, B a C v komentářích. První oblasti pokrývá spuštění funkce až do konce další stálé uloží. K popisu tento fragment tak, že má prologu a žádné epilogů musí být zkonstruovaný záznam .pdata a .xdata.

Střední B oblasti získá svůj vlastní .pdata a .xdata záznam, který popisuje fragment, který nemá žádné prologu a epilogu žádné. Však kódy unwind pro tuto oblast musí být stále k dispozici vzhledem k tomu, že se považuje za těla funkce. Kódy musí popisovat složené prologu, který představuje obou původní registrů uloženo v prologu A oblast a další registry uložit před zadáním oblasti B, jako kdyby byly vytvořeny pomocí jednoho posloupnost operací.

Pro oblast, kterou B nelze považovat jako "vnitřní prologu", protože složené prologu pro oblasti B musí popisovat prologu A oblast a další registry uložit uloží do registru. Pokud fragment B jsou popsány tak, že má prologu, kódy unwind by také implikují velikost tohoto prologu a neexistuje žádný způsob, jak popisují složené prologu tak, aby mapování 1: 1 s operační kódy, které pouze uložit další registry.

Uložení dalších registrů musí považovány za součást této oblasti A, protože dokud nedojde k jejich dokončení, složený prologu přesně nepopisuje stav zásobníku.

Poslední oblast C získá svůj vlastní .pdata a .xdata záznam s popisem, který nemá žádné prologu, ale nemá epilogu fragment.

Alternativním přístupem můžete také použít, když zásobník manipulace provést před zadáním oblasti B může být snížena na jedné instrukce:

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatile registers
    sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
    ...                      ; A:
    push   {r4-r9}           ; A: save remaining non-volatiles
    ...                      ; B:
    pop    {r4-r9}           ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C: restore non-volatile registers
```

Klíč zde je, že na každé hranici instrukce je plně v souladu s kódy unwind pro oblast zásobníku. V případě unwind před vnitřní nasdílení změn v tomto příkladu je považovány za součást této oblasti A a je oddělen pouze oblasti prologu. Pokud dojde k procesu odvíjení po dokončení vnitřní operace push, bude považován, že obsahuje části oblasti B, který nemá žádné prologu, ale má unwind kódy, které popisují vnitřní nasdílení změn a původní prologu z oblasti A. podobnou logiku pro vnitřní pop.

### <a name="encoding-optimizations"></a>Optimalizace kódování

Z důvodu bohatost kódy unwind a možnost využití zkomprimovat a rozšířené formy data jsou řadu příležitostí k optimalizaci kódování, pokud chcete dál snížit místa. Agresivní používání těchto technik může být net režii popisující funkce a fragmenty pomocí kódy unwind poměrně minimální.

Nejdůležitější optimalizace je dejte pozor, abyste zmást prologu/epilogu hranice pro účely odvíjení logické prologu/epilogu hranic z hlediska kompilátoru. Hranice odvíjení můžete zmenšit a provedli užší ke zvýšení efektivity. Například prologu může obsahovat kód po kontroly zásobníku instalační program a provést další ověření. Ale po dokončení všech manipulaci s zásobníku není nutné ke kódování další operace, a nic nad rámec, který je možné odebrat ze odvíjení prologu.

Tato stejná pravidla platí pro funkce délku. Pokud data – například literálu fondu –, který sleduje epilogu ve funkci, neměl by být součástí délka funkce. Zmenšením funkci pouze kód, který je součástí funkce, jsou mnohem větší, že epilogu bude velmi end a compact riziko. je možné záznamu pdata.

V prologu Jakmile ukazatel zásobníku je uložený na jiné registru, není obvykle nutné zaznamenat všechny další operační kódy. K provedení operace unwind funkce, je obnoven uložené registr SP, který se má provést, a tak další operace nemají žádný vliv na unwind.

Jednoinstrukční epilogů nemají být zakódovaný, aby vůbec, buď jako obory nebo jako parsovat kódy unwind. Pokud unwind se provádí před provedením této instrukce, pak ho může být předpokládá se, že z v rámci těla funkce a právě spouští kód prologu unwind je dostačující. Pokud procesu odvíjení, dojde po spuštění jedné instrukce, poté podle definice bude provedeno v jiné oblasti.

Více instrukcí epilogů nemusíte kódovat první instrukce epilogu, ze stejného důvodu jako předchozí bod: Pokud unwind probíhá před provedením této instrukce, stačí úplné prologu unwind. Probíhá-li procesu odvíjení po instrukce, pak pouze následné operace měli považovat za.

Unwind kód by měl být znovu použít agresivní. Index zadaný každý epilogu oboru body na libovolného počáteční bod v poli kódy unwind. Nemá na začátku předchozí pořadí; může odkazovat uprostřed. Nejlepším řešením je generovat pořadí požadovaný kód a potom zkontrolovat shodu přesné bajtů ve fondu už kódováním pořadí a použít všechny skvěle hodí pro opakované použití jako výchozí bod.

Pokud po jednoinstrukční epilogů jsou ignorovány, neexistují žádné zbývající epilogů, zvažte použití compact .pdata formuláře; bude mnohem pravděpodobněji chybí epilogu.

## <a name="examples"></a>Příklady

V těchto příkladech je základní image na 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Příklad 1: Funkce typu list, žádné místní hodnoty

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x000535F8 (= 0x004535F8 0x00400000)

- Word 1

   - *Příznak* = 1, určující canonical formáty prologu a epilogu

   - *Funkce délka* = 0x31 (= 0x62/2)

   - *Staré* = 1, určující návratový 16bitové větve

   - *H* = 0, která parametry nebyly adresami

   - *R*= 0 a *Reg* = 1, určující nabízených oznámení/pop r4 r5

   - *L* = 0 označující žádné LR uložit/obnovit

   - *C* = 0 označující žádné řetězení rámce

   - *Stack – upravit* = 0 označující žádné úpravy zásobníku

### <a name="example-2-nested-function-with-local-allocation"></a>Příklad 2: Vnořená funkce s místní přidělení

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x000533AC (= 0x004533AC-0x00400000)

- Word 1

   - *Příznak* = 1, určující canonical formáty prologu a epilogu

   - *Funkce délka* = 0x35 (= 0x6A/2)

   - *Staré* = 0 označující pop {pc} vrácená

   - *H* = 0, která parametry nebyly adresami

   - *R*= 0 a *Reg* = 3, určující nabízených oznámení/pop r4 r7

   - *L* = 1, LR označující byl uložit/obnovit

   - *C* = 0 označující žádné řetězení rámce

   - *Upravit zásobníku* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Příklad 3: Vnořené Variadické funkce

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x00053988 (= 0x00453988 0x00400000)

- Word 1

   - *Příznak* = 1, určující canonical formáty prologu a epilogu

   - *Funkce délka* = 0x2A (= 0x54/2)

   - *Staré* = 0 označující pop {pc}-stylu return (v tomto případě počítači k omezeně distribuovatelných oprav [sp], #0x14 vrátit)

   - *H* = 1, která parametry byly adresami

   - *R*= 0 a *Reg* = 2, určující nabízených oznámení/pop r4 r6

   - *L* = 1, LR označující byl uložit/obnovit

   - *C* = 0 označující žádné řetězení rámce

   - *Stack – upravit* = 0 označující žádné úpravy zásobníku

### <a name="example-4-function-with-multiple-epilogues"></a>Příklad 4: Funkce s více epilogů

```asm
Prologue:
  004592F4: E92D 47F0 stmdb       sp!, {r4-r10, lr}
  004592F8: B086      sub         sp, sp, #0x18
Epilogues:
  00459316: B006      add         sp, sp, #0x18
  00459318: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  0045943E: B006      add         sp, sp, #0x18
  00459440: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  004595D4: B006      add         sp, sp, #0x18
  004595D6: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459606: B006      add         sp, sp, #0x18
  00459608: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459636: F028 FF0F bl          KeBugCheckEx     ; end of function
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x000592F4 (= 0x004592F4 0x00400000)

- Word 1

   - *Příznak* = 0, která přítomný záznam .xdata (vyžaduje z důvodu více epilogů)

   - *Adresa .xdata* -0x00400000

.xdata (proměnná, 6 slov):

- Word 0

   - *Funkce délka* = 0x0001A3 (= 0x000346/2)

   - *Ver* = 0 označující první verzi xdata

   - *X* = 0 označující žádná data výjimky

   - *Elektronické* = 0 označující seznam oborů epilogu

   - *F* = 0 označující popis plná funkčnost, včetně prologu

   - *Počet epilogu* = 0x04 označující 4 obory celkový epilogu

   - *Kód slova* = 0x01, určující kódy unwind o jedno slovo 32-bit

- Slova 1 – 4, popisující 4 epilogu obory na 4 umístění. Každý obor má společnou sadu kódy unwind dostaly prologu na posunu 0x00 a Nepodmíněný určující podmínku 0x0E (vždy).

- Unwind kódy, počínaje slovo 5: (sdílené mezi prologu/epilogu)

   - Unwind kód 0 = 0x06: sp += (6 << 2)

   - Unwind kód 1 = 0xDE: pop {r4 r10, lr}

   - Unwind kód 2 = 0xFF: ukončení

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Příklad 5: Funkce dynamické zásobníku a vnitřní epilogu

```asm
Prologue:
  00485A20: B40F      push        {r0-r3}
  00485A22: E92D 41F0 stmdb       sp!, {r4-r8, lr}
  00485A26: 466E      mov         r6, sp
  00485A28: 0934      lsrs        r4, r6, #4
  00485A2A: 0124      lsls        r4, r4, #4
  00485A2C: 46A5      mov         sp, r4
  00485A2E: F2AD 2D90 subw        sp, sp, #0x290
Epilogue:
  00485BAC: 46B5      mov         sp, r6
  00485BAE: E8BD 41F0 ldm         sp!, {r4-r8, lr}
  00485BB2: B004      add         sp, sp, #0x10
  00485BB4: 4770      bx          lr
  ...
  00485E2A: F7FF BE7D b           #0x485B28    ; end of function
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x00085A20 (= 0x00485A20 0x00400000)

- Word 1

   - *Příznak* = 0, která přítomný záznam .xdata (třeba z důvodu více epilogů)

   - *Adresa .xdata* -0x00400000

.xdata (proměnná, 3 slova):

- Word 0

   - *Funkce délka* = 0x0001A3 (= 0x000346/2)

   - *Ver* = 0 označující první verzi xdata

   - *X* = 0 označující žádná data výjimky

   - *Elektronické* = 0 označující seznam oborů epilogu

   - *F* = 0 označující popis plná funkčnost, včetně prologu

   - *Počet epilogu* = 0x001 označující 1 oboru celkový epilogu

   - *Kód slova* = 0x01, určující kódy unwind o jedno slovo 32-bit

- Word 1: Obor epilogu posunem 0xC6 (= 0x18C/2), počáteční index kódu unwind 0x00 a s podmínkou 0x0E (vždy)

- Unwind kódy, počínaje slovo 2: (sdílené mezi prologu/epilogu)

   - Unwind kód 0 = 0xC6: sp = r6

   - Unwind kód 1 = 0xDC: pop {r4 r8, lr}

   - Unwind kód 2 = 0x04: sp += (4 << 2)

   - Unwind kódu 3 = 0xFD: nakonec se 16bitové instrukce pro epilogu

### <a name="example-6-function-with-exception-handler"></a>Příklad 6: Funkce s obslužnou rutinou výjimky

```asm
Prologue:
  00488C1C: 0059 A7ED dc.w  0x0059A7ED
  00488C20: 005A 8ED0 dc.w  0x005A8ED0
FunctionStart:
  00488C24: B590      push        {r4, r7, lr}
  00488C26: B085      sub         sp, sp, #0x14
  00488C28: 466F      mov         r7, sp
Epilogue:
  00488C6C: 46BD      mov         sp, r7
  00488C6E: B005      add         sp, sp, #0x14
  00488C70: BD90      pop         {r4, r7, pc}
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x00088C24 (= 0x00488C24 0x00400000)

- Word 1

   - *Příznak* = 0, která přítomný záznam .xdata (třeba z důvodu více epilogů)

   - *Adresa .xdata* -0x00400000

.xdata (proměnná, 5 slov):

- Word 0

   - *Funkce délka* = 0x000027 (= 0x00004E/2)

   - *Ver* = 0 označující první verzi xdata

   - *X* = 1, která data výjimky, které jsou k dispozici

   - *Elektronické* = 1, určující jednu epilogu

   - *F* = 0 označující popis plná funkčnost, včetně prologu

   - *Počet epilogu* = 0x00 označující kódy unwind epilogu začínají znakem posunu 0x00

   - *Kód slova* = 0x02 označující dvě slova 32-bit kódy unwind

- Unwind kódy, počínaje Word 1:

   - Unwind kód 0 = 0xC7: sp = r7

   - Unwind kód 1 = 0x05: sp += (5 << 2).

   - Unwind kód 2 = 0xed bez možnosti odinstalování/0x90: vyvolat přes pop {r4, r7, lr}

   - Unwind kód 4 = 0xFF: ukončení

- Word 3 určuje obslužné rutiny výjimek = 0x0019A7ED (= 0x0059A7ED - 0x00400000)

- Slova 4 a novější se data vložená výjimky

### <a name="example-7-funclet"></a>Příklad 7: Funkce

```asm
Function:
  00488C72: B500      push        {lr}
  00488C74: B081      sub         sp, sp, #4
  00488C76: 3F20      subs        r7, #0x20
  00488C78: F117 0308 adds        r3, r7, #8
  00488C7C: 1D3A      adds        r2, r7, #4
  00488C7E: 1C39      adds        r1, r7, #0
  00488C80: F7FF FFAC bl          target
  00488C84: B001      add         sp, sp, #4
  00488C86: BD00      pop         {pc}
```

.pdata (fixní, 2 slov):

- Word 0

   - *Začátek funkce RVA* = 0x00088C72 (= 0x00488C72 0x00400000)

- Word 1

   - *Příznak* = 1, určující canonical formáty prologu a epilogu

   - *Funkce délka* = 0x0B (= 0x16/2)

   - *Staré* = 0 označující pop {pc} vrácená

   - *H* = 0, která parametry nebyly adresami

   - *R*= 0 a *Reg* = 7, která žádné registry nebyly uložit/obnovit

   - *L* = 1, LR označující byl uložit/obnovit

   - *C* = 0 označující žádné řetězení rámce

   - *Stack – upravit* = 1, která 1 × 4 bajtů zásobníku úpravy

## <a name="see-also"></a>Viz také:

[Přehled konvencí ARM ABI](overview-of-arm-abi-conventions.md)<br/>
[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)
