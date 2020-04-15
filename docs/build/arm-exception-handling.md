---
title: Zpracování výjimek ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: 4bdf0c88f0c2fe445f3a8865353ca1259ba586fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323228"
---
# <a name="arm-exception-handling"></a>Zpracování výjimek ARM

Systém Windows na ARM používá stejný mechanismus zpracování strukturovaných výjimek pro asynchronní výjimky generované hardwarem a synchronní výjimky generované softwarem. Obslužné rutiny výjimek specifické pro jazyk jsou postaveny na nad windows strukturované zpracování výjimek pomocí funkce jazykového pomocníka. Tento dokument popisuje zpracování výjimek v systému Windows na ARM a pomocné jazyky používané kódem, který je generován assemblerem Microsoft ARM a kompilátorem MSVC.

## <a name="arm-exception-handling"></a>Zpracování výjimek ARM

Windows na ARM používá *unwind kódy* pro řízení odvíjení zásobníku během [zpracování strukturovaných výjimek](/windows/win32/debug/structured-exception-handling) (SEH). Unwind kódy jsou posloupnost bajtů uložených v části .xdata spustitelného obrazu. Popisují operaci prologu funkce a epilogu kódu abstraktním způsobem, takže účinky prologu funkce lze vrátit zpět v rámci přípravy na odvíjení do rámce zásobníku volajícího.

ARM EABI (vložené binární rozhraní aplikace) určuje model odvíjení výjimky, který používá unwind kódy, ale není dostačující pro UNWinding v systému Windows, který musí zpracovat asynchronní případy, kdy je procesor uprostřed prologu nebo epilogu funkce. Systém Windows také odděluje odvíjení ovládacího prvku do odvíjení na úrovni funkce a odvíjení oboru specifické pro jazyk, který je sjednocen v ARM EABI. Z těchto důvodů windows na ARM určuje další podrobnosti pro odvíjení dat a postup.

### <a name="assumptions"></a>Předpoklady

Spustitelné bitové kopie pro systém Windows v arm používají formát Portable Spustitelný soubor (PE). Další informace naleznete v [tématech Microsoft PE a COFF Specification](https://go.microsoft.com/fwlink/p/?linkid=84140). Informace o zpracování výjimek jsou uloženy v oddílech .pdata a .xdata v bitové kopii.

Mechanismus zpracování výjimek provádí určité předpoklady o kódu, který následuje Za ABI pro Windows na ARM:

- Pokud dojde k výjimce v těle funkce, nezáleží na tom, zda jsou operace prologu zpět, nebo operace epilogu jsou prováděny dopředu. Oba by měly přinést stejné výsledky.

- Prology a epilogy mají tendenci zrcadlit navzájem. To lze použít ke zmenšení velikosti metadat potřebných k popisu unwinding.

- Funkce mají tendenci být relativně malé. Několik optimalizace spoléhat na to pro efektivní balení dat.

- Pokud je podmínka umístěna na epilogu, platí stejně pro každou instrukci v epilogu.

- Pokud je ukazatel zásobníku (SP) uložen v jiném registru v prologu, tento registr musí zůstat nezměněn v celé funkci, aby původní SP může být kdykoli obnovena.

- Pokud sp je uložen v jiném registru, všechny manipulace s ním musí dojít výhradně v rámci prologu a epilogu.

- Chcete-li uvolnit libovolný rámec zásobníku, jsou vyžadovány tyto operace:

  - Upravte r13 (SP) v krocích po 4 bajtů.

  - Pop jeden nebo více celé číslo registru.

  - Pop jeden nebo více vfp (virtuální plovoucí-bod) registry.

  - Zkopírujte libovolnou hodnotu registru do hodnoty r13 (SP).

  - Načtěte SP ze zásobníku pomocí operace malé po snížení.

  - Analyzujte jeden z několika dobře definovaných typů rámců.

### <a name="pdata-records"></a>Záznamy .pdata

Záznamy .pdata v obraze ve formátu PE jsou uspořádané pole položek s pevnou délkou, které popisují každou funkci manipulace s zásobníkem. Funkce List, což jsou funkce, které nevolají jiné funkce, nevyžadují záznamy .pdata, když nemanipulují s zásobníkem. (To znamená, že nevyžadují žádné místní úložiště a není nutné ukládat nebo obnovovat nevolatilní registry.). Záznamy pro tyto funkce lze vynechat z oddílu .pdata pro úsporu místa. Operace unwind z jedné z těchto funkcí stačí zkopírovat zpáteční adresu z registru odkazů (LR) do čítače programu (PC) a přesunout se k volajícímu.

Každý záznam .pdata pro ARM je 8 bajtů dlouhý. Obecný formát záznamu umístí relativní virtuální adresu (RVA) funkce začínat v první 32bitové slovo, následuje druhé slovo, které obsahuje buď ukazatel na proměnnou délku .xdata bloku nebo balené slovo, které popisuje kanonické funkce odvíjení sekvence, jak je znázorněno v této tabulce:

|Posun aplikace Word|Bity|Účel|
|-----------------|----------|-------------|
|0|0-31|*Funkce Start RVA* je 32bitové RVA na začátku funkce. Pokud funkce obsahuje kód palce, musí být nastaven nízký bit této adresy.|
|1|0-1|*Příznak* je 2bitové pole, které označuje, jak interpretovat zbývajících 30 bitů druhého slova .pdata. Pokud *Flag* je 0, pak zbývající bity tvoří *výjimku informace RVA* (s nízké dva bity implicitně 0). Pokud *Flag* je nenulová, pak zbývající bity tvoří *packed unwind data* struktury.|
|1|2-31|*Informace o výjimce RVA* nebo *zabalená data unwind*.<br /><br /> *RVA informace o výjimce* je adresa informační struktury výjimek proměnné délky, která je uložena v části .xdata. Tato data musí být zarovnána se 4 bajty.<br /><br /> *Packed Unwind Data* je komprimovaný popis operací potřebných k uvolnění z funkce za předpokladu kanonické ho formuláře. V tomto případě není vyžadován žádný záznam .xdata.|

### <a name="packed-unwind-data"></a>Zabalená data unwind

Pro funkce, jejichž prology a epilogy postupujte podle kanonické formy popsané níže, lze použít zabalená data unwind. To eliminuje potřebu záznamu .xdata a výrazně snižuje prostor potřebný k poskytnutí unwind data. Kanonické prology a epilogy jsou navrženy tak, aby splňovaly společné požadavky jednoduché funkce, která nevyžaduje obslužnou rutinu výjimky a provádí operace nastavení a roztržení ve standardním pořadí.

V této tabulce je uveden formát záznamu .pdata, který zabalen unwind data:

|Posun aplikace Word|Bity|Účel|
|-----------------|----------|-------------|
|0|0-31|*Funkce Start RVA* je 32bitové RVA na začátku funkce. Pokud funkce obsahuje kód palce, musí být nastaven nízký bit této adresy.|
|1|0-1|*Příznak* je dvoubitové pole, které má tyto významy:<br /><br />- 00 = nevyužité údaje o odpočinku; zbývající bity přejděte na záznam .xdata.<br />- 01 = zabalená data unwind.<br />- 10 = zabalená data unwind, kde se předpokládá, že funkce nemá žádný prolog. To je užitečné pro popis fragmentů funkce, které jsou nesousedící se začátkem funkce.<br />- 11 = vyhrazeno.|
|1|2-12|*Délka funkce* je 11bitové pole, které poskytuje délku celé funkce v bajtů děleno 2. Pokud je funkce větší než 4 K bajtů, musí být použit úplný záznam .xdata.|
|1|13-14|*Ret* je 2bitové pole, které označuje, jak funkce vrací:<br /><br />- 00 = return přes pop {pc} (bit *l* příznaku musí být v tomto případě nastaven na 1).<br />- 01 = návrat pomocí 16bitové větve.<br />- 10 = návrat pomocí 32bitové větve.<br />- 11 = žádný epilog vůbec. To je užitečné pro popis nesousedící fragment funkce, který může obsahovat pouze prolog, ale jehož epilog je jinde.|
|1|15|*H* je 1bitový příznak, který označuje, zda funkce "homes" celočíselný parametr registruje (r0-r3) jejich odesláním na začátku funkce a zruší 16 bajtů zásobníku před vrácením. (0 = domov registrů, 1 = domy registry.)|
|1|16-18|*Reg* je 3bitové pole, které označuje index posledního uloženého stálého registru. Pokud *r* bit je 0, pak jsou uloženy pouze celočíselné registry a předpokládá se, že je v rozsahu r4-rN, kde N se rovná 4 + *Reg*. Pokud *r* bit je 1, pak jsou uloženy pouze registry s plovoucí desetinnou desetinnou tísní a předpokládá se, že je v rozsahu d8 dN, kde N se rovná 8 + *Reg*. Speciální kombinace *R* = 1 a *Reg* = 7 označuje, že nejsou uloženy žádné registry.|
|1|19|*R* je 1bitový příznak, který označuje, zda jsou uložené nestálé registry celočíselné registry (0) nebo registry s plovoucí desetinnou desetinnou tázkou (1). Pokud *R* r je nastavena na 1 a *Reg* pole je nastavena na 7, žádné nevolatilní registry byly posunuty.|
|1|20|*L* je 1bitový příznak, který označuje, zda funkce ukládá/obnovuje LR, spolu s dalšími registry označenými polem *Reg.* (0 = neukládá/neobnovuje, 1 = ukládá/obnovuje.)|
|1|21|*C* je 1bitový příznak, který označuje, zda funkce obsahuje další pokyny k nastavení řetězu rámů pro rychlé procházení zásobníku (1) nebo ne (0). Pokud je tento bit nastaven, r11 je implicitně přidán do seznamu celých číselných nevolatilních registrů. (Viz omezení níže, pokud je použit příznak *C.)*|
|1|22-31|*Adjustování zásobníku* je 10bitové pole, které označuje počet bajtů zásobníku, které jsou přiděleny pro tuto funkci, děleno 4. Však pouze hodnoty mezi 0x000-0x3F3 mohou být přímo kódovány. Funkce, které přidělují více než 4044 bajtů zásobníku musí používat úplný záznam .xdata. Pokud je pole *Adjust zásobníku* 0x3F4 nebo větší, mají nízké 4 bity zvláštní význam:<br /><br />- Bity 0-1 označují počet slov nastavení zásobníku (1-4) minus 1.<br />- Bit 2 je nastaven na 1, pokud prolog zkombinoval tuto úpravu do své operace push.<br />- Bit 3 je nastavena na 1, pokud epilog zkombinován tuto úpravu do své pop operace.|

Z důvodu možného propouštění ve výše uvedených kódováních platí tato omezení:

- Pokud je příznak *C* nastaven na 1:

  - Příznak *L* musí být také nastaven na 1, protože řetězení rámu vyžaduje r11 i LR.

  - r11 nesmí být zahrnuta do souboru registrů popsaných *reg*. To znamená, že pokud r4-r11 jsou tlačeny, *Reg* by měl popisovat pouze r4-r10, protože příznak *C* znamená r11.

- Pokud je pole *Ret* nastaveno na 0, příznak *L* musí být nastaven na 1.

Porušení těchto omezení způsobí nepodporovanou sekvenci.

Pro účely níže uvedené diskuse jsou odvozeny dva pseudo-příznaky z *Stack Adjust*:

- *PF* nebo "prolog skládací" označuje, že *Stack Adjust* je 0x3F4 nebo větší a bit 2 je nastavena.

- *EF* nebo "epilog skládání" označuje, že *Stack Adjust* je 0x3F4 nebo větší a bit 3 je nastavena.

Prology pro kanonické funkce mohou mít až 5 instrukcí (všimněte si, že 3a a 3b se vzájemně vylučují):

|Instrukce|Předpokládá se, že opcode existuje, pokud:|Velikost|Opcode|Uvolnit kódy|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*==1|16|`push {r0-r3}`|04|
|2|*C*==1 nebo *L*==1 nebo *R*==0 nebo PF==1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*==1 a (*L*==0 a *R*==1 a PF==0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*==1 a (*L*==1 nebo *R*==0 nebo PF==1)|32|`add r11,sp,#xx`|Fc|
|4|*R*==1 a *Reg* != 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Úprava zásobníku* != 0 a PF==0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instrukce 1 je vždy k dispozici, pokud je *h* bit nastaven na 1.

Chcete-li nastavit řetězení rámu, je k dispozici instrukce 3a nebo 3b, pokud je nastaven bit *C.* Jedná se o 16bitový, `mov` pokud nejsou posunuty žádné jiné registry než r11 a LR; v opačném případě se jedná `add`o 32bitový .

Pokud je zadána nepřeložená úprava, instrukce 5 je explicitní nastavení zásobníku.

Pokyny 2 a 4 jsou nastaveny na základě toho, zda je požadováno push. Tato tabulka shrnuje, které registry jsou uloženy na základě polí *C*, *L*, *R*a *PF.* Ve všech *případech n* se rovná *Reg* + 4, *E* se rovná *Reg* + 8, a *S* se rovná (~*Stack Adjust)*& 3.

|C|L|R|PF|Posunuté celé registry|VFP Registry tlačil|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|r4-r*N*|Žádná|
|0|0|0|1|r*S*-r*N*|Žádná|
|0|0|1|0|Žádná|d8-d*E*|
|0|0|1|1|r*S*-r3|d8-d*E*|
|0|1|0|0|r4-r*N*, LR|Žádná|
|0|1|0|1|r*S*-r*N*, LR|Žádná|
|0|1|1|0|LR|d8-d*E*|
|0|1|1|1|r*S*-r3, LR|d8-d*E*|
|1|0|0|0|r4-r*N*, r11|Žádná|
|1|0|0|1|r*S*-r*N*, r11|Žádná|
|1|0|1|0|r11|d8-d*E*|
|1|0|1|1|r*S*-r3, r11|d8-d*E*|
|1|1|0|0|r4-r*N*, r11, LR|Žádná|
|1|1|0|1|r*S*-r*N*, r11, LR|Žádná|
|1|1|1|0|r11, LR|d8-d*E*|
|1|1|1|1|r*S*-r3, r11, LR|d8-d*E*|

Epilogy pro kanonické funkce následují podle podobné holčikového tvaru, ale obráceně a s některými dalšími možnostmi. Epilog může být dlouhý až 5 instrukcí a jeho forma je přísně diktována formou prologu.

|Instrukce|Předpokládá se, že opcode existuje, pokud:|Velikost|Opcode|
|-----------------|-----------------------------------|----------|------------|
|6|*Upravit zásobník*!=0 a *EF*==0|16/32|`add   sp,sp,#xx`|
|7|*R*==1 a *Reg*!=7|32|`vpop  {d8-dE}`|
|8|*C*==1 nebo (*L*==1 a *H*==0) nebo *R*==0 nebo *EF*==1|16/32|`pop   {registers}`|
|9|*H*==1 a *L*==0|16|`add   sp,sp,#0x10`|
|9b|*H*==1 a *L*==1|32|`ldr   pc,[sp],#0x14`|
|10|*Ret*==1|16|`bx    reg`|
|10b|*Ret*==2|32|`b     address`|

Instrukce 6 je explicitní nastavení zásobníku, pokud je zadána nepřeložená úprava. Vzhledem k tomu, *že PF* je nezávislý na *EF*, je možné mít instrukce 5 přítomen bez instrukce 6, nebo naopak.

Instrukce 7 a 8 použít stejnou logiku jako prolog k určení, které registry jsou obnoveny ze zásobníku, ale s těmito dvěma změnami: za prvé, *EF* se používá místo *PF*; za druhé, pokud *Ret* = 0, pak LR je nahrazen PC v seznamu registrů a epilog ukončí okamžitě.

Pokud *H* je nastavena, pak buď instrukce 9a nebo 9b je k dispozici. Instrukce 9a se používá, když *L* je 0, k označení, že LR není v zásobníku. V tomto případě zásobníku je ručně upravena a *Ret* musí být 1 nebo 2 určit explicitní návrat. Instrukce 9b se používá, když *L* je 1, k označení předčasného ukončení epilogu a vrátit a upravit zásobníku ve stejnou dobu.

Pokud epilog ještě neskončil, pak buď instrukce 10a nebo 10b je k dispozici, k označení 16-bit nebo 32-bit větev, na základě hodnoty *Ret*.

### <a name="xdata-records"></a>Záznamy .xdata

Pokud je zabalený formát unwind nedostatečný k popisu odvíjení funkce, musí být vytvořen záznam xdata proměnné délky. Adresa tohoto záznamu je uložena v druhém slově záznamu .pdata. Formát .xdata je zabalená sada slov s proměnnou délkou, která má čtyři části:

1. Záhlaví 1 nebo 2 slova, které popisuje celkovou velikost struktury .xdata a poskytuje data klíčových funkcí. Druhé slovo je k dispozici pouze v případě, že pole *Počet epilogů* a *Slova kódu* jsou nastaveny na 0. Pole jsou rozdělena v této tabulce:

   |Word|Bity|Účel|
   |----------|----------|-------------|
   |0|0-17|*Délka funkce* je 18bitové pole, které označuje celkovou délku funkce v bajtech vydělené 2. Pokud je funkce větší než 512 KB, musí být k popisu funkce použito více záznamů .pdata a .xdata. Podrobnosti naleznete v části Velké funkce v tomto dokumentu.|
   |0|18-19|*Vers* je 2bitové pole, které popisuje verzi zbývajících xdata. Nyní je definována pouze verze 0. hodnoty 1-3 jsou vyhrazeny.|
   |0|20|*X* je 1bitové pole, které označuje přítomnost (1) nebo nepřítomnost (0) dat výjimky.|
   |0|21|*E* je jednobitové pole, které označuje, že informace popisující jeden epilog je zabalen do záhlaví (1) spíše než vyžadovat další obor slova později (0).|
   |0|22|*F* je 1bitové pole, které označuje, že tento záznam popisuje fragment funkce (1) nebo úplnou funkci (0). Fragment znamená, že neexistuje žádný prolog a že by mělo být ignorováno veškeré zpracování prologu.|
   |0|23-27|*Počet epilogů* je 5bitové pole, které má dva významy v závislosti na stavu bitu *E:*<br /><br /> - Pokud je *E* 0, toto pole je počteno z celkového počtu oborů výjimek popsaných v části 3. Pokud ve funkci existuje více než 31 oborů, musí být toto pole i pole *Kódová slova* nastaveny na 0, což znamená, že je vyžadováno přípojné slovo.<br />- Pokud *E* je 1, toto pole určuje index první unwind kód, který popisuje pouze epilogu.|
   |0|28-31|*Slova kódu* je 4bitové pole, které určuje počet 32bitových slov potřebných k tomu, aby obsahovala všechny unwind kódy v části 4. Pokud je pro více než 63 bajtů unwind kódu vyžadováno více než 15 slov, musí být toto pole i pole *Počet epilogů* nastaveny na 0, což znamená, že je vyžadováno vypoovací slovo.|
   |1|0-15|*Rozšířený počet epilogů* je 16bitové pole, které poskytuje více místa pro kódování neobvykle velkého počtu epilogů. Příponeční slovo, které obsahuje toto pole, je k dispozici pouze v případě, že pole *Počet epilogů* a *Slova kódu* v prvním slově záhlaví jsou nastaveny na 0.|
   |1|16-23|*Rozšířená slova kódu* je 8bitové pole, které poskytuje více místa pro kódování neobvykle velkého počtu slov unwind kódu. Příponeční slovo, které obsahuje toto pole, je k dispozici pouze v případě, že pole *Počet epilogů* a *Slova kódu* v prvním slově záhlaví jsou nastaveny na 0.|
   |1|24-31|Vyhrazeno|

1. Po data výjimky (pokud bit *E* v záhlaví byla nastavena na 0) je seznam informací o oborech epilogu, které jsou zabaleny jeden do slova a uloženy v pořadí zvýšení počáteční posun. Každý obor obsahuje tato pole:

   |Bity|Účel|
   |----------|-------------|
   |0-17|*Epilog Start Offset* je 18bitové pole, které popisuje posun epilogu v bajtech děleno 2 vzhledem k začátku funkce.|
   |18-19|*Res* je 2bitové pole vyhrazené pro budoucí rozšíření. Jeho hodnota musí být 0.|
   |20-23|*Podmínka* je 4bitové pole, které poskytuje podmínku, pod kterou je epilog proveden. Pro bezpodmínečné epilogy by měla být nastavena na 0xE, což znamená "vždy". (Epilog musí být zcela podmíněné nebo zcela bezpodmínečné a v režimu Thumb-2 epilogu začíná první instrukce po operační kód IT.)|
   |24-31|*Epilog Start Index* je 8bitové pole, které označuje index bajtů prvního unwind kódu, který popisuje tento epilog.|

1. Po seznamu oborů epilogu přichází pole bajtů, které obsahují unwind kódy, které jsou podrobně popsány v unwind kódy části v tomto článku. Toto pole je doplněno na konci k nejbližší hranici celého slova. Bajty jsou uloženy v pořadí little-endian tak, aby mohly být přímo načteny v režimu little-endian.

1. Pokud je pole *X* v záhlaví 1, za unwind kód bajtů následují informace o obslužné rutině výjimky. To se skládá z jednoho *rva obslužné rutiny výjimky,* která obsahuje adresu obslužné rutiny výjimky, následovaná okamžitě množstvím dat (proměnná délka) vyžadované obslužnou rutinou výjimky.

Záznam .xdata je navržen tak, aby bylo možné načíst prvních 8 bajtů a vypočítat plnou velikost záznamu, bez délky dat výjimky proměnné velikosti, která následuje. Tento fragment kódu vypočítá velikost záznamu:

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

Přestože prolog a každý epilog má index do unwind kódy, tabulka je sdílena mezi nimi. Není neobvyklé, že mohou všichni sdílet stejné unwind kódy. Doporučujeme, aby autoři kompilátoru optimalizovat pro tento případ, protože největší index, který lze zadat je 255 a že omezuje celkový počet unwind kódy možné pro konkrétní funkci.

### <a name="unwind-codes"></a>Uvolnit kódy

Pole unwind kódy je fond instrukční sekvence, které popisují přesně, jak vrátit zpět účinky prologu, v pořadí, ve kterém operace musí být vrátit zpět. Unwind kódy jsou mini instrukční sada, kódované jako řetězec bajtů. Po dokončení spuštění je vrácená adresa volající funkce v registru LR a všechny nestálé registry jsou obnoveny na jejich hodnoty v době, kdy byla volána funkce.

Pokud bylo zaručeno, že výjimky se vždy vyskytují pouze v těle funkce a nikdy v rámci prologu nebo epilogu, bude nutné pouze jedno unwind sekvence. Model odvíjení systému Windows však vyžaduje možnost unwind z v rámci částečně spuštěna prologu nebo epilogu. Chcete-li vyhovět tomuto požadavku, unwind kódy byly pečlivě navrženy tak, aby jednoznačné mapování 1:1 na každý příslušný operační kód v prologu a epilogu. To má několik důsledků:

- Je možné vypočítat délku prologu a epilogu počítáním počtu unwind kódy. To je možné i s proměnné délky Thumb-2 pokyny, protože existují odlišné mapování pro 16bitové a 32bitové opcodes.

- Počítáním počtu instrukcí za začátkem oboru epilogu je možné přeskočit ekvivalentní počet unwind kódů a provést zbytek sekvence k dokončení částečně provedené unwind, který epilog prováděl.

- Počítáním počtu instrukcí před koncem prologu je možné přeskočit ekvivalentní počet unwind kódů a provést zbytek sekvence vrátit zpět pouze ty části prologu, které dokončily provádění.

V následující tabulce je zobrazeno mapování od unwind kódů na opcodes. Nejběžnější kódy jsou pouze jeden bajt, zatímco méně běžné kódy vyžadují dva, tři nebo dokonce čtyři bajty. Každý kód je uložen z nejvýznamnější bajt na nejméně významný bajt. Unwind code structure se liší od kódování popsaného v ARM EABI, protože tyto unwind kódy jsou navrženy tak, aby mít 1:1 mapování na opcodes v prologu a epilogu, aby bylo možné unwinding částečně provedené prology a epilogy.

|Bajt 1|Bajt 2|Bajt 3|Bajt 4|Opsize|Vysvětlení|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> kde X je (kód & \* 0x7F) 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> kde LR je popped, pokud kód & 0x2000 a r0-r12 jsou popped, pokud odpovídající bit je nastaven v code & 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> kde X je kód & 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> kde X je (Kód & 0x03) + 4 a LR je vyskočila, pokud kód & 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> kde X je (Kód & 0x03) + 8 a LR je vyskočila, pokud kód & 0x04|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> kde X je (kód & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> kde X je (kód & 0x03FF) \* 4|
|ES-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> kde LR je popped, pokud kód & 0x0100 a r0-r7 jsou popped, pokud odpovídající bit je nastaven v code & 0x00FF|
|EE|00-0F|||16|specifické pro společnost Microsoft|
|EE|10-FF|||16|K dispozici.|
|Ef|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> kde X je (kód & 0x000F) \* 4|
|Ef|10-FF|||32|K dispozici.|
|F0-F4||||-|K dispozici.|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> kde S je (kód & 0x00F0) >> 4 a E je kód & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> kde S je ((Kód & 0x00F0) >> 4) + 16 a E je (kód & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFF) \* 4|
|Dm|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFFFF) \* 4|
|Fb||||16|nop (16bitový)|
|Fc||||32|nop (32bitový)|
|Fd||||16|konec + 16-bit nop v epilogu|
|Fe||||32|konec + 32-bit nop v epilogu|
|Ff||||-|end|

To ukazuje rozsah šestnáctkových hodnot pro každý bajt v *unwind*kód kódu , spolu s opcode velikost *Opsize* a odpovídající původní interpretace instrukce. Prázdné buňky označují kratší unwind kódy. V pokynech, které mají velké hodnoty pokrývající více bajtů, jsou nejprve uloženy nejvýznamnější bity. Pole *Opsize* zobrazuje implicitní velikost opcode přidruženou ke každé operaci Thumb-2. Zdánlivé duplicitní položky v tabulce s různými kódováními se používají k rozlišení mezi různými velikostmi operačního kódu.

Unwind kódy jsou navrženy tak, aby první bajt kódu říká, jak celkovou velikost v bajtů kódu a velikost odpovídající opcode v proudu instrukcí. Chcete-li vypočítat velikost prologu nebo epilogu, projděte unwind kódy od začátku sekvence do konce a použijte vyhledávací tabulku nebo podobnou metodu k určení, jak dlouho je odpovídající opcode.

Unwind kódy 0xFD a 0xFE jsou ekvivalentní normální koncový kód 0xFF, ale účet pro jeden extra nop opcode v případě epilogu, buď 16bitový nebo 32bitový. Pro prology jsou kódy 0xFD, 0xFE a 0xFF přesně ekvivalentní. To odpovídá běžným zakončením epilogu `bx lr` nebo `b <tailcall-target>`, které nemají ekvivalentní prologovou instrukci. Tím se zvyšuje pravděpodobnost, že unwind sekvence mohou být sdíleny mezi prologu a epilogů.

V mnoha případech by mělo být možné použít stejnou sadu unwind kódy pro prologu a všechny epilogy. Však pro zpracování unwinding částečně spuštěné prology a epilogů, budete muset mít více unwind sekvence kódu, které se liší v řazení nebo chování. To je důvod, proč každý epilog má svůj vlastní index do unwind pole ukázat, kde začít provádění.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Odvíjení částečných prologů a epilogů

Nejběžnější unwinding případ je, když dojde k výjimce v těle funkce, mimo prologu a všechny epilogy. V tomto případě unwinder spustí kódy v unwind pole začínající na indexu 0 a pokračuje, dokud je zjištěn konec opcode.

Pokud dojde k výjimce při provádění prologu nebo epilogu, je rámec zásobníku pouze částečně vytvořen a unwinder musí přesně určit, co bylo provedeno, aby bylo možné jej správně vrátit zpět.

Zvažte například tuto sekvenci prologu a epilogu:

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

Vedle každého operačního kódu je příslušný unwind kód k popisu této operace. Posloupnost unwind kódy pro prologu je zrcadlový obraz unwind kódy pro epilogu, nepočítaje konečné instrukce. Tento případ je běžné a je důvod, proč unwind kódy proprologu jsou vždy považovány za uloženy v opačném pořadí z pořadí provádění prologu. To nám dává společnou sadu unwind kódy:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Kód 0xFD je speciální kód pro konec sekvence, což znamená, že epilog je jeden 16bitová instrukce delší než prolog. To umožňuje větší sdílení unwind kódy možné.

V příkladu pokud dojde k výjimce, zatímco tělo funkce mezi prologem a epilogem je spuštěno, unwinding začíná případem epilogu při posunu 0 v kódu epilogu. To odpovídá posunu 0x140 v příkladu. Unwinder provede úplné unwind sekvence, protože žádné vyčištění bylo provedeno. Pokud místo toho dojde k výjimce jednu instrukci po začátku kódu epilogu, unwinder můžete úspěšně unwind přeskočením první unwind kód. Vzhledem k tomu, one-to-one mapování mezi opcodes a unwind kódy, pokud unwinding z instrukce *n* v epilogu, unwinder by měl přeskočit první *n* unwind kódy.

Podobná logika funguje v opačném směru pro prolog. Pokud unwinding od posun0 v prologu, nic musí být provedeny. Pokud unwinding z jedné instrukce v unwind sekvence by měla spustit jeden unwind kód od konce, protože prolog unwind kódy jsou uloženy v obráceném pořadí. V obecném případě pokud unwinding z instrukce *n* v prologu, unwinding by měl začít provádění na *n* unwind kódy z konce seznamu kódů.

Prolog a epilog unwind kódy ne vždy přesně shodují. V takovém případě unwind kód pole může obsahovat několik sekvencí kódů. Chcete-li určit posun pro zahájení zpracování kódů, použijte tuto logiku:

1. Pokud unwinding z v rámci těla funkce, začít provádění unwind kódy v indexu 0 a pokračovat, dokud je dosaženo konce opcode.

2. Pokud unwinding z v rámci epilogu, použijte počáteční index specifický pro epilogu, který poskytuje obor epilogu. Vypočítejte, kolik bajtů je počítač od začátku epilogu. Přeskočte vpřed prostřednictvím unwind kódy, dokud všechny již provedené pokyny jsou zaúčtovány. Spusťte unwind sekvence začíná v tomto okamžiku.

3. Pokud unwinding z v rámci předlogu, začít od indexu 0 v unwind kódy. Vypočítejte délku kódu prologu z sekvence a potom vypočítejte, kolik bajtů je počítač z konce prologu. Přeskočte vpřed prostřednictvím unwind kódy, dokud všechny neprovedené pokyny jsou zaúčtovány. Spusťte unwind sekvence začíná v tomto okamžiku.

Unwind kódy pro prologu musí být vždy první v poli. Jsou to také kódy používané k odpočinku v obecném případě odvíjení z těla. Všechny sekvence kódu specifické pro epilogby by měly následovat bezprostředně po posloupnosti kódu prologu.

### <a name="function-fragments"></a>Fragmenty funkcí

Pro optimalizaci kódu může být užitečné rozdělit funkci na nesousedící části. Když toto je hotovo, každý fragment funkce vyžaduje vlastní samostatný .pdata – a případně .xdata – záznam.

Za předpokladu, že prolog funkce je na začátku funkce a nelze rozdělit, existují čtyři případy fragmentu funkce:

- Pouze prolog; všechny epilogy v jiných fragmentech.

- Prolog a jeden nebo více epilogů; další epilogy v jiných fragmentech.

- Žádné prology nebo epilogy; prologu a jednoho nebo více epilogů v jiných fragmentech.

- Pouze epilogy; prologu a případně dalších epilogů v jiných fragmentech.

V prvním případě musí být popsán pouze prolog. To lze provést v kompaktní formě .pdata tak, že popisuje prolog normálně a zadání *množiny hodnotu* 3 označuje žádný epilog. V úplném formuláři .xdata to lze provést poskytnutím prologu unwind kódy v indexu 0 jako obvykle a určení epilogu počet 0.

Druhý případ je jako normální funkce. Pokud je pouze jeden epilog v fragmentu a je na konci fragmentu, pak kompaktní záznam .pdata lze použít. V opačném případě musí být použit úplný záznam .xdata. Mějte na paměti, že posuny zadané pro zahájení epilogu jsou relativní vzhledem k začátku fragmentu, nikoli k původnímu spuštění funkce.

Třetí a čtvrtý případ jsou varianty prvního a druhého případů, s výjimkou, že neobsahují prolog. V těchto situacích se předpokládá, že před začátkem epilogu existuje kód a je považován za součást těla funkce, která by za normálních okolností byla odvinuta zrušením účinků prologu. Tyto případy proto musí být zakódovány pseudo-prologu, který popisuje, jak uvolnit z uvnitř těla, ale který je považován za 0-délka při určování, zda provést částečné unwind na začátku fragmentu. Alternativně tento pseudo-prolog uvaděčů může být popsán pomocí stejných unwind kódy jako epilogu, protože pravděpodobně provádět ekvivalentní operace.

Ve třetím a čtvrtém případě je přítomnost pseudoprologu určena nastavením pole *Příznak* kompaktního záznamu .pdata na hodnotu 2 nebo nastavením příznaku *F* v hlavičce .xdata na hodnotu 1. V obou případech je ignorována kontrola pro částečný prolog unwind a všechny unwinds bez epilogu jsou považovány za úplné.

#### <a name="large-functions"></a>Velké funkce

Fragmenty lze použít k popisu funkcí větších než limit 512 kB, který jsou uloženy bitovými poli v hlavičce .xdata. Chcete-li popsat velmi velké funkce, stačí rozdělit na fragmenty menší než 512 KB. Každý fragment by měl být upraven tak, aby nerozdělil epilog na více částí.

Pouze první fragment funkce obsahuje prolog; všechny ostatní fragmenty jsou označeny jako bez prologu. V závislosti na počtu epilogů může každý fragment obsahovat nulu nebo více epilogů. Mějte na paměti, že každý obor epilogu v fragmentu určuje jeho počáteční posun vzhledem k začátku fragmentu, nikoli začátek funkce.

Pokud fragment nemá žádný prolog a žádný epilog, stále vyžaduje vlastní .pdata – a případně .xdata – záznam k popisu, jak unwind z v těle funkce.

#### <a name="shrink-wrapping"></a>Smršťovací balení

Složitější zvláštní případ fragmentů funkce je *smršťovací balení*, technika pro odložení registru uloží od začátku funkce na později ve funkci, optimalizovat pro jednoduché případy, které nevyžadují ukládání registru. To lze popsat jako vnější oblast, která přiděluje místo zásobníku, ale šetří minimální sadu registrů a vnitřní oblast, která ukládá a obnovuje další registry.

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

Smršťovací zabalené funkce se obvykle očekává, že předem přidělit místo pro další registru uloží v pravidelné `str` `stm` prologu a potom provést ukládání registru pomocí nebo místo `push`. To udržuje všechny manipulace zásobníku ukazatel v původní prologu funkce.

Příklad zmenšit zabalené funkce musí být rozdělena do tří oblastí, které jsou označeny jako A, B a C v komentářích. První oblast A pokrývá začátek funkce až do konce dalších nevolatilních uložení. Záznam .pdata nebo .xdata musí být vytvořen tak, aby popisoval tento fragment jako prolog a žádné epilogy.

Střední oblast B získá vlastní .pdata nebo .xdata záznam, který popisuje fragment, který nemá žádný prolog a žádný epilog. Unwind kódy pro tuto oblast však musí být stále k dispozici, protože je považován za tělo funkce. Kódy musí popisovat složený prolog, který představuje jak původní registry uložené v prologu region-A, tak další registry uložené před vstupem do oblasti B, jako by byly vytvořeny jednou posloupností operací.

Registr uloží pro oblast B nelze považovat za "vnitřní prolog", protože složený prolog popsaný pro oblast B musí popisovat prolog region-A a další uložené registry. Pokud fragment B byly popsány jako s prologu, unwind kódy by také znamenat velikost tohoto prologu a neexistuje žádný způsob, jak popsat složený prolog způsobem, který mapuje one-to-one s opcodes, které pouze uložit další registry.

Další ukládací registr musí být považován za součást oblasti A, protože dokud nejsou dokončeny, složený prolog není přesně popsat stav zásobníku.

Poslední oblast C získá vlastní záznam .pdata nebo .xdata, popisující fragment, který nemá žádný prolog, ale má epilog.

Alternativní přístup může fungovat také v případě, že manipulace zásobníku provádí před vstupem do oblasti B lze snížit na jednu instrukci:

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

Klíčem je, že na každé hranici instrukce zásobníku je plně konzistentní s unwind kódy pro oblast. Pokud unwind dojde před vnitřní push v tomto příkladu, je považován za součást oblasti A a pouze oblast Prologue je odvíjet. Pokud unwind dojde po vnitřní push, je považován za součást oblasti B, který nemá žádný prolog, ale má unwind kódy, které popisují vnitřní push a původní prolog z oblasti A. Podobná logika platí pro vnitřní pop.

### <a name="encoding-optimizations"></a>Optimalizace kódování

Vzhledem k bohatosti unwind kódů a schopnost využít kompaktní a rozšířené formy dat, existuje mnoho příležitostí k optimalizaci kódování pro další snížení prostoru. Při agresivním použití těchto technik může být čistá režie popisu funkcí a fragmentů pomocí unwind kódů poměrně minimální.

Nejdůležitější optimalizace je dávat pozor, aby zaměnit prolog/epilog hranice pro odvíjení účely s logickým prologu/epilogu hranice z hlediska kompilátoru. Odvíjecí hranice lze zmenšit a zpřísnit pro zlepšení efektivity. Prolog může například obsahovat kód po nastavení zásobníku k provedení dalších ověřovacích kontrol. Ale jakmile všechny manipulace zásobníku je dokončena, není nutné kódovat další operace a nic nad rámec, které lze odebrat z unwinding prologu.

Stejné pravidlo platí pro délku funkce. Pokud existují data – například fond literálu – který následuje za epilogem ve funkci, neměl by být zahrnut jako součást délky funkce. Zmenšením funkce pouze na kód, který je součástí funkce, je mnohem větší, že epilog bude na samém konci a kompaktní. lze použít záznam pdata.

V prologu, jakmile je ukazatel zásobníku uložen do jiného registru, obvykle není nutné zaznamenávat žádné další opcodes. Chcete-li uvolnit funkci, první věc, která je provedena, je obnovit SP z uloženého registru, a tak další operace nemají žádný vliv na unwind.

Epilogy s jednou instrukcí nemusí být kódovány vůbec, jako obory nebo jako unwind kódy. Pokud unwind probíhá před spuštěním této instrukce, pak lze předpokládat, že je z v rámci těla funkce a právě provádění prologu unwind kódy je dostačující. Pokud unwind probíhá po spuštění jedné instrukce, pak podle definice probíhá v jiné oblasti.

Epilogy s více instrukcemi nemusí zakódovat první instrukce epilogu ze stejného důvodu jako předchozí bod: pokud dojde k unwind před provedením této instrukce, je postačující úplné prologu. Pokud k odvětru dojde po této instrukci, je třeba vzít v úvahu pouze následné operace.

Unwind kód opětovné použití by mělo být agresivní. Index určený každým oborem epilogu odkazuje na libovolný počáteční bod v poli unwind kódů. Nemusí ukazovat na začátek předchozí sekvence; může ukazovat uprostřed. Nejlepší přístup je zde generovat požadovanou sekvenci kódu a pak hledat přesnou shodu bajtů v již zakódovaném fondu sekvencí a použít libovolnou dokonalou shodu jako výchozí bod pro opakované použití.

Pokud po jednoinstrukční epilogů jsou ignorovány, neexistují žádné zbývající epilogy, zvažte použití kompaktní .pdata formulář; to se stává mnohem pravděpodobnější, v nepřítomnosti epilogu.

## <a name="examples"></a>Příklady

V těchto příkladech je základna obrázku na 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Příklad 1: Funkce listu, žádní místní

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x000535F8 (= 0x004535F8-0x00400000)

- Slovo 1

  - *Příznak* = 1, označující formáty kanonického prologu a epilogu

  - *Délka funkce* = 0x31 (= 0x62/2)

  - *Ret* = 1, označující 16bitový návrat větve

  - *H* = 0, označující, že parametry nebyly homed

  - *R*=0 a *Reg* = 1, označující push/pop r4-r5

  - *L* = 0, což znamená, že není uloženo/obnoveno LR

  - *C* = 0, což znamená žádné řetězení rámu

  - *Adjustovat zásobníku* = 0, což znamená žádné nastavení zásobníku

### <a name="example-2-nested-function-with-local-allocation"></a>Příklad 2: Vnořená funkce s místním přidělením

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x000533AC (= 0x004533AC -0x00400000)

- Slovo 1

  - *Příznak* = 1, označující formáty kanonického prologu a epilogu

  - *Délka funkce* = 0x35 (= 0x6A/2)

  - *Ret* = 0, označující pop {pc} návrat

  - *H* = 0, označující, že parametry nebyly homed

  - *R*=0 a *Reg* = 3, označující push/pop r4-r7

  - *L* = 1, což naznačuje, že LR bylo uloženo/obnoveno

  - *C* = 0, což znamená žádné řetězení rámu

  - *Úprava zásobníku* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Příklad 3: Vnořená variadická funkce

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x00053988 (= 0x00453988-0x00400000)

- Slovo 1

  - *Příznak* = 1, označující formáty kanonického prologu a epilogu

  - *Délka funkce* = 0x2A (= 0x54/2)

  - *Ret* = 0, označující návrat ve stylu pop {pc} (v tomto případě ldr pc,[sp],#0x14 return)

  - *H* = 1, označující parametry byly homed

  - *R*=0 a *Reg* = 2, označující push/pop r4-r6

  - *L* = 1, což naznačuje, že LR bylo uloženo/obnoveno

  - *C* = 0, což znamená žádné řetězení rámu

  - *Adjustovat zásobníku* = 0, což znamená žádné nastavení zásobníku

### <a name="example-4-function-with-multiple-epilogues"></a>Příklad 4: Funkce s více epilogy

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

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x000592F4 (= 0x004592F4-0x00400000)

- Slovo 1

  - *Příznak* = 0, označující .xdata záznam přítomen (povinné z důvodu více epilogů)

  - *.xdata adresa* - 0x00400000

.xdata (proměnná, 6 slov):

- Slovo 0

  - *Délka funkce* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0, označující první verzi xdata

  - *X* = 0, což znamená, že data o žádné výjimce

  - *E* = 0, označující seznam oborů epilogu

  - *F* = 0, označující úplný popis funkce, včetně prologu

  - *Počet epilogů* = 0x04, označující 4 celkové obory epilogu

  - *Kódová slova* = 0x01, označující jedno 32bitové slovo unwind kódů

- Slova 1-4, popisující 4 epilogobory na 4 místech. Každý obor má společnou sadu unwind kódy, sdílené s prologu, na posun 0x00 a je bezpodmínečné, zadání podmínky 0x0E (vždy).

- Unwind kódy, počínaje Word 5: (sdílené mezi prologu/epilogu)

  - Unwind kód 0 = 0x06: sp += (6 << 2)

  - Unwind kód 1 = 0xDE: pop {r4-r10, lr}

  - Unwind kód 2 = 0xFF: konec

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Příklad 5: Funkce s dynamickým zásobníkem a vnitřním epilogem

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

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x00085A20 (= 0x00485A20-0x00400000)

- Slovo 1

  - *Příznak* = 0, označující .xdata záznam přítomen (potřebné z důvodu více epilogů)

  - *.xdata adresa* - 0x00400000

.xdata (proměnná, 3 slova):

- Slovo 0

  - *Délka funkce* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0, označující první verzi xdata

  - *X* = 0, což znamená, že data o žádné výjimce

  - *E* = 0, označující seznam oborů epilogu

  - *F* = 0, označující úplný popis funkce, včetně prologu

  - *Počet epilogů* = 0x001, označující 1 celkový rozsah epilogu

  - *Kódová slova* = 0x01, označující jedno 32bitové slovo unwind kódů

- Word 1: Obor epilogu při posunu 0xC6 (= 0x18C/2), spuštění unwind indexu kódu na 0x00 a s podmínkou 0x0E (vždy)

- Unwind kódy, počínaje Word 2: (sdílené mezi prologu/epilogu)

  - Unwind kód 0 = 0xC6: sp = r6

  - Unwind kód 1 = 0xDC: pop {r4-r8, lr}

  - Unwind kód 2 = 0x04: sp += (4 << 2)

  - Unwind kód 3 = 0xFD: konec, počítá jako 16-bit instrukce pro epilogu

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

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x00088C24 (= 0x00488C24-0x00400000)

- Slovo 1

  - *Příznak* = 0, označující .xdata záznam přítomen (potřebné z důvodu více epilogů)

  - *.xdata adresa* - 0x00400000

.xdata (proměnná, 5 slov):

- Slovo 0

  - *Délka funkce* =0x000027 (= 0x00004E/2)

  - *Vers* = 0, označující první verzi xdata

  - *X* = 1, označující údaje o výjimce

  - *E* = 1, označující jeden epilog

  - *F* = 0, označující úplný popis funkce, včetně prologu

  - *Počet epilogů* = 0x00, označující unwind kódy epilogu začínají posunem 0x00

  - *Kódová slova* = 0x02, označující dvě 32bitová slova unwind kódů

- Unwind kódy, počínaje Word 1:

  - Unwind kód 0 = 0xC7: sp = r7

  - Unwind kód 1 = 0x05: sp += (5 << 2)

  - Unwind kód 2 = 0xED/0x90: pop {r4, r7, lr}

  - Unwind kód 4 = 0xFF: konec

- Word 3 určuje obslužnou rutinu výjimky = 0x0019A7ED (= 0x0059A7ED - 0x00400000)

- Slova 4 a dále jsou vložená data výjimek

### <a name="example-7-funclet"></a>Příklad 7: Funclet

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

.pdata (pevná, 2 slova):

- Slovo 0

  - *Spuštění funkce RVA* = 0x00088C72 (= 0x00488C72-0x00400000)

- Slovo 1

  - *Příznak* = 1, označující formáty kanonického prologu a epilogu

  - *Délka funkce* = 0x0B (= 0x16/2)

  - *Ret* = 0, označující pop {pc} návrat

  - *H* = 0, označující, že parametry nebyly homed

  - *R*=0 a *Reg* = 7, což znamená, že nebyly uloženy/obnoveny žádné registry

  - *L* = 1, což naznačuje, že LR bylo uloženo/obnoveno

  - *C* = 0, což znamená žádné řetězení rámu

  - *Adjustace zásobníku* = 1, označující nastavení zásobníku o velikosti 1 × 4 bajty

## <a name="see-also"></a>Viz také

[Přehled konvencí ARM ABI](overview-of-arm-abi-conventions.md)<br/>
[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)
