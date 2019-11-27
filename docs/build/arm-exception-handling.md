---
title: Zpracování výjimek ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: c55baf453c1879f1e0a857cc746bba7802d69f88
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303277"
---
# <a name="arm-exception-handling"></a>Zpracování výjimek ARM

Windows na ARM používá stejný mechanismus strukturovaného zpracování výjimek pro asynchronní výjimky generované hardwarem a synchronní výjimky generované softwarem. Obslužné rutiny výjimek pro konkrétní jazyk jsou postaveny na základě strukturovaného zpracování výjimek ve Windows pomocí pomocných funkcí jazyka. Tento dokument popisuje zpracování výjimek v systému Windows na ARM a jazyky, které používá kód generovaný kompilátorem Microsoft ARM assembler a MSVC.

## <a name="arm-exception-handling"></a>Zpracování výjimek ARM

Windows v ARM používá *unwind kódy* k řízení odvíjení zásobníku během [strukturovaného zpracování výjimek](/windows/win32/debug/structured-exception-handling) (SEH). Unwind kódy jsou posloupnosti bajtů uložených v oddílu. xdata spustitelného obrázku. Popisují operaci prologu a kódu epilogu abstraktním způsobem tak, aby se účinky prologu funkce mohly vrátit zpět v přípravě pro odvinutí na rámec zásobníku volajícího.

Rozhraní EABI ARM (vložené binární rozhraní aplikace) určuje výjimku nelikvidačního modelu, který používá unwind kódy, ale není dostačující pro SEH v systému Windows, které musí zpracovávat asynchronní případy, kdy procesor je uprostřed prologu nebo epilogu funkce Systém Windows také odděluje nelikvidační ovládací prvek na úrovni funkcí a zpětnou působnost oboru pro konkrétní jazyk, což je sjednocení v EABI ARM. Z těchto důvodů Windows na ARM určí další podrobnosti o odvíjení dat a postupu.

### <a name="assumptions"></a>Předpoklady

Spustitelné image pro Windows v ARM používají formát přenositelného spustitelného souboru (PE). Další informace najdete v tématu [specifikace Microsoft PE a COFF](https://go.microsoft.com/fwlink/p/?linkid=84140). Informace o zpracování výjimek jsou uloženy v částech. pdata a. xdata obrázku.

Mechanismus zpracování výjimek provádí určité předpoklady týkající se kódu, který následuje po ABI pro Windows na ARM:

- Pokud dojde k výjimce v těle funkce, nezáleží na tom, zda jsou operace prologu vráceny zpět nebo že operace epilogu jsou prováděny způsobem dopředné. Obě by měly mít stejné výsledky.

- Prologues a epilogues se obvykle rozrážejí. To lze použít ke zmenšení velikosti metadat potřebných k popsání nevinutí.

- Funkce mají být poměrně malé. Několik optimalizací spoléhá na to, že se má efektivně dobalit data.

- Pokud je podmínka umístěna na epilogu, platí stejně pro každou instrukci v epilogu.

- Pokud je ukazatel zásobníku (SP) uložen v jiném registru prologu, musí být tento registr v rámci funkce beze změny, takže původní aktualizace SP může být kdykoli obnovena.

- Pokud se aktualizace SP neuloží v jiném registru, musí se veškerá manipulace s ní provádět výhradně v rámci prologu a epilogu.

- Chcete-li unwind libovolný rámec zásobníku, je nutné tyto operace:

  - Upravte R13 (SP) o 4 bajtových přírůstcích.

  - Odpop jeden nebo více celočíselných registrů.

  - Byl zobrazen jeden nebo více registrů VFP (Virtual floatal-Point).

  - Zkopírujte libovolnou hodnotu registru do R13 (SP).

  - Načtěte SP ze zásobníku pomocí malé operace po odečtení.

  - Analyzujte jeden z několika dobře definovaných typů rámců.

### <a name="pdata-records"></a>Záznamy. pdata

Záznamy. pdata ve formátu PE jsou seřazené pole položek s pevnou délkou, které popisují všechny funkce manipulace s zásobníkem. List Functions, což jsou funkce, které nevolají jiné funkce, nevyžadují záznamy. pdata, když nepracují s zásobníkem. (To znamená, že nevyžadují žádné místní úložiště a nemusejí ukládat ani obnovovat nestálé Registry.) Záznamy pro tyto funkce mohou být vynechány v části. pdata pro uložení místa. Operace unwind z jedné z těchto funkcí může jednoduše zkopírovat zpáteční adresu z registru odkazů (LR) do čítače programu (PC) a přejít tak k volajícímu.

Každý záznam. pdata pro ARM má délku 8 bajtů. Obecný formát záznamu umístí relativní virtuální adresu (RVA) funkce v prvním 32ovém slově následovaný druhým slovem, které obsahuje buď ukazatel na proměnnou length. xdata, nebo zabalené slovo, které popisuje kanonickou funkci. sekvence odvíjení, jak je znázorněno v této tabulce:

|Odsazení slova|Bity|Účel|
|-----------------|----------|-------------|
|0|0-31|*Počáteční adresa RVA funkce* je 32-BITOVÁ adresa RVA začátku funkce. Pokud funkce obsahuje kód miniatury, musí být nastaven nižší bit této adresy.|
|1|0-1|*Příznak* je 2 bitové pole, které určuje, jak interpretovat zbývající 30 bitů druhého. pdata slovo. Pokud je *příznak* 0, zbývající bity vycházejí z *informací o výjimce RVA* (s nízkými dvěma bitymi implicitně 0). Pokud *příznak* není nula, zbývající bity budou mít *sbalenou strukturu unwind dat* .|
|1|2-31|*Informace o výjimce RVA* nebo *zabalená zpětná data*.<br /><br /> *Informace o výjimce RVA* je adresa struktury informací o výjimce s proměnnou délkou, která je uložená v oddílu. xdata. Tato data musí být zarovnané na 4 bajty.<br /><br /> *Zabalená unwind data* jsou komprimovaný popis operací vyžadovaných k unwind z funkce za předpokladu kanonického tvaru. V tomto případě není vyžadován žádný záznam XData.|

### <a name="packed-unwind-data"></a>Zabalená unwind data

Pro funkce, jejichž prologues a epilogues se řídí kanonickým tvarem popsaným níže, lze použít zabalená data unwind. To eliminuje nutnost záznamu. xdata a významně snižuje prostor potřebný k poskytnutí unwind dat. Kanonické prologues a epilogues jsou navržené tak, aby splňovaly společné požadavky jednoduché funkce, která nevyžaduje obslužnou rutinu výjimky, a provádí její nastavení a rozboru operace ve standardním pořadí.

Tato tabulka zobrazuje formát záznamu. pdata, který obsahuje zabalená data unwind:

|Odsazení slova|Bity|Účel|
|-----------------|----------|-------------|
|0|0-31|*Počáteční adresa RVA funkce* je 32-BITOVÁ adresa RVA začátku funkce. Pokud funkce obsahuje kód miniatury, musí být nastaven nižší bit této adresy.|
|1|0-1|*Příznak* je 2 bitové pole s těmito významy:<br /><br />-00 = nepoužívá se zabalená data unwind; zbývající bity nasměrují na záznam. xdata.<br />-01 = zabalená unwind data.<br />-10 = zabalená unwind data, u kterých se předpokládá, že funkce nemá žádný prologu. To je užitečné pro popis fragmentů funkce, které jsou nesouvislé na začátku funkce.<br />-11 = rezervováno.|
|1|2-12|*Délka funkce* je 8bitové pole, které poskytuje délku celé funkce v bajtech dělených 2. Pokud je funkce větší než 4K bajtů, je třeba použít úplný záznam. xdata.|
|1|13-14|*Ret* je 2 bitové pole, které určuje, jak funkce vrací:<br /><br />-00 = návrat přes pop {PC} (v tomto případě musí být v tomto případě nastavený parametr *L* ).<br />-01 = návrat pomocí 16bitové větve.<br />-10 = vrátí se pomocí 32 větve.<br />-11 = žádné epilogu. To je užitečné pro popis nesouvislého fragmentu funkce, který může obsahovat jenom prologu, ale jeho epilogu je jinde.|
|1|15|*H* je 32bitový příznak, který označuje, zda je funkce "domy" registrována jako celočíselný parametr (r0-R3) jejich vložením na začátek funkce a uvolněním 16 bajtů zásobníku před vrácením. (0 = nejedná se o domovské Registry, 1 = obydlí v registru.)|
|1|16-18|*Reg* je 3 bitové pole, které označuje index posledního uloženého nestálého registru. Pokud je bit *R* 0, uloží se pouze celočíselné registry a předpokládá se, že se nachází v rozsahu R4-RN, kde N se rovná 4 + *reg*. Pokud je bit *R* 1, budou uloženy pouze Registry s plovoucí desetinnou čárkou, přičemž se předpokládá, že jsou v rozsahu D8-DN, kde N je rovno 8 + *reg*. Speciální kombinace *R* = 1 a *reg* = 7 označuje, že nejsou uloženy žádné Registry.|
|1|19|*R* je 32bitový příznak, který označuje, zda jsou uložené netěkavé Registry Registry Integer (0) nebo Registry s plovoucí desetinnou čárkou (1). Pokud je jazyk *R* nastaven na hodnotu 1 a pole *reg* je nastaveno na hodnotu 7, nebyly vloženy žádné jiné než nestálé Registry.|
|1|20|*L* je 32bitový příznak, který označuje, zda funkce ukládá nebo obnovuje LR spolu s dalšími Registry uvedenými v poli *reg* . (0 = neukládá ani neobnovuje, 1 = uloží/obnoví.)|
|1|21|*C* je 32bitový příznak, který označuje, zda funkce zahrnuje další pokyny pro nastavení řetězu snímků pro rychlé procházení zásobníku (1) nebo ne (0). Pokud je tento bit nastaven, R11 se implicitně přidá do seznamu uložených celých registrů, které nejsou v registru. (Viz omezení níže, pokud se používá příznak *C* .)|
|1|22-31|*Přizpůsobení zásobníku* je 8bitové pole, které určuje počet bajtů zásobníku, které jsou přiděleny pro tuto funkci a dělenou 4. Pouze hodnoty mezi 0x000-0x3F3 lze však přímo zakódovat. Funkce, které přidělují více než 4044 bajtů zásobníku, musí používat plný záznam. xdata. Pokud je pole pro *úpravu zásobníku* 0x3F4 nebo větší, má dolní 4 bity zvláštní význam:<br /><br />-Bity 0-1 udávají počet slov úpravy zásobníku (1-4) minus 1.<br />-Bit 2 je nastaven na hodnotu 1, pokud prologu zkombinuje tuto úpravu do své nabízené operace.<br />-Bit 3 je nastaven na hodnotu 1, pokud epilogu zkombinuje tuto úpravu do své operace pop.|

V důsledku možné redundance v kódováních platí tato omezení:

- Pokud je příznak *C* nastavený na 1:

   - Příznak *L* musí být také nastaven na hodnotu 1, protože řetězení snímků vyžaduje parametry R11 i LR.

   - R11 nesmí být součástí sady registrů popsaných v souboru *reg*. To znamená, že pokud je příkaz R4-R11 vložen, příkaz *reg* by měl obsahovat pouze popis R4-R10, protože příznak *C* implikuje R11.

- Pokud je pole *ret* nastaveno na hodnotu 0, příznak *L* musí být nastaven na hodnotu 1.

Porušení těchto omezení způsobí nepodporovanou sekvenci.

Pro účely diskuze jsou dva pseudo příznaky odvozeny od *přizpůsobení zásobníku*:

- *PF* nebo "prologu skládání" značí, že *přizpůsobení zásobníku* je 0x3F4 nebo větší a je nastaveno na hodnotu bit 2.

- *EF* nebo "epilogu skládání" značí, že *přizpůsobení zásobníku* je 0x3F4 nebo větší a je nastaven bit 3.

Prologues pro kanonické funkce můžou mít až 5 instrukcí (Všimněte si, že 3a a 3b se vzájemně vylučují):

|Instrukce|Opcode je považována za přítomný v těchto případech:|Velikost|Operačních|Unwind kódy|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*= = 1|16|`push {r0-r3}`|04|
|2|*C*= = 1 nebo *L*= = 1 nebo *R*= = 0 nebo PF = = 1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*= = 1 a (*L*= = 0 a *R*= = 1 a PF = = 0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*= = 1 a (*L*= = 1 nebo *R*= = 0 nebo PF = = 1)|32|`add r11,sp,#xx`|FC|
|4|*R*= = 1 a *reg* ! = 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Úprava zásobníku* ! = 0 a PF = = 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instrukce 1 je vždy přítomna v případě, že je bit *H* nastavený na hodnotu 1.

Chcete-li nastavit řetězení rámců, je k dispozici buď instrukce 3a, nebo 3b, pokud je nastaven bit *jazyka C* . Je to 16bitová `mov`, pokud nejsou vloženy žádné Registry jiné než R11 a LR; v opačném případě je to 32 `add`.

Pokud je zadána nepřeložená úprava, instrukci 5 představuje explicitní úpravu zásobníku.

Pokyny 2 a 4 jsou nastaveny na základě toho, zda je vyžadován požadavek na vložení. Tato tabulka shrnuje, které Registry budou uloženy na základě polí v jazyce *C*, *L*, *R*a *PF* . Ve všech případech se *N* rovná *reg* + 4, *E* se rovná *reg* + 8 a *S* se rovná (~*úpravu zásobníku*) & 3.

|C|L|v|PF|Vložené celočíselné registry|Vložené Registry VFP|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|R4-r*N*|žádná|
|0|0|0|1|r*S*– r*N*|žádná|
|0|0|1|0|žádná|D8-d*E*|
|0|0|1|1|r*S*-R3|D8-d*E*|
|0|1|0|0|R4-r*N*, LR|žádná|
|0|1|0|1|r*S*-r*N*, LR|žádná|
|0|1|1|0|LR|D8-d*E*|
|0|1|1|1|r*S*-R3, LR|D8-d*E*|
|1|0|0|0|R4-r*N*, R11|žádná|
|1|0|0|1|r*S*-r*N*, R11|žádná|
|1|0|1|0|r11|D8-d*E*|
|1|0|1|1|r*S*-R3, R11|D8-d*E*|
|1|1|0|0|R4-r*N*, R11, LR|žádná|
|1|1|0|1|r*S*-r*N*, R11, LR|žádná|
|1|1|1|0|r11, LR|D8-d*E*|
|1|1|1|1|r*S*-R3, R11, LR|D8-d*E*|

Epilogues pro kanonické funkce se řídí podobným formulářem, ale v opačném a s dalšími možnostmi. Epilogu může být dlouhý až 5 instrukcí a jeho forma je striktně nadiktujná formou prologu.

|Instrukce|Opcode je považována za přítomný v těchto případech:|Velikost|Operačních|
|-----------------|-----------------------------------|----------|------------|
|6|*Úprava zásobníku*! = 0 a *EF*= = 0|16/32|`add   sp,sp,#xx`|
|7|*R*= = 1 a *reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*= = 1 nebo (*L*= = 1 a *H*= = 0) nebo *R*= = 0 nebo *EF*= = 1|16/32|`pop   {registers}`|
|9a|*H*= = 1 a *L*= = 0|16|`add   sp,sp,#0x10`|
|9b|*H*= = 1 a *L*= = 1|32|`ldr   pc,[sp],#0x14`|
|10a|*Ret*= = 1|16|`bx    reg`|
|10b|*Ret*= = 2|32|`b     address`|

Instrukce 6 je explicitní úprava zásobníku, pokud je zadána nepřeložená úprava. Vzhledem k tomu, že *PF* je nezávislý na *EF*, je možné, že je k dispozici pokyn 5 bez instrukcí 6 nebo naopak.

Pokyny 7 a 8 používají stejnou logiku jako prologu k určení, které Registry budou obnoveny ze zásobníku, ale s těmito dvěma změnami: první, *EF* se používá místo *BF*; za druhé, pokud je *vrácená* hodnota = 0, pak se LR v seznamu registr nahrazuje řetězcem a epilogu končí okamžitě.

Pokud je nastavená možnost *H* , pak je k dispozici buď pokyn 9a, nebo 9b. K označení, že LR *není v* zásobníku, se používá pokyn 9a. V tomto případě je zásobník manuálně upraven a *ret* musí mít hodnotu 1 nebo 2 pro určení explicitního návratu. Instrukce 9b se používá, když *L* je 1, k indikaci počátečního konce epilogu a k vrácení a úpravě zásobníku ve stejnou dobu.

Pokud se epilogu ještě neukončil, pak je k dispozici buď instrukce 10a, nebo 10b, aby označovala 16bitovou nebo 32ovou větev na základě hodnoty *ret*.

### <a name="xdata-records"></a>.xdata Records

Pokud je zabalený unwind formát nedostatečný pro popis odvíjení funkce, je nutné vytvořit záznam s proměnnou délkou. xdata. Adresa tohoto záznamu je uložena ve druhém slově záznamu. pdata. Formát. xdata je zabalená sada slov s proměnlivou délkou, která má čtyři části:

1. Záhlaví 1 nebo 2 slova, které popisuje celkovou velikost struktury. xdata a poskytuje klíčová data funkce. Druhé slovo je přítomno pouze v případě, že pole *epilogu Count* a *Code* jsou nastavena na hodnotu 0. V této tabulce jsou rozdělená pole:

   |Word|Bity|Účel|
   |----------|----------|-------------|
   |0|0-17|*Délka funkce* je 18 bitové pole, které označuje celkovou délku funkce v bajtech dělenou 2. Je-li funkce větší než 512 KB, je nutné pro popis funkce použít více záznamů. pdata a. xdata. Podrobnosti najdete v části velké funkce v tomto dokumentu.|
   |0|18-19|' 2D *' je 2* bitové pole, které popisuje verzi zbývajícího XData. V tuto chvíli je definovaná jenom verze 0. hodnoty 1-3 jsou vyhrazené.|
   |0|20|*X* je 1 bitové pole, které indikuje přítomnost (1) nebo absence (0) dat výjimky.|
   |0|21|*E* je 1 bitové pole, které indikuje, že informace, které popisují jeden epilogu, se zabalí do hlavičky (1) místo vyžadování dalších slov oboru později (0).|
   |0|22|*F* je 1 bitové pole, které indikuje, že tento záznam popisuje fragment funkce (1) nebo úplnou funkci (0). Fragment znamená, že neexistuje žádný prologu a že všechny zpracování prologu by se měly ignorovat.|
   |0|23-27|*Epilogu Count* je 5 bitové pole, které má dva významy v závislosti na stavu *E* -bitu:<br /><br /> – Pokud je hodnota *E* 0, toto pole je celkový počet oborů výjimek popsaných v části 3. Pokud ve funkci existuje více než 31 oborů, pak musí být toto pole a pole *kódového kódu* nastavené na hodnotu 0, aby bylo indikováno, že je nutné zadat rozšiřující slovo.<br />-Pokud je číslo *E* 1, toto pole určuje index prvního unwind kódu, který popisuje pouze epilogu.|
   |0|28-31|*Kódové slovo* je 4 bitové pole, které určuje počet 32-bitových slov vyžadovaných k zahrnutí všech unwind kódů v oddílu 4. Pokud je vyžadováno více než 15 slov pro více než 63 unwind kódu bajtů, pole a *epilogu Count* musí být obě nastaveny na 0, aby označovaly, že je nutné zadat rozšiřující slovo.|
   |1|0-15|*Rozšířený epilogu počet* je 16bitové pole, které poskytuje více místa pro kódování neobvykle velkého počtu epilogues. Slovo rozšíření, které obsahuje toto pole, je přítomno pouze v případě, že pole *epilogu Count* a *Code* v prvním záhlaví jsou nastavena na hodnotu 0.|
   |1|16-23|*Rozšířená slova kódu* jsou 8bitové pole, které poskytuje více místa pro kódování neobvykle velkého počtu slov unwind kódu. Slovo rozšíření, které obsahuje toto pole, je přítomno pouze v případě, že pole *epilogu Count* a *Code* v prvním záhlaví jsou nastavena na hodnotu 0.|
   |1|24-31|Rezervované|

1. Po datech výjimky (pokud byl bit *E* v hlavičce nastaven na hodnotu 0) je seznam informací o oborech epilogu, které jsou zabaleny do slova a jsou uloženy v pořadí nárůstu počátečního posunu. Každý obor obsahuje tato pole:

   |Bity|Účel|
   |----------|-------------|
   |0-17|*Epilogu počáteční posun* je 18 bitové pole, které popisuje posun epilogu v bajtech dělených 2 vzhledem k začátku funkce.|
   |18-19|*Res* je 2 bitové pole rezervované pro budoucí rozšíření. Jeho hodnota musí být 0.|
   |20-23|*Podmínka* je 4 bitové pole, které poskytuje podmínku, pod kterou je epilogu proveden. Pro nepodmíněné epilogues by měl být nastaven na 0xE, což znamená "Always". (Epilogu musí být zcela podmíněné nebo zcela bezpodmínečné a v režimu palec – 2 začíná epilogu první instrukcí po jejím opcode.)|
   |24-31|*Epilogu Start index* je 8bitové pole, které označuje index bajtů prvního unwind kódu, který popisuje tento epilogu.|

1. Po seznamu rozsahů epilogu je pole bajtů, které obsahují unwind kódy, které jsou podrobně popsány v části unwind kódy v tomto článku. Toto pole je doplněno na konci k nejbližší celé hranici slova. Bajty se ukládají v řádu Little-endian, aby je bylo možné přímo načíst v režimu Little endian.

1. Pokud je pole *X* v hlavičce 1, za bajtem unwind kódu následují informace obslužné rutiny výjimky. To se skládá z jedné adresy *RVA obslužné rutiny výjimek* , která obsahuje adresu obslužné rutiny výjimky následované okamžitou (proměnlivou délkou) množství dat vyžadovaných obslužnou rutinou výjimky.

Záznam. xdata je navržen tak, aby bylo možné načíst prvních 8 bajtů a vypočítat celou velikost záznamu, a to bez zahrnutí délky dat výjimky proměnné velikosti, které následují. Tento fragment kódu vypočítá velikost záznamu:

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

I když prologu a každá epilogu mají index do unwind kódů, je mezi nimi sdílena tabulka. Není neobvyklé, že můžou všechny sdílet stejné kódy unwind. Doporučujeme, aby moduly pro zápis kompilátoru byly pro tento případ optimalizovány, protože největší index, který lze zadat, je 255 a omezuje celkový počet nezpětných kódů, které mohou konkrétní funkce být k dispozici.

### <a name="unwind-codes"></a>Unwind kódy

Pole unwind kódů je fond instrukcí sekvence, který přesně popisuje, jak vrátit zpět účinky prologu, v pořadí, ve kterém je nutné operace vrátit zpět. Unwind kódy jsou mini sada instrukcí, která je zakódována jako řetězec bajtů. Po dokončení spuštění je zpáteční adresa volající funkce v registru LR a všechny nestálé Registry jsou obnoveny do jejich hodnot v době volání funkce.

Pokud byla výjimka zaručena pouze v těle funkce a nikdy v rámci prologu nebo epilogu, pak bude nutná pouze jedna sekvence unwind. Model unwind pro systém Windows však vyžaduje schopnost vrátit se zpět z částečně spouštěného prologu nebo epilogu. Aby bylo možné tento požadavek přizpůsobit, jsou unwind kódy pečlivě navržené tak, aby měly jednoznačně mapování 1:1 na každý relevantní operační kód v prologu a epilogu. To má několik dopadů:

- Je možné vypočítat délku prologu a epilogu, a to tak, že spočítá počet unwind kódů. To je možné i s instrukcemi s proměnlivou délkou na palec, protože existují různá mapování pro 16bitové a 32-bitové operační kódy.

- Vynásobením počtu instrukcí za začátekem oboru epilogu je možné přeskočit ekvivalentní počet unwind kódů a spustit zbytek sekvence a dokončit částečně spouštěné unwind, které prováděla epilogu.

- Napočítáním počtu instrukcí před koncem prologu je možné přeskočit ekvivalentní počet unwind kódů a spustit zbytek sekvence, a vrátit zpět pouze ty části prologu, které dokončily provádění.

Následující tabulka ukazuje mapování z unwind kódů na operační kódy. Nejběžnější kódy jsou pouze jeden bajt, zatímco méně společná vyžadují dvě, tři nebo dokonce čtyři bajty. Každý kód je uložen z nejvýznamnějšího bajtu do nejméně významného bajtu. Struktura unwind kódu se liší od kódování popsaného v EABI ARM, protože tyto unwind kódy jsou navrženy tak, aby měly mapování typu 1:1 na operační kódy v prologu a epilogu, aby bylo možné odvíjení částečně spouštěných prologues a epilogues.

|Bajt 1|Bajt 2|Bajt 3|Bajt 4|Opsize|Vysvětlení|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> kde X je (Code & 0x7F) \* 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> kde LR je odebráno, pokud kód & 0x2000 a r0-R12 jsou odebrány, pokud je odpovídající bit nastaven v kódu & 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> kde X je kód & 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> kde X je (Code & 0x03) + 4 a LR je vyjmuta, pokud kód & 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> kde X je (Code & 0x03) + 8 a LR je vyjmuta, pokud kód & 0x04|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> kde X je (Code & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> kde X je (Code & 0x03FF) \* 4|
|ES – ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> kde LR je odebráno, pokud je kód & 0x0100 a r0-R7 odebrány, pokud je odpovídající bit nastaven v kódu & 0x00FF|
|EE|00-0F|||16|specifické pro společnost Microsoft|
|EE|10-FF|||16|K dispozici|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> kde X je (Code & 0x000F) \* 4|
|EF|10-FF|||32|K dispozici|
|F0-F4||||-|K dispozici|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> kde S je (Code & 0x00F0) > > 4 a E je Code & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> kde S je ((Code & 0x00F0) > > 4) + 16 a E je (Code & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> kde X je (Code & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> kde X je (Code & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> kde X je (Code & 0x00FFFF) \* 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> kde X je (Code & 0x00FFFFFF) \* 4|
|FB||||16|NOP (16 bitů)|
|FC||||32|NOP (32 bitů)|
|FD||||16|end + 16. bit NOP v epilogu|
|FE||||32|konec + 32 – bit NOP v epilogu|
|FF||||-|end|

Tím se zobrazuje rozsah hexadecimálních hodnot pro každý bajt v *kódu*unwind kódu, spolu s velikostí operačního systému *Opsize* a odpovídajícím způsobem interpretace instrukcí. Prázdné buňky označují kratší kódy unwind. V pokynech, které mají velké hodnoty pokrývající více bajtů, jsou nejprve uloženy nejvýznamnější bity. Pole *Opsize* zobrazuje implicitní velikost operačního kódu spojenou s každou operací palec-2. Zjevné duplicitní položky v tabulce s různými kódováními slouží k rozlišení mezi různými velikostmi operačního kódu.

Unwind kódy jsou navržené tak, že první bajt kódu oznamuje celkovou velikost v bajtech kódu a velikost odpovídajícího operačního kódu v datovém proudu instrukcí. Chcete-li vypočítat velikost prologu nebo epilogu, Projděte si unwind kódy od začátku sekvence až do konce a použijte vyhledávací tabulku nebo podobnou metodu k určení, jak dlouho je odpovídající operační kód.

Unwind kódy 0xFD a 0xFE jsou ekvivalentní regulárnímu kódu 0xFF, ale účet pro jeden další nop opcode v případě epilogu, buď 16 bitů nebo 32-bit. Pro prologues jsou kódy 0xFD, 0xFE a 0xFF přesně ekvivalentní. Tyto účty pro běžné epilogu končí `bx lr` nebo `b <tailcall-target>`, které nemají ekvivalentní instrukci prologu. Tím se zvyšuje pravděpodobnost, že lze odvinout sekvence sdílet mezi prologu a epilogues.

V mnoha případech by mělo být možné použít stejnou sadu unwind kódů pro prologu a všechny epilogues. Pro zpracování nevinutí částečně spuštěných prologues a epilogues však může být nutné mít více sekvencí unwind kódu, které se liší v pořadí nebo chování. To je důvod, proč každý epilogu má svůj vlastní index do pole unwind k zobrazení, kde začít provádět.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Odvíjení částečných Prologues a Epilogues

Nejběžnější případ unwind je výjimka, pokud dojde k výjimce v těle funkce, od prologu a všech epilogues. V tomto případě provede unwind kódy v poli unwind, které začíná na indexu 0 a pokračuje, dokud není detekována koncová instrukce.

V případě, že dojde k výjimce při provádění prologu nebo epilogu, je rámec zásobníku vytvořen pouze částečně a unwinda musí přesně určit, co bylo provedeno, aby bylo možné jej správně vrátit.

Zvažte například tuto prologu a epilogu sekvenci:

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

Pro popis této operace je u každého operačního kódu odpovídající unwind kód. Sekvence unwind kódů pro prologu je zrcadlovým obrázkem unwind kódu pro epilogu, nikoli za poslední instrukcí. V tomto případě je to běžné a je důvod, že unwind kódy pro prologu se vždy považují za uložené v opačném pořadí od pořadí provádění prologu. Díky tomu máme společnou sadu unwind kódů:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Kód 0xFD je speciální kód pro konec sekvence, který znamená, že epilogu je 1 16-bit instrukcí déle než prologu. Díky tomu je možné větší sdílení kódů unwind.

V příkladu, pokud dojde k výjimce, když je prováděno tělo funkce mezi prologu a epilogu, začíná odvíjení epilogu případ, na posun 0 v kódu epilogu. To odpovídá posunu 0x140 v příkladu. Unwind spustí úplnou sekvenci unwind, protože nebylo provedeno žádné vyčištění. Pokud místo toho dojde k výjimce o jednu instrukci za počátkem epilogu kódu, může být unwinda úspěšně unwind vynecháním prvního unwind kódu. Pro mapování 1:1 mezi operačními kódy a unwind kódy, pokud je unwind z instrukce *n* v epilogu, by neměl přeskočit prvních *n* unwind kódů.

Podobná logika funguje v opačném případě pro prologu. Pokud se unwinda z posunu 0 v prologu, nic se neprovede. Pokud se odvíjí od jednoho pokynu v nástroji, by měla sekvence unwind začít jeden unwind kód od konce, protože prologu unwind kódy jsou uloženy v opačném pořadí. Pokud se v obecném případě odvíjí od instrukcí *n* v prologu, by se mělo začít spouštět v *n* unwind kódech na konci seznamu kódů.

Prologu a epilogu unwind kódy se vždy přesně neshodují. V takovém případě může být pole unwind kódu obsahovat několik sekvencí kódů. K určení posunu pro zahájení zpracování kódů použijte tuto logiku:

1. Pokud se odvíjí od těla funkce, zahajte spouštění unwind kódu na indexu 0 a pokračujte, dokud nedosáhnete koncového opcode.

2. Při unwindi v rámci epilogu použijte počáteční index specifický pro epilogu poskytnutý oborem epilogu. Vypočítá počet bajtů, které počítač začíná na začátku epilogu. Přeskočí vpřed kódů unwind, dokud nejsou všechny již spouštěné instrukce pro. Spustí unwind sekvenci začínající v daném okamžiku.

3. Pokud se odvíjí v rámci prologu, začněte od indexu 0 v unwind kódu. Vypočítá délku prologu kódu z sekvence a pak vypočítá, kolik bajtů má počítač ze konce prologu. Přeskočit vpřed kódů unwind až do všech nespuštěných pokynů pro. Spustí unwind sekvenci začínající v daném okamžiku.

Unwind kódy pro prologu musí být vždy první v poli. Jsou to také kódy používané k odvíjení v obecném případě odvíjení v těle. Jakékoli sekvence kódu specifické pro epilogu by měly následovat hned po sekvenci kódu prologu.

### <a name="function-fragments"></a>Fragmenty funkcí

Pro optimalizaci kódu může být užitečné rozdělit funkci na nesouvislé části. V případě, že je to hotové, bude každý fragment funkce vyžadovat vlastní samostatný. pdata – a případně. xdata – záznam.

Za předpokladu, že funkce prologu je na začátku funkce a nedá se rozdělit, existují čtyři případy fragmentů funkcí:

- Pouze prologu; všechny epilogues v dalších fragmentech.

- Prologu a jeden nebo více epilogues; Další epilogues v dalších fragmentech.

- Žádné prologu ani epilogues; prologu a jeden nebo více epilogues v jiných fragmentech.

- Pouze Epilogues; prologu a případně další epilogues v dalších fragmentech.

V prvním případě musí být popsána pouze prologu. To se dá udělat ve formuláři Compact. pdata tak, že se prologu normálně a určíte hodnotu *ret* 3, která značí, že se epilogu. V úplném formuláři. xdata lze to provést tak, že zadáte prologu unwind kódy na index 0 jako obvykle a určíte počet epilogu 0.

Druhý případ je stejný jako normální funkce. Pokud je v fragmentu pouze jeden epilogu a je na konci fragmentu, lze použít záznam Compact. pdata. V opačném případě je nutné použít úplný záznam. xdata. Mějte na paměti, že posuny zadané pro epilogu Start jsou relativní vzhledem k začátku fragmentu, ne původnímu začátku funkce.

Třetí a čtvrtý případ jsou varianty prvního a druhého případu s tím rozdílem, že neobsahují prologu. V těchto situacích se předpokládá, že existuje kód před začátkem epilogu a je považován za součást těla funkce, což by bylo normálně oddělit vrácením efektů prologu. Tyto případy musí být proto kódovány pomocí pseudo-prologu, která popisuje, jak zpětně převinout z těla, ale je považována za 0-Length při určování, zda provést částečný unwind na začátku fragmentu. Alternativně může být tento pseudo-prologu popsán pomocí stejných unwind kódů jako epilogu, protože se předpokládá, že provádějí ekvivalentní operace.

Ve třetím a čtvrtém případě je přítomnost pseudo-prologu zadána buď nastavením pole *příznak* v záznamu Compact. pdata na hodnotu 2, nebo nastavením příznaku *F* v hlavičce. xdata na hodnotu 1. V obou případech se kontrolu částečného prologu unwind ignoruje a všechny neepilogué unwind se považují za úplné.

#### <a name="large-functions"></a>Velké funkce

Fragmenty lze použít k popisu funkcí větších, než je limit 512 KB, který je určen bitovými poli v hlavičce. xdata. Chcete-li popsat velmi velkou funkci, stačí ji rozdělit na fragmenty menší než 512 KB. Jednotlivé fragmenty by měly být upraveny tak, aby epilogu nerozdělit na více částí.

Pouze první fragment funkce obsahuje prologu; všechny ostatní fragmenty jsou označené jako žádné prologu. V závislosti na počtu epilogues mohou jednotlivé fragmenty obsahovat nula nebo více epilogues. Mějte na paměti, že každý obor epilogu v fragmentu Určuje počáteční posun vzhledem k začátku fragmentu, ne na začátku funkce.

Pokud fragment neobsahuje žádné prologu a žádné epilogu, bude stále vyžadovat vlastní. pdata – a případně. xdata – záznam, který popisuje, jak se vrátit zpět v těle funkce.

#### <a name="shrink-wrapping"></a>Zmenšit – zabalení

Složitější zvláštní případ fragmentů funkcí je *sbalení zúžení*, technika pro odložení zápisu ze začátku funkce do pozdější funkce, pro optimalizaci pro jednoduché případy, které nevyžadují uložení registru. To lze popsat jako vnější oblast, která přiděluje prostor zásobníku, ale ukládá minimální sadu registrů, a vnitřní oblast, která ukládá a obnovuje další registry.

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

Funkce zabalené v rámci zúžení obvykle mají za následek předem přidělit prostor pro nadbytečné Registry v normálním prologu a poté provést příkaz Register pro uložení pomocí `str` nebo `stm` namísto `push`. Tím se zachová všechna manipulace s ukazateli na zásobníku v původní prologu funkce.

Ukázková funkce zmenšení se musí rozdělit do tří oblastí, které jsou v komentářích označeny jako A, B a C. První oblast pokrývá začátek funkce na konci dalších nestálých uložení. Aby se tento fragment popsal jako prologu a No epilogues, musí být vytvořený záznam. pdata nebo. xdata.

Oblast uprostřed B získá svůj vlastní záznam. pdata nebo. xdata, který popisuje fragment, který nemá žádné prologu a epilogu. Nicméně kódy unwind pro tuto oblast musí být stále k dispozici, protože se považují za tělo funkce. Kódy musí popsat složený prologu, který představuje původní Registry uložené v oblasti-A prologu a další registry uložené před vstupem do oblasti B, jako kdyby byly vyráběny pomocí jedné sekvence operací.

Zápisy registru pro oblast B nelze považovat za "vnitřní prologu", protože složené prologu popsané pro oblast B musí popsat jak region, tak prologu a další uložené registry. Pokud byly fragmenty B popsané jako prologu, unwind kódy by také znamenaly velikost tohoto prologu a neexistuje žádný způsob, jak popsat složený prologu způsobem, který mapuje 1:1 pomocí operačních kódů, které ukládají pouze další registry.

Další zápisy v registru se musí považovat za součást oblasti A, protože až do jejich dokončení, složené prologuy přesně popisují stav zásobníku.

Poslední oblast jazyka C získá svůj vlastní záznam. pdata nebo. xdata, který popisuje fragment, který nemá žádné prologu, ale má epilogu.

Alternativní přístup může fungovat i v případě, že před vstupem oblasti B se dá provést manipulace s jednou instrukcí:

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

Tady je klíč, který je v každé z hranic instrukcí, zásobník je plně v souladu s kódy unwind pro oblast. Pokud k unwind dojde před vnitřním vložením v tomto příkladu, je považován za součást oblasti A a pouze oblast A prologu je zrušeno. Pokud k unwind dojde po vnitřní nabídce push, je považována za součást oblasti B, která nemá žádné prologu, ale obsahuje unwind kódy, které popisují vnitřní navýšení a původní prologu z oblasti A. podobná logice uchovává vnitřní bod POP.

### <a name="encoding-optimizations"></a>Optimalizace kódování

Z důvodu bohatosti unwind kódů a schopnosti využít kompaktní a rozšířené formy dat existuje mnoho příležitostí k optimalizaci kódování pro další snížení místa. Díky agresivnímu používání těchto technik může být netto režie popisující funkce a fragmenty pomocí unwind kódů poměrně minimální.

Nejdůležitější optimalizace je dbát, aby nepleťte hranice prologu/epilogu pro účely odvíjení logických prologuů a epilogu z perspektivy kompilátoru. Aby se zlepšila efektivita, je možné hranice odvíjení zmenšit a vytvořit těsnější. Například prologu může obsahovat kód poté, co nastavení zásobníku provede další kontroly ověřování. Ale po dokončení veškeré manipulace s zásobníkem není nutné zakódovat další operace a cokoli nad tím, co je možné odebrat z unwindho prologuu.

Toto pravidlo se vztahuje na délku funkce. Pokud jsou k dispozici data – například fond literálů, který následuje epilogu ve funkci, neměl by být součástí délky funkce. Zmenšením funkce na pouze kód, který je součástí funkce, je pravděpodobnost mnohem větší, než epilogu bude na konci a komprimaci. záznam PDATA lze použít.

Jakmile je ukazatel zásobníku uložen v prologu do jiného registru, obvykle není nutné nahrávat žádné další operační kódy. Aby bylo možné funkci vrátit zpět, první věc, kterou je třeba provést, je obnovit aktualizaci SP z uloženého registru, takže další operace nemají žádný vliv na unwind.

Epilogues s jednou instrukcí není nutné vůbec kódovat, a to buď jako obory, nebo jako unwind kódy. Pokud dojde k unwind před provedením této instrukce, lze předpokládat, že je v těle funkce, a stačí pouze spustit prologu kódy unwind. Pokud dojde k odvíjení po provedení jedné instrukce, pak podle definice proběhne v jiné oblasti.

Epilogues s více instrukcemi nemusí zakódovat první instrukci epilogu, ze stejného důvodu jako předchozí bod: Pokud se unwind provede před spuštěním této instrukce, bude stačit kompletní prologu unwind. Pokud dojde k převinutí po této instrukci, je nutné vzít v úvahu pouze následné operace.

Opakované použití unwind kódu by mělo být agresivní. Index zadaný každým oborem epilogu odkazuje na libovolný výchozí bod v poli unwind kódů. Není nutné nasměrovat na začátek předchozí sekvence; může ukázat uprostřed. Nejlepším způsobem je vygenerovat požadovanou sekvenci kódu a pak vyhledat přesnou shodu bajtů v již kódovaném fondu sekvencí a použít jakoukoli dokonalou shodu jako výchozí bod pro opakované použití.

Pokud se po ignorování epilogues s jednou instrukcí žádné zbývající epilogues, zvažte použití formátu Compact. pdata; může to být mnohem pravděpodobnější, že nebudete mít k dispozici epilogu.

## <a name="examples"></a>Příklady

V těchto příkladech je základ obrázku na adrese 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Příklad 1: funkce listu bez místních hodnot

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x000535F8 (= 0x004535F8-0x00400000)

- Word 1

   - *Příznak* = 1, který označuje kanonické formáty prologu a epilogu

   - *Funkce Length* = 0x31 (= 0x62/2)

   - *Ret* = 1, což značí 16bitovou návratovou větev.

   - *H* = 0, což značí, že se parametry nepřesunuly domů

   - *R*= 0 a *reg* = 1, označující vložení/pop z R4-R5

   - *L* = 0, což znamená, že nelze uložit/obnovit LR

   - *C* = 0, což značí, že žádné řetězení snímků

   - *Úprava zásobníku* = 0, což značí neúpravu zásobníku

### <a name="example-2-nested-function-with-local-allocation"></a>Příklad 2: vnořená funkce s místním přidělením

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x000533AC (= 0x004533AC-0x00400000)

- Word 1

   - *Příznak* = 1, který označuje kanonické formáty prologu a epilogu

   - *Funkce Length* = 0x35 (= 0x6A/2)

   - *Ret* = 0, což značí, že se vrátí pop {PC}

   - *H* = 0, což značí, že se parametry nepřesunuly domů

   - *R*= 0 a *reg* = 3, indikující vložení/pop z R4 – R7

   - *L* = 1, určující, že LR byl uložen nebo obnoven

   - *C* = 0, což značí, že žádné řetězení snímků

   - *Úprava zásobníku* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Příklad 3: vnořená funkce variadické

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x00053988 (= 0x00453988-0x00400000)

- Word 1

   - *Příznak* = 1, který označuje kanonické formáty prologu a epilogu

   - *Funkce Length* = 0x2a (= 0x54/2)

   - *Ret* = 0, což značí, že se vrátí pop (v tomto případě počítač LDR, [SP], #0x14 návrat)

   - *H* = 1, označující, že parametry byly domovské

   - *R*= 0 a *reg* = 2, indikující vložení/pop z R4-R6

   - *L* = 1, určující, že LR byl uložen nebo obnoven

   - *C* = 0, což značí, že žádné řetězení snímků

   - *Úprava zásobníku* = 0, což značí neúpravu zásobníku

### <a name="example-4-function-with-multiple-epilogues"></a>Příklad 4: funkce s více Epilogues

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

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x000592F4 (= 0x004592F4-0x00400000)

- Word 1

   - *Příznak* = 0, který značí, že je přítomný záznam XData (vyžaduje se v důsledku více epilogues)

   - *adresa. xdata* – 0x00400000

. xdata (proměnná, 6 slov):

- Word 0

   - *Funkce Length* = 0x0001A3 (= 0x000346/2)

   - *Průřez* = 0, který označuje první verzi XData

   - *X* = 0, což značí, že žádná data výjimky

   - *E* = 0, který označuje seznam oborů epilogu

   - *F* = 0, indikuje úplný popis funkce, včetně prologu

   - *Epilogu Count* = 0x04, což značí 4 obory celkem epilogu

   - *Kódová slova* = 0x01, což značí 1 32.-bit unwind kódů

- Slova 1-4, popisující 4 epilogu obory ve 4 umístěních. Každý obor má společnou sadu unwind kódů, které jsou sdíleny s prologu, na posunu 0x00 a je nepodmíněný, určením podmínky 0x0E (Always).

- Unwind kódy začínající na slovu 5: (Shared Between prologu/epilogu)

   - Unwind kód 0 = 0x06: SP + = (6 < < 2)

   - Unwind kód 1 = 0xDE: pop {R4-R10, LR}

   - Unwind kód 2 = 0xFF: end

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Příklad 5: funkce s dynamickým zásobníkem a vnitřním epilogu

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

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x00085A20 (= 0x00485A20-0x00400000)

- Word 1

   - *Příznak* = 0, který značí, že je přítomný záznam XData (vyžaduje se v důsledku více epilogues)

   - *adresa. xdata* – 0x00400000

. xdata (proměnná; 3 slova):

- Word 0

   - *Funkce Length* = 0x0001A3 (= 0x000346/2)

   - *Průřez* = 0, který označuje první verzi XData

   - *X* = 0, což značí, že žádná data výjimky

   - *E* = 0, který označuje seznam oborů epilogu

   - *F* = 0, indikuje úplný popis funkce, včetně prologu

   - *Epilogu Count* = 0x001, což značí 1 celkový rozsah epilogu

   - *Kódová slova* = 0x01, což značí 1 32.-bit unwind kódů

- Word 1: epilogu rozsah na posunu 0xC6 (= 0x18C/2), spuštění indexu unwind kódu v hodnotě 0x00 a podmínka 0x0E (Always)

- Unwind kódy začínající na slovo 2: (Shared Between prologu/epilogu)

   - Unwind kód 0 = 0xC6: SP = R6

   - Unwind kód 1 = 0xDC: pop {R4-R8, LR}

   - Unwind kód 2 = 0x04: SP + = (4 < < 2)

   - Unwind kód 3 = 0xFD: end, počítá se jako 16bitové instrukce pro epilogu.

### <a name="example-6-function-with-exception-handler"></a>Příklad 6: funkce s obslužnou rutinou výjimky

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

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x00088C24 (= 0x00488C24-0x00400000)

- Word 1

   - *Příznak* = 0, který značí, že je přítomný záznam XData (vyžaduje se v důsledku více epilogues)

   - *adresa. xdata* – 0x00400000

. xdata (proměnná, 5 slov):

- Word 0

   - *Funkce Length* = 0x000027 (= 0x00004E/2)

   - *Průřez* = 0, který označuje první verzi XData

   - *X* = 1, což znamená, že jsou přítomna data výjimky

   - *E* = 1, označující jeden epilogu

   - *F* = 0, indikuje úplný popis funkce, včetně prologu

   - *Epilogu Count* = 0x00, což značí, že epilogu kódy unwind začínají na posunu 0x00

   - *Kódová slova* = 0x02, která značí 2 32 – bitová slova unwind kódů

- Unwind kódy začínající na slovo 1:

   - Unwind kód 0 = 0xC7: SP = R7

   - Unwind kód 1 = 0x05: SP + = (5 < < 2)

   - Unwind kód 2 = 0xED/0x90: pop {R4, R7, LR}

   - Unwind kód 4 = 0xFF: end

- Word 3 určuje obslužnou rutinu výjimky = 0x0019A7ED (= 0x0059A7ED-0x00400000).

- Slova 4 a novější jsou vložená data výjimky.

### <a name="example-7-funclet"></a>Příklad 7: funkce

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

. pdata (pevná, 2 slova):

- Word 0

   - *Funkce Start RVA* = 0x00088C72 (= 0x00488C72-0x00400000)

- Word 1

   - *Příznak* = 1, který označuje kanonické formáty prologu a epilogu

   - *Funkce Length* = 0x0B (= 0x16/2)

   - *Ret* = 0, což značí, že se vrátí pop {PC}

   - *H* = 0, což značí, že se parametry nepřesunuly domů

   - *R*= 0 a *reg* = 7, což značí, že nebyly uloženy nebo obnoveny žádné Registry

   - *L* = 1, určující, že LR byl uložen nebo obnoven

   - *C* = 0, což značí, že žádné řetězení snímků

   - *Úprava zásobníku* = 1, což značí 1 × 4 bajty nastavení zásobníku

## <a name="see-also"></a>Viz také:

[Přehled konvencí ARM ABI](overview-of-arm-abi-conventions.md)<br/>
[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)
