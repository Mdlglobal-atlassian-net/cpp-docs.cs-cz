---
title: "Zpracovávání výjimek v jazyce ARM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fdbb6ea3563fb82e90b2bc4ca19f76c43c703cf3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="arm-exception-handling"></a>Zpracovávání výjimek v jazyce ARM
Systém Windows na ARM používá stejné strukturovaného zpracování mechanismus pro asynchronní výjimky generované hardwaru a synchronní výjimky generované softwaru výjimek. Obslužné rutiny výjimek specifické pro jazyk je postavená na Windows strukturovaného zpracování pomocí jazyka podpůrné funkce výjimek. Tento dokument popisuje zpracování výjimek v systému Windows na ARM a pomocníky jazyk používaný kód, který je generován MASM a kompilátor Visual C++.  
  
## <a name="arm-exception-handling"></a>Zpracovávání výjimek v jazyce ARM  
 Windows na ARM používá *unwind kódy* k řízení uvolnění zásobníku během [strukturovanému zpracování výjimek](http://msdn.microsoft.com/library/windows/desktop/ms680657) (SEH). Unwind kódy jsou sekvenci bajtů, které jsou uložené v části .xdata spustitelné bitové kopie. Popisují operaci kódu prologu a epilogu funkce abstraktní způsobem tak, aby důsledky prologu funkce může být v rámci přípravy na rámec zásobníku volajícího unwinding vrátit zpět.  
  
 EABI ARM (embedded aplikace binární rozhraní) určuje unwinding modelu výjimky, který používá unwind kódy, ale není dostatečná pro SEH unwinding v systému Windows, který musí zpracování asynchronní případech, kdy procesor uprostřed prologu nebo epilogu funkce. Windows taky odděluje unwinding řízení na úrovni funkcí unwinding a unwinding oboru pro specifický jazyk, což je jednotná v ARM EABI. Z těchto důvodů Windows on ARM Určuje další podrobnosti o unwinding dat a postup.  
  
### <a name="assumptions"></a>Předpoklady  
 Spustitelné bitové kopie pro Windows on ARM použijte formát přenosného spustitelný soubor (PE). Další informace najdete v tématu [Microsoft PE a specifikace COFF](http://go.microsoft.com/fwlink/p/?linkid=84140). Informace o zpracování výjimek je uložený v částech .pdata a .xdata bitové kopie.  
  
 Zpracování mechanismus výjimek určitých předpokladů o kód, který odpovídá na ARM ABI pro Windows:  
  
-   Když dojde k výjimce v textu, funkce, není důležité, zda prologu operace jsou vrátit zpět, nebo epilogu operací dopředného způsobem. Obě by měl mít stejné výsledky.  
  
-   Prologů a epilogů často vzájemně zrcadlení. To slouží ke snížení velikosti metadata potřebná k popisu unwinding.  
  
-   Funkce jsou obvykle relativně malé. Několik optimalizací spoléhat na to pro efektivní okolních data.  
  
-   Pokud je podmínka je umístěn na epilogu, vztahuje stejnou měrou na každý instrukce v epilogu.  
  
-   Pokud má ukazatel zásobníku (SP2) je uložen v jiné registrace v prologu, které musí zůstat registrace beze změny v rámci funkce, tak, aby původní SP může být kdykoli obnoven.  
  
-   Pokud SP je uložen v jiné zaregistrovat, musí všechny zpracování výhradně nastat do během prologu a epilogu.  
  
-   Chcete-li unwind žádné rámce zásobníku, jsou tyto operace vyžaduje:  
  
    -   Upravit r13 (SP) v přírůstcích po 4 bajtů.  
  
    -   POP – jeden nebo více celočíselné registry.  
  
    -   POP – jeden nebo více VFP (virtuální s plovoucí desetinnou čárkou) zaregistruje.  
  
    -   Zkopírujte hodnotu libovolný zaregistrovat do r13 (SP).  
  
    -   Pomocí malé operace po snížení zatížení SP ze zásobníku.  
  
    -   Jeden z několika typů dobře definovaný rámce analyzovat.  
  
### <a name="pdata-records"></a>.pdata záznamů  
 Záznamy .pdata PE formát obrázku jsou uspořádaného pole pevnou délkou položky, které popisují každou funkce manipulace s zásobníku. Listů funkcí, které jsou funkce, které Nevolejte jiných funkcí, nevyžadují .pdata záznamy při jejich nemáte manipulaci zásobníku. (To znamená, že nevyžadují žádné místní úložiště a nemáte k uložení nebo obnovení nezávislé registry.). Záznamy pro tyto funkce lze vynechat z části .pdata ušetřit místo. Operace unwind z jednoho z těchto funkcí můžete jednoduše zkopírujete zpáteční adresu z na odkaz zaregistrovat (LR) k čítač programu (počítače) až po volající.  
  
 Každý záznam .pdata pro ARM délce 8 bajty. Obecný formát záznamu umístí relativní virtuální adresy (RVA) spouštění funkce v první slovo 32-bit, a druhá slovo, které obsahuje ukazatel na blok proměnlivou délkou .xdata nebo sbalené slovo, které popisuje kanonické funkce unwinding pořadí, jak je uvedené v této tabulce:  
  
|Posun aplikace Word|Bity|Účel|  
|-----------------|----------|-------------|  
|0|0-31|*Funkce spustit RVA* je 32-bit RVA spouštění funkce. Pokud funkce obsahuje kód, Flash, nízkou bit tato adresa musí být nastavena.|  
|1|0-1|*Příznak* je 2-bit pole, které určuje, jak interpretovat zbývajících 30 bitů druhý .pdata slov. Pokud *příznak* se 0, pak je zbývající bits formuláře *výjimka informace RVA* (s nízkou bity dva implicitně 0). Pokud *příznak* je nulová, pak zbývající bits formuláře *mnoha funkcemi Unwind dat* struktura.|  
|1|2-31|*Informace o výjimce RVA* nebo *mnoha funkcemi Unwind Data*.<br /><br /> *Výjimka informace RVA* je adresa struktury proměnlivou délkou výjimka informace uložené v části .xdata. Tato data musí být zarovnána 4bajtový.<br /><br /> *Unwind Data mnoha funkcemi* komprimované popis operací nutných k unwind z funkce, za předpokladu, že kanonický tvar. V takovém případě žádný záznam .xdata je požadovaná.|  
  
### <a name="packed-unwind-data"></a>Mnoha funkcemi Unwind dat  
 Pro funkce jejichž prologů a epilogů podle mnoha funkcemi kanonický tvar popsané níže unwind dat lze. Tím se eliminuje potřeba záznam .xdata a výrazně snižuje požadované zajistit místo unwind data. Kanonický prologů a epilogů jsou navrženy pro běžné požadavkům jednoduché funkci, která nevyžaduje, aby obslužná rutina výjimky a provede jeho operací a rušením ve standardní pořadí.  
  
 Tato tabulka ukazuje formát z .pdata záznam, který má zabaleny unwind dat:  
  
|Posun aplikace Word|Bity|Účel|  
|-----------------|----------|-------------|  
|0|0-31|*Funkce spustit RVA* je 32-bit RVA spouštění funkce. Pokud funkce obsahuje kód, Flash, nízkou bit tato adresa musí být nastavena.|  
|1|0-1|*Příznak* je 2-bit pole, které má tyto významy:<br /><br /> -00 = sbalené unwind dat nepoužívá; Zbývající bod bits .xdata záznam.<br />-01 = sbalené unwind data.<br />-10 = sbalené unwind dat, kde se předpokládá mít žádné prologu funkce. To je užitečné pro popisující fragmenty funkce, které jsou nesousedících s spuštění funkce.<br />-11 = vyhrazené.|  
|1|2-12|*Funkce délka* je 11 bitů pole poskytující délku celého funkce v bajtech dělený 2. Pokud funkce je větší než 4 kB, třeba zadat místo toho úplné .xdata záznam.|  
|1|13-14|*Vrácená hodnota* je 2-bit pole, která určuje, jak funkce vrátí hodnotu:<br /><br /> -00 = vrátí prostřednictvím protokolu pop {pc} ( *L* bit příznaku musí být nastavena na hodnotu 1 v tomto případě).<br />-01 = vrátit pomocí větev 16 bitů.<br />-10 = vrátit pomocí 32bitové větev.<br />-11 = žádné epilogu vůbec. To je užitečné pro popisující fragment nesousedících funkce může obsahovat jenom prologu, ale jejichž epilogu je jinde.|  
|1|15|*H* je 1-bit příznak určující, zda funkce "homes" parametr celé číslo (r0-r3) zaregistruje jejich vynucením při spuštění funkce a zruší přidělení zásobníku 16 bajtů před vrácením. (0 = není domácí registrů, 1 = domácnostech registruje.)|  
|1|16-18|*Reg* 3bitová pole, která značí index posledního uloží stálé registrace. Pokud *R* 0 je bit, pak pouze registry celé číslo se ukládají a jsou považovány za v rozsahu r4 nout, kde N je rovno 4 + *Reg*. Pokud *R* bit je 1 a pak zaregistruje se jenom s plovoucí desetinnou čárkou jsou uloženy a se předpokládá, že v rozsahu d8 – rozlišující název, kde N je rovnat hodnotě 8 + *Reg*. Speciální kombinace *R* = 1 a *Reg* = 7 označuje, že jsou uložit žádné Registry.|  
|1|19|*R* je příznak 1-bit, která určuje, jestli jsou uložené registry stálé celočíselné registry (0) nebo s plovoucí desetinnou čárkou Registry (1). Pokud *R* je nastaven na hodnotu 1 a *Reg* je nastaveno na 7, byly nabídnutých žádné nezávislé registry.|  
|1|20|*L* je 1-bit příznak, který určuje, zda funkce uloží a obnovování LR, spolu s jinými registry indikován *Reg* pole. (0 = není uložit/obnovit, 1 = nemá uložit/obnovit.)|  
|1|21|*C* je 1-bit příznak, který určuje, zda funkce obsahuje doplňující pokyny k nastavení řetěz rámce pro rychlé zásobníku proti (1) nebo ne (0). Pokud je tento bit nastavený, r11 se implicitně přidá do seznamu celé číslo bez registry uložit. (Viz omezení níže v případě *C* příznak se používá.)|  
|1|22-31|*Zásobník upravit* je 10 bitů pole, které udává počet bajtů zásobníku, které jsou přiděleny pro tuto funkci, dělený 4. Však může být přímo zakódován pouze hodnoty mezi hodnotu 0x000 0x3F3. Funkce, které přidělit víc než 4044 bajtů zásobníku musí používat úplnou .xdata záznam. Pokud *zásobníku upravit* pole je 0x3F4 nebo větší, pak nízkou 4 bits mají zvláštní význam:<br /><br /> -Bits 0-1 označuje počet slov úpravu zásobníku (1-4) minus 1.<br />-Bit 2 je nastavena na hodnotu 1, pokud prologu kombinaci tato úprava do jeho operace push.<br />-Bit 3 je nastavena na hodnotu 1, pokud epilogu kombinaci tato úprava do jeho pop operace.|  
  
 Z důvodu možných propouštění v kódování výše uvedené platí tato omezení:  
  
-   Pokud *C* je příznak nastaven na 1:  
  
    -   *L* příznak musí být také nastavena na hodnotu 1, protože rámce řetězení požadované r11 a LR.  
  
    -   R11 nesmí být zahrnuté v sadě registrů popsaného *Reg*. To znamená, pokud jsou nabídnutých r4 r11, *Reg* by měla pouze popisují r4 r10, protože *C* příznak znamená r11.  
  
-   Pokud *Ret* je nastaveno na hodnotu 0, *L* na 1 musí být nastaven příznak.  
  
 Tato omezení bychom při tom porušili způsobí, že Nepodporovaná pořadí.  
  
 Pro účely následující diskusi se dvěma pseudo příznaky jsou odvozeny od *zásobníku upravit*:  
  
-   *PF* nebo "prologu skládání" znamená, že *zásobníku upravit* je 0x3F4 nebo větší a chvíli 2 je nastaven.  
  
-   *EF* nebo "epilogu skládání" znamená, že *zásobníku upravit* je 0x3F4 nebo větší a chvíli 3 je nastaven.  
  
 Prologů pro kanonické funkce může mít až 5 pokyny (Všimněte si, že se vzájemně vylučují 3a a 3b):  
  
|Instrukce|Operační kód se předpokládá, existuje-li:|Velikost|Operační kód|Unwind kódy|  
|-----------------|-----------------------------------|----------|------------|------------------|  
|1|*H*== 1|16|`push {r0-r3}`|04|  
|2|*C*== 1 nebo *L*== 1 nebo *R*== 0 nebo PF == 1|16/32|`push {registers}`|80-BF/D0-DF/ES ED|  
|3a|*C*== 1 a (*L*== 0 a *R*== 1 a PF == 0)|16|`mov r11,sp`|C0-CR/FB|  
|3b|*C*== 1 a (*L*== 1 nebo *R*== 0 nebo PF == 1)|32|`add r11,sp,#xx`|FC|  
|4|*R*== 1 a *Reg* ! = 7|32|`vpush {d8-dE}`|E0 E7|  
|5|*Upravit zásobníku* ! = 0 a PF == 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|  
  
 Instrukce 1 je vždy k dispozici Pokud *H* bit nastaven na hodnotu 1.  
  
 Nastavení řetězení rámečku, je přítomen instrukce 3a nebo 3b Pokud *C* je nastaven bit. Je 16 bitů `mov` Pokud ne, registry než r11 a LR odesílají; jinak, je 32-bit `add`.  
  
 Pokud je zadán úpravu přeloženy, instrukce 5 je úpravou explicitní zásobníku.  
  
 Pokyny, 2 a 4 se nastavují v závislosti na tom, jestli je požadované push. Tato tabulka shrnuje, která registruje se ukládají na základě *C*, *L*, *R*, a *PF* pole. Ve všech případech *N* rovná *Reg* + 4, *E* rovná *Reg* + 8, a *S* je rovno (~*Upravit zásobníku*) a 3.  
  
|C|L|R|PF|Poslat registry celé číslo|Zaregistruje VFP nabídnutých|  
|-------|-------|-------|--------|------------------------------|--------------------------|  
|0|0|0|0|R4-r*N*|žádná|  
|0|0|0|1|r*S*- r*N*|žádná|  
|0|0|1|0|žádná|D8-d*E*|  
|0|0|1|1|r*S*-r3|D8-d*E*|  
|0|1|0|0|R4-r*N*, LR|žádná|  
|0|1|0|1|r*S*- r*N*, LR|žádná|  
|0|1|1|0|LR|D8-d*E*|  
|0|1|1|1|r*S*-r3 LR|D8-d*E*|  
|1|0|0|0|R4-r*N*, r11|žádná|  
|1|0|0|1|r*S*- r*N*, r11|žádná|  
|1|0|1|0|R11|D8-d*E*|  
|1|0|1|1|r*S*-r3 r11|D8-d*E*|  
|1|1|0|0|R4-r*N*, r11 LR|žádná|  
|1|1|0|1|r*S*- r*N*, r11 LR|žádná|  
|1|1|1|0|R11 LR|D8-d*E*|  
|1|1|1|1|r*S*-r3, r11, LR|D8-d*E*|  
  
 Epilogů pro zpracování kanonické funkce podobné formuláře, ale v zpětného a některé další možnosti. Epilogu může být až 5 pokyny dlouho a jeho formuláře je výhradně závisí na formuláři prologu.  
  
|Instrukce|Operační kód se předpokládá, existuje-li:|Velikost|Operační kód|  
|-----------------|-----------------------------------|----------|------------|  
|6|*Upravit zásobníku*! = 0 a *EF*== 0|16/32|`add   sp,sp,#xx`|  
|7|*R*== 1 a *Reg*! = 7|32|`vpop  {d8-dE}`|  
|8|*C*== 1 nebo (*L*== 1 a *H*== 0) nebo *R*== 0 nebo *EF*== 1|16/32|`pop   {registers}`|  
|9a|*H*== 1 a *L*== 0|16|`add   sp,sp,#0x10`|  
|9b|*H*== 1 a *L*== 1|32|`ldr   pc,[sp],#0x14`|  
|10a|*Vrácená hodnota*== 1|16|`bx    reg`|  
|10b|*Vrácená hodnota*== 2|32|`b     address`|  
  
 Instrukce 6 je úpravou explicitní zásobníku, pokud je určen jiný přeloženými úpravu. Protože *PF* je nezávislý na *EF*, je možné, že instrukce 5 přítomen bez instrukce 6 nebo naopak.  
  
 Pokyny 7 a 8 můžete určit, která registruje jsou obnoveny v zásobníku pomocí stejné logiky, která jako prologu, ale pomocí těchto dvou změní: nejdřív *EF* slouží místě *PF*; druhé, pokud *Ret*  = 0, pak LR nahradí počítače v seznamu registrace a končí epilogu okamžitě.  
  
 Pokud *H* nastavena, pak 9a pokyn nebo 9b je k dispozici. Instrukce 9a se používá při *L* 0, k označení, že LR není v zásobníku. V takovém případě je zásobníku ručně upraveny a *Ret* musí být 1 nebo 2, pokud chcete zadat explicitní vrátit. Instrukce 9b se používá při *L* je 1, k označení časná mohli epilogu a vraťte se a upravit v zásobníku ve stejnou dobu.  
  
 Pokud epilogu nebyla již skončila, pak buď instrukce 10a nebo 10b je k dispozici, k označení 16bitové nebo 32bitové větev, na základě hodnoty z *Ret*.  
  
### <a name="xdata-records"></a>.xdata záznamů  
 Když sbalené unwind formát je nedostatečná pro popisují unwinding funkce, musí být vytvořený záznam .xdata proměnlivou délkou. Adresa tento záznam je uložená v druhé slovo .pdata záznamu. Formát .xdata je sbalené proměnlivou délkou sadu slov, který má čtyři části:  
  
1.  1 nebo 2-word hlavičku, která popisuje celkovou velikost strukturu .xdata a poskytuje klíčové funkce data. Druhý slovo je přítomen pouze pokud *epilogu počet* a *slova kódu* obě pole jsou nastaveny na hodnotu 0. Pole jsou rozdělená v této tabulce:  
  
    |Word|Bity|Účel|  
    |----------|----------|-------------|  
    |0|0-17|*Funkce délka* je pole 18-bit určující celková délka funkce v bajtech dělený 2. Pokud funkci je větší než 512 KB, musí více záznamů .pdata a .xdata použít k popisu funkce. Podrobnosti najdete v tématu v části velké funkce v tomto dokumentu.|  
    |0|18-19|*Vladače* je 2-bit pole, které popisuje verzi zbývající xdata. Aktuálně je definována pouze verze 0; hodnoty 1 – 3 jsou vyhrazené.|  
    |0|20|*X* je 1-bit pole, které určuje (1) přítomnosti nebo absenci (0) data výjimky.|  
    |0|21|*E* je 1-bit pole, které označuje, že je informace, které popisují jeden epilogu balí do záhlaví (1) místo nutnosti další oboru slova novější (0).|  
    |0|22|*F* je 1-bit pole, která určuje, že tento záznam popisuje funkce fragment (1) nebo úplné funkce (0). Fragment znamená, že neexistuje žádná prologu a že veškeré zpracování prologu třeba ji ignorovat.|  
    |0|23-27|*Počet epilogu* je 5-bit pole, která má dva významy, v závislosti na stavu *E* bit:<br /><br /> -Pokud *E* je 0, toto pole je počet celkový počet výjimek obory popsané v části 3. Pokud existuje více než 31 obory ve funkci a pak v tomto poli a *slova kódu* pole musí oba nastavena na hodnotu 0 k označení, že rozšíření je povinný.<br />-Pokud *E* je 1, toto pole určuje index první unwind kód, který popisuje pouze epilogu.|  
    |0|28-31|*Kód slova* je 4-bit pole, které určuje počet slov 32-bit musí obsahovat všechny kódy unwind v části 4. Pokud jsou vyžadovány pro více než 63 unwind kód bajtů, toto pole více než 15 slova a *epilogu počet* pole musí oba nastavena na hodnotu 0 k označení, že rozšíření je povinný.|  
    |1|0-15|*Rozšířené epilogu počet* je 16bitové pole, které poskytuje více místa pro kódování neobvykle velký počet epilogů. Word rozšíření, která obsahuje toto pole je přítomen pouze, pokud *epilogu počet* a *slova kódu* pole v první aplikaci word hlavičky jsou obě nastaveny na hodnotu 0.|  
    |1|16-23|*Rozšířený kód slova* je 8bitové pole, které poskytuje více místa pro kódování neobvykle velký počet unwind kód slova. Word rozšíření, která obsahuje toto pole je přítomen pouze, pokud *epilogu počet* a *slova kódu* pole v první aplikaci word hlavičky jsou obě nastaveny na hodnotu 0.|  
    |1|24-31|Vyhrazené|  
  
2.  Po data výjimky (Pokud *E* bit v hlavičce byla nastavena na hodnotu 0) je přehled informací o epilogu obory, které se jedna slovo mnoha funkcemi a jsou uložené v pořadí podle zvýšení počáteční posun. Každý obor obsahuje tato pole:  
  
    |Bity|Účel|  
    |----------|-------------|  
    |0-17|*Posun spustit epilogu* je na 18-bit pole, která popisuje posun epilogu, v bajtech dělený 2, vzhledem k spuštění funkce.|  
    |18-19|*Res* je vyhrazena pro budoucí rozšíření pole 2 bitů. Její hodnota musí být 0.|  
    |20-23|*Podmínka* je 4-bit pole, které poskytuje podmínky, při které je spouštěn epilogu. Nepodmíněné epilogů musí být nastavená na 0xE, který označuje "vždy". (Epilogu musí být zcela podmíněný nebo zcela nepodmíněné, a v režimu 2 jezdec epilogu začíná první pokyn po IT opcode.)|  
    |24-31|*Index spustit epilogu* je na 8bitové pole, která značí index bajtů první unwind kód, který popisuje tento epilogu.|  
  
3.  Po seznam obory epilogu dodává pole bajtů, které obsahují unwind kódy, které jsou podrobně popsané v části Unwind kódy v tomto článku. Toto pole se vyplní na konci na nejbližší hranici úplné aplikace word. Počet bajtů jsou uloženy v pořadí little endian, takže může být přímo načtených v režimu little endian.  
  
4.  Pokud *X* pole v hlavičce je 1, bajtů kódu unwind následuje za informace obslužná rutina výjimky. Tento postup se skládá z jednoho *RVA obslužná rutina výjimky* obsahující adresu obslužná rutina výjimky, vzápětí (proměnlivou délkou) množství dat, které vyžadují obslužná rutina výjimky.  
  
 Záznam .xdata je navržené tak, aby je možné načíst první 8 bajtů a výpočetní na plnou velikost na záznam, nejsou včetně délka data výjimky proměnlivé velikosti, který následuje dále. Tento fragment kódu vypočítá velikost položky:  
  
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
  
 Athough prologu a každý epilogu má index do unwind kódy, v tabulce jsou sdílena mezi nimi. Není, že se všechny sdílet stejnou unwind kódy. Doporučujeme vám, že kompilátoru zapisovače optimalizovat pro tento případ, protože je 255 největší index, který lze zadat, a celkový počet unwind kódy možné pro určitou funkci, která omezuje.  
  
### <a name="unwind-codes"></a>Unwind kódy  
 Pole unwind kódy je fond instrukce pořadí, které popisují, jak přesně to vrátit důsledky prologu, v pořadí, ve kterém musí být operace vrátit zpět. Unwind kódy jsou sady mini instrukce, kódovaná jako řetězec bajtů. Po dokončení provádění zpáteční adresu volání funkce je v LR zaregistrovat a všechny nezávislé registry obnoví se jejich hodnoty v době, kdy byla zavolána funkce.  
  
 Pokud byly záruku, že výjimky vždy jen nastat do během tělo funkce a nikdy v rámci prologu nebo epilogu, pak pouze jeden unwind pořadí by nezbytné. Unwinding modelu Windows ale vyžaduje schopnost odvíjejí v rámci částečně proveden prologu nebo epilogu. Abychom vyhověli tento požadavek, byly unwind kódy pečlivě navrženy tak, aby měl jednoznačným mapování 1: 1 pro každý relevantní kód operace v prologu a epilogu. To má několik důsledky:  
  
-   Je možné k výpočtu Délka prologu a epilogu určovat počet unwind kódy. To lze provést i s proměnlivou délkou pokyny jezdec-2, protože nejsou k dispozici odlišné mapování pro 16bitové a 32bitové operační kódy.  
  
-   Určovat počet pokynů po spuštění rozsah epilogu, je možné přeskočit ekvivalentní počet unwind kódy a spouštět zbytek pořadí k dokončení, částečně provést unwind, aby byl epilogu výkon.  
  
-   Určovat počet pokynů před koncem prologu, je možné přeskočit ekvivalentní počet unwind kódy a provést zbytek pořadí zrušit pouze ty části prologu, které byly dokončeny provádění.  
  
 V následující tabulce jsou uvedeny mapování z unwind kódy na operační kódy. Nejběžnější kódy jsou právě jeden bajt, zatímco méně běžné ty, které vyžadují dva, tři nebo i čtyři bajtů. Každý kód je uložen z nejvýznamnější bajt nejméně významný bajt. Struktury unwind kód se liší od kódování, popsané v ARM EABI, protože tyto unwind kódy jsou navržené tak, aby měly mapování 1: 1 pro operační kódy prologu a epilogu umožňující unwinding z částečně provést prologů a epilogů.  
  
|Byte 1|Byte 2|Byte 3|Byte 4|Opsize|Vysvětlení|  
|------------|------------|------------|------------|------------|-----------------|  
|00 7F||||16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x7F) * 4|  
|80 BF|00 VYPNUTO|||32|`pop   {r0-r12, lr}`<br /><br /> kde je LR odebrány, pokud kód & 0x2000 a r r0 12 jsou odebrány, pokud odpovídající bit je nastavený v 0x1FFF & kódu|  
|C0 CR||||16|`mov   sp,rX`<br /><br /> kde X je 0x0F & kódu|  
|D0 D7||||16|`pop   {r4-rX,lr}`<br /><br /> kde X je (kód & 0x03) + 4 a LR odebrány, pokud kód & 0x04|  
|D8 DF||||32|`pop   {r4-rX,lr}`<br /><br /> kde X je (kód & 0x03) + 8 a LR odebrány, pokud kód & 0x04|  
|E0 E7||||32|`vpop  {d8-dX}`<br /><br /> kde X je (kód & 0x07) + 8|  
|E8 EB|00 VYPNUTO|||32|`addw  sp,sp,#X`<br /><br /> kde X je (kód & 0x03FF) * 4|  
|ES ED|00 VYPNUTO|||16|`pop   {r0-r7,lr}`<br /><br /> kde je LR odebrány, pokud kód & 0x0100 a r0 – r7 jsou odebrány, pokud je v kódu & 0x00FF nastaven odpovídající bit|  
|EE|00 0F|||16|specifické pro společnost Microsoft|  
|EE|10 VYPNUTO|||16|K dispozici|  
|EF|00 0F|||32|`ldr   lr,[sp],#X`<br /><br /> kde X je (kód & 0x000F) * 4|  
|EF|10 VYPNUTO|||32|K dispozici|  
|F0 F4||||-|K dispozici|  
|F5|00 VYPNUTO|||32|`vpop  {dS-dE}`<br /><br /> kde je (kód & 0x00F0) >> 4 a E je 0x000F & kódu|  
|F6|00 VYPNUTO|||32|`vpop  {dS-dE}`<br /><br /> kde je S ((Code & 0x00F0) >> 4) + 16bitová a E je (kód & 0x000F) + 16|  
|F7|00 VYPNUTO|00 VYPNUTO||16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFF) * 4|  
|F8|00 VYPNUTO|00 VYPNUTO|00 VYPNUTO|16|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFFFF) * 4|  
|F9|00 VYPNUTO|00 VYPNUTO||32|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFF) * 4|  
|DM|00 VYPNUTO|00 VYPNUTO|00 VYPNUTO|32|`add   sp,sp,#X`<br /><br /> kde X je (kód & 0x00FFFFFF) * 4|  
|FB||||16|Nop (16 bitů)|  
|FC||||32|Nop (32 bitů)|  
|FD||||16|end + 16bitové nop v epilogu|  
|FE||||32|end + 32-bit nop v epilogu|  
|VYPNUTO||||-|end|  
  
 Zobrazí rozsah hexadecimální hodnoty pro každý bajtů v unwind kód *kód*, společně s velikost opcode *Opsize* a odpovídající původní interpretace instrukcí. U prázdných buněk znamenat kratší unwind kódy. V pokynech, které mají velkých hodnot pokrývajících několik bajtů jsou uloženy nejprve nejvýznamnějších bits. *Opsize* poli se zobrazí implicitní opcode velikost související s každou operaci jezdec-2. Zřejmá duplicitní položky v tabulce s různá kódování se používají k rozlišení různých opcode velikosti.  
  
 Unwind kódy jsou navržené tak, aby první bajt kód informuje celková velikost v bajtech kódu a velikost odpovídající kód operace v datovém proudu instrukcí. K výpočtu velikosti prologu nebo epilogu, provede unwind kódy od začátku pořadí na konec a použít k určení, jak dlouho je odpovídající opcode vyhledávací tabulky nebo podobné metody.  
  
 Unwind kódy 0xFD a Bugcheck 0xFE odpovídají regulární end kódu 0xFF, ale účet pro jeden další nop opcode v případě epilogu 16bitové nebo 32bitové. Pro prologů jsou kódy 0xFD, Bugcheck 0xFE a 0xFF přesně ekvivalentní. To účty pro běžné zakončení epilogu `bx lr` nebo `b <tailcall-target>`, které nemají ekvivalentní prologu instrukce. To zvýší pravděpodobnost, že unwind pořadí lze sdílet mezi prologu a epilogů.  
  
 V mnoha případech by měl být možné použít stejnou sadu unwind kódy pro prologu a všechny epilogů. Pro zpracování unwinding částečně proveden prologů a epilogů, ale může mít tak, aby měl více pořadí unwind kódu, která se liší v řazení nebo chování. Z tohoto důvodu každý epilogu má vlastní index do pole unwind zobrazíte kde začít provádění.  
  
### <a name="unwinding-partial-prologues-and-epilogues"></a>Unwinding částečné prologů a epilogů  
 Nejběžnější unwinding případem je případě výjimka v těle funkce mimo prologu a všechny epilogů. V takovém případě unwinder spustí kódy v unwind pole počínaje indexem 0 a pokračuje, dokud je zjištěna opcode end.  
  
 Pokud dojde k výjimce při prologu nebo epilogu provádí, pouze částečně sestavený rámce zásobníku a unwinder musí určit přesně co bylo provedeno aby bylo možné správně vrátit zpět.  
  
 Představte si třeba toto prologu a epilogu pořadí:  
  
```  
0000:   push  {r0-r3}         ; 0x04  
0002:   push  {r4-r9, lr}     ; 0xdd  
0006:   mov   r7, sp          ; 0xc7  
...  
0140:   mov   sp, r7          ; 0xc7  
0142:   pop   {r4-r9, lr}     ; 0xdd  
0146:   add   sp, sp, #16     ; 0x04  
0148:   bx    lr  
```  
  
 Vedle každého opcode je vhodné unwind kód k popisu tuto operaci. Pořadí unwind kódy pro prologu je zrcadlený obraz unwind kódy pro epilogu, není počítání konečné instrukcí. Tento případ je běžné a je důvod, proč unwind kódy pro prologu jsou vždy předpokládá, že z pořadí zpracování prologu ukládaly v obráceném pořadí. To nám dává společnou sadu unwind kódy:  
  
```  
0xc7, 0xdd, 0x04, 0xfd  
```  
  
 Kód 0xFD je speciální kód na konci pořadí, které znamená, že se epilogu jeden 16bitové instrukce delší než prologu. To umožňuje větší sdílení unwind kódy.  
  
 V příkladu Pokud dojde k výjimce při spouštění tělo funkce mezi prologu a epilogu unwinding začíná epilogu případu, u posunu 0 v rámci Kód epilogu. To odpovídá posun 0x140 v příkladu. Unwinder provede úplné unwind pořadí, protože bylo provedeno žádné čištění. Pokud místo toho výjimka dojde k jedné instrukce po začátku kód epilogu, můžete unwinder úspěšně unwind přeskočením první unwind kód. Zadané mapování 1: 1 mezi operační kódy a unwind kódy, pokud unwinding z instrukce  *n*  v epilogu, přeskočte unwinder první  *n*  unwind kódy.  
  
 Podobně jako logiku funguje obráceným pro prologu. Pokud unwinding z posunu 0 v prologu, nic musí být spuštěn. Pokud unwinding z jedné instrukce v, začněte unwind pořadí od konce jeden unwind kód, protože prologu unwind kódy jsou uložené v obráceném pořadí. V případě obecné Pokud unwinding z instrukce  *n*  v prologu, unwinding by se měl spustit provádění na  *n*  unwind kódy od konce seznamu kódy.  
  
 Unwind kódy prologu a epilogu není vždy přesně shodují. V takovém případě může mít unwind kódu tak, aby obsahovala několik pořadí kódů. K určení posun k zahájení zpracování kódy, použijte tuto logiku:  
  
1.  Pokud unwinding z v textu, funkce, začátek spuštění unwind kódy indexem 0 a pokračovat, dokud nebude dosaženo opcode end.  
  
2.  Pokud unwinding z v rámci epilogu, použijte konkrétní epilogu počáteční index poskytované epilogu oboru. Vypočítejte, kolik bajty v počítači je od začátku epilogu. Přeskočte předat prostřednictvím unwind kódy, dokud všechny pokyny již provést jsou pozornost. Spusťte unwind pořadí spouštění v daném okamžiku.  
  
3.  Pokud unwinding z v rámci prologu, spusťte z indexu 0 v unwind kódy. Vypočítat délka kódu prologu z pořadí a potom vypočítat počet bajtů v počítači je od konce prologu. Přeskočte předat prostřednictvím unwind kódy, dokud všechny odvolat pokyny jsou pozornost. Spusťte unwind pořadí spouštění v daném okamžiku.  
  
 Unwind kódy pro prologu musí být vždy první v poli. Jsou také kódy používané pro unwind v obecné malá unwinding z v textu. Ihned po pořadí kódu prologu postupujte podle jakékoli kódu pro konkrétní epilogu pořadí.  
  
### <a name="function-fragments"></a>Fragmenty – funkce  
 Optimalizace kódu může být užitečné rozdělit na části nesousedících funkce. Když to uděláte, každý fragment funkce vyžaduje vlastní samostatný .pdata – a které by mohly mít .xdata – záznam.  
  
 Za předpokladu, že funkce prologu je na začátku funkce a nelze rozdělit, jsou čtyři funkce fragment případy:  
  
-   Prologu pouze; všechny epilogů v dalších fragmentů.  
  
-   Prologu a jeden nebo více epilogů; Další epilogů v dalších fragmentů.  
  
-   Žádné prologu nebo epilogů; prologu a jeden nebo více epilogů v dalších fragmentů.  
  
-   Epilogů pouze; prologu a případně dalších epilogů v dalších fragmentů.  
  
 V prvním případě musí být pouze prologu popsané. To lze provést v podobě compact .pdata popisující prologu normálně a určením *Ret* hodnotu 3, která určuje žádné epilogu. Ve formuláři úplné .xdata to lze provést jako obvykle poskytuje unwind kódy prologu indexem 0 a určením epilogu počet 0.  
  
 Druhém případě je stejně jako normální funkce. Pokud existuje jenom jeden epilogu ve fragmentu, a je na konci fragment, můžete záznam compact .pdata používá. Jinak potřeba použít úplnou .xdata záznam. Mějte na paměti, že jsou posuny zadané pro počáteční epilogu od začátku fragment, není původní spuštění funkce.  
  
 Třetí a čtvrtý případech jsou variant případech první a druhý v uvedeném pořadí, s výjimkou jejich neobsahují prologu. V těchto situacích se předpokládá, že je kód před zahájením epilogu a bude považován za součást tělo funkce, která by za normálních okolností odděleny zrušením důsledky prologu. Tyto případy proto musí být kódován pseudo prologu, který popisuje, jak unwind z v textu, ale který je považován za délku 0 při určování, zda provádět částečné unwind na začátku fragment. Alternativně může být tento pseudo prologu popsané pomocí stejné unwind kódy jako epilogu, protože pravděpodobně z důvodu provádějí ekvivalentní operations.  
  
 V případech třetí a čtvrtý přítomnost pseudo prologu je zadána buď pomocí nastavení *příznak* pole záznamu compact .pdata 2, nebo nastavením *F* příznak v hlavičce .xdata na 1. V obou případech kontrolu pro částečné prologu unwind ignorována a všechny jiný epilogu unwinds jsou považovány za úplné.  
  
#### <a name="large-functions"></a>Velké funkce  
 Fragmenty slouží k popisu funkce, které jsou větší než způsobené bitová pole v hlavičce .xdata limit 512 KB. K popisu velké funkce, stačí ho rozdělte na fragmenty menší než 512 KB. Každý fragment je třeba upravit tak, aby nerozděluje epilogu do na více místech.  
  
 Pouze první fragment funkce obsahuje prologu; všechny ostatní fragmenty jsou označeny jako s žádné prologu. V závislosti na počtu epilogů každý fragment může obsahovat nula nebo více epilogů. Uvědomte si, že každý obor epilogu v fragment určuje jeho počáteční posun vzhledem k začátku fragment, nespustí funkce.  
  
 Pokud fragment žádné prologu a žádné epilogu, stále vyžaduje vlastní .pdata – a které by mohly mít .xdata – záznam k popisu postup odvíjejí v rámci tělo funkce.  
  
#### <a name="shrink-wrapping"></a>Zmenšující obalení  
 Složitější zvláštním případem funkce fragmentů, ve kterých je *zmenšující obalení*, uloží technika odložit registrace od začátku funkce později ve funkci, za účelem optimalizace pro jednoduché případů, které nevyžadují ukládání registrace. To lze popsat jako vnější oblast, která přiděluje místo zásobníku, ale uloží minimální sadu registry a vnitřní oblast, která uloží a obnoví další registry.  
  
```  
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
  
 Pečlivě zabaleny funkce se obvykle očekává předem přidělit místo pro další registrace uloží v pravidelných prologu a potom proveďte registraci uloží pomocí `str` nebo `stm` místo `push`. To zajišťuje všechny ukazatel zásobníku manipulaci s původní prologu funkce.  
  
 Funkce pečlivě zabaleny příklad musí rozdělená do tří oblastí, které jsou označeny jako A, B a C v komentářích. V první oblasti popisuje spuštění funkce až do konce další stálé uloží. Záznam .pdata nebo .xdata musí zkonstruovat k popisu fragment tak, že má prologu a žádné epilogů.  
  
 Oblasti střední B získá svůj vlastní .pdata nebo .xdata záznam, který popisuje fragment, který má žádné prologu a žádné epilogu. Však unwind kódy pro tuto oblast musí být stále přítomen protože považuje za tělo funkce. Kódy musí popisovat složené prologu, představující obou původní registry uloženo v oblasti A prologu a další registry uložit před vstupem oblast B, jako kdyby byly vyprodukované jeden posloupnost operací.  
  
 Registr uloží pro oblast, kterou B nelze považovat za "vnitřní prologu", protože složené prologu popsané pro oblast B musí popisovat, oblast A prologu i další registry uložit. Pokud byly fragment B popsané tak, že má prologu, unwind kódy znamenalo by to také velikost této prologu a neexistuje žádný způsob, jak popisují složené prologu způsobem, který mapuje 1: 1 s operační kódy, které pouze uložit další registry.  
  
 Uloží další registrace je třeba zvážit součástí oblasti A, protože dokud nedojde k jejich dokončení, složené prologu přesně nepopisuje stav zásobníku.  
  
 Poslední oblasti C získá svůj vlastní .pdata nebo .xdata záznam popisující fragment, který nemá žádné prologu ale nemá epilogu.  
  
 Alternativní způsob můžete také použít, když zásobník manipulaci provést před vstupem oblast B, se může snížit na jednu instrukcí:  
  
```  
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
  
 Klíč tady je, že na každé hranice, instrukce, není plně v souladu s unwind kódy pro oblast zásobníku. Pokud před vnitřní nabízeného oznámení v tomto příkladu dojde k unwind, bude považován za součást oblasti A, přičemž pouze oblast prologu je oddělen. V případě unwind po vnitřní nabízené předpokládá se, že obsahuje součást oblast B, který nemá žádné prologu, ale má unwind kódy, které popisují vnitřní nabízeného oznámení a původní prologu z oblasti A. podobné logiku pro vnitřní pop.  
  
### <a name="encoding-optimizations"></a>Kódování optimalizace  
 Z důvodu bohatost unwind kódy a možnost využít zkomprimovat a rozšířená forms dat existuje mnoho možností k optimalizaci kódování určené k dalšímu snížení místa. S agresivní využívání těchto postupů může být poměrně minimální net režii popisující funkce a fragmenty pomocí unwind kódy.  
  
 Nejdůležitější optimalizace je dávejte pozor, abyste nezaměnili prologu/epilogu hranice pro účely unwinding logické prologu/epilogu hranic z hlediska kompilátoru. Unwinding hranice můžete zmenšit a provedené náročnější ke zlepšení efektivity. Například prologu může obsahovat kód, až instalační program zásobníku a provést další ověření zkontroluje. Ale po dokončení všech manipulaci zásobníku není nutné ke kódování další operace, a nic nad rámec, který lze odebrat z unwinding prologu.  
  
 Tento stejné pravidlo se vztahuje na funkce délku. Pokud nejsou data – například literálu fondu – epilogu ve funkci, který následuje, neměl by být součástí délka funkce. Zmenšením funkce kódu, který je součástí funkce šance jsou mnohem větší, že epilogu bude velmi end a compact. pdata záznam může být použit.  
  
 V prologu ukazatel zásobníku uložena do jiného rejstříku, je obvykle potřeba zaznamenejte všechny další operační kódy. Unwind funkce, je první věc, kterou bylo dokončeno obnovení SP z registru uložené, a proto další operace nemají žádný vliv na unwind.  
  
 Jedním instrukce epilogů nemusíte být zakódován buď jako obory na všechny, nebo jako unwind kódy. Pokud se unwind se provádí před provedením této instrukce, dá se předpokládat, musí být z v těle funkce a právě provádění unwind kódy prologu je dostačující. Pokud unwind probíhá po provedení jednoho pokyn, pak podle definice dojde místo v jiné oblasti.  
  
 Více instrukce epilogů nemusíte kódovat první instrukcí epilogu, ze stejného důvodu jako předchozí bod: Pokud unwind uskuteční před provedením této instrukce, je úplné prologu unwind dostatečná. Pokud unwind probíhá po instrukce, pak musí být považovány za pouze následných operací.  
  
 Unwind kódu opakovaného použití by měla být agresivní. Každý obor body epilogu na libovolný počáteční bod v poli unwind kódy zadaný index. Nemá tak, aby odkazoval na začátek předchozí pořadí; může odkazovat uprostřed. Nejlepším postupem je pro generování kódu požadované pořadí a pak prohledávání bajtů přesnou shodu ve fondu již kódováním pořadí a použít všechny ideální doplněk jako výchozí bod pro nové použití.  
  
 Pokud po jedné instrukce epilogů jsou ignorovány, neexistují žádné zbývající epilogů, zvažte použití compact .pdata formuláře; stane se mnohem pravděpodobnější chybí epilogu.  
  
## <a name="examples"></a>Příklady  
 V těchto příkladech je základní bitovou kopii na 0x00400000.  
  
### <a name="example-1-leaf-function-no-locals"></a>Příklad 1: Funkce listu, žádné místní hodnoty  
  
```  
Prologue:  
  004535F8: B430      push        {r4-r5}  
Epilogue:  
  00453656: BC30      pop         {r4-r5}  
  00453658: 4770      bx          lr  
```  
  
 .pdata (pevná, 2 slova):  
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x000535F8 (= 0x004535F8 0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 1, označující kanonický formáty prologu a epilogu  
  
    -   *Funkce délka* = 0x31 (= 0x62/2)  
  
    -   *Vrácená hodnota* = 1, označující návratový 16bitové větve  
  
    -   *H* = 0, označující parametry nebyly adresami  
  
    -   *R*= 0 a *Reg* = 1, označující nabízené/pop r4 r5  
  
    -   *L* = 0, označující žádné LR uložit/obnovit  
  
    -   *C* = 0, označující žádné rámce řetězení  
  
    -   *Zásobník upravit* = 0, označující bez úpravy zásobníku  
  
### <a name="example-2-nested-function-with-local-allocation"></a>Příklad 2: Vnořené funkce s místní přidělení  
  
```  
Prologue:  
  004533AC: B5F0      push        {r4-r7, lr}  
  004533AE: B083      sub         sp, sp, #0xC  
Epilogue:  
  00453412: B003      add         sp, sp, #0xC  
  00453414: BDF0      pop         {r4-r7, pc}  
```  
  
 .pdata (pevná, 2 slova):  
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x000533AC (= 0x004533AC-0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 1, označující kanonický formáty prologu a epilogu  
  
    -   *Funkce délka* = 0x35 (= 0x6A/2)  
  
    -   *Vrácená hodnota* = 0, označující pop {pc} návratový  
  
    -   *H* = 0, označující parametry nebyly adresami  
  
    -   *R*= 0 a *Reg* = 3, označující nabízené/pop r4 r7  
  
    -   *L* = 1, označující LR byl uložit/obnovit  
  
    -   *C* = 0, označující žádné rámce řetězení  
  
    -   *Upravit zásobníku* = 3 (0x0C/4 =)  
  
### <a name="example-3-nested-variadic-function"></a>Příklad 3: Vnořené funkce Variadická  
  
```  
Prologue:  
  00453988: B40F      push        {r0-r3}  
  0045398A: B570      push        {r4-r6, lr}  
Epilogue:  
  004539D4: E8BD 4070 pop         {r4-r6}  
  004539D8: F85D FB14 ldr         pc, [sp], #0x14  
```  
  
 .pdata (pevná, 2 slova):  
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x00053988 (= 0x00453988 0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 1, označující kanonický formáty prologu a epilogu  
  
    -   *Funkce délka* = 0x2A (= 0x54/2)  
  
    -   *Vrácená hodnota* = 0, označující pop {pc}-style vrátit (v tomto případě počítači ldr [sp], #0x14 vrátit)  
  
    -   *H* = 1, označující parametry byly adresami  
  
    -   *R*= 0 a *Reg* = 2, označující nabízené/pop r4 r6  
  
    -   *L* = 1, označující LR byl uložit/obnovit  
  
    -   *C* = 0, označující žádné rámce řetězení  
  
    -   *Zásobník upravit* = 0, označující bez úpravy zásobníku  
  
### <a name="example-4-function-with-multiple-epilogues"></a>Příklad 4: Funkce s více epilogů  
  
```  
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
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x000592F4 (= 0x004592F4 0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 0, označující .xdata záznam k dispozici (vyžadováno kvůli více epilogů)  
  
    -   *Adresa .xdata* -0x00400000  
  
 .xdata (proměnné, 6 slova):  
  
-   Word 0  
  
    -   *Funkce délka* = 0x0001A3 (= 0x000346/2)  
  
    -   *Vladače* = 0, která určuje první verze součásti xdata  
  
    -   *X* = 0, označující žádná data výjimky  
  
    -   *E* = 0, označující seznam obory epilogu  
  
    -   *F* = 0, označující popis úplné funkce, včetně prologu  
  
    -   *Počet epilogu* = 0x04, označující 4 obory celkový epilogu  
  
    -   *Kód slova* = 0x01, označující jedno 32bitové slovo unwind kódů  
  
-   Slova 1 – 4 popisující 4 epilogu obory na 4 umístění. Každý obor má společnou sadu unwind kódy, sdílené s prologu na posunu 0x00 a nepodmíněné určující podmínku 0x0E (vždy).  
  
-   Unwind kódy, počínaje Word 5: (sdílené mezi prologu/epilogu)  
  
    -   Unwind kód 0 = 0x06: sp += (6 << 2)  
  
    -   Unwind kód 1 = 0xDE: pop {r4 r10, lr}  
  
    -   Unwind kód 2 = 0xFF: end  
  
### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Příklad 5: Funkce dynamické zásobníku a vnitřní epilogu  
  
```  
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
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x00085A20 (= 0x00485A20 0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 0, označující .xdata záznam k dispozici (je potřeba kvůli více epilogů)  
  
    -   *Adresa .xdata* -0x00400000  
  
 .xdata (proměnné, 3 slova):  
  
-   Word 0  
  
    -   *Funkce délka* = 0x0001A3 (= 0x000346/2)  
  
    -   *Vladače* = 0, která určuje první verze součásti xdata  
  
    -   *X* = 0, označující žádná data výjimky  
  
    -   *E* = 0, označující seznam obory epilogu  
  
    -   *F* = 0, označující popis úplné funkce, včetně prologu  
  
    -   *Počet epilogu* = 0x001, označující oboru 1 celkový epilogu  
  
    -   *Kód slova* = 0x01, označující jedno 32bitové slovo unwind kódů  
  
-   Word 1: Epilogu oboru na posunu 0xC6 (= 0x18C/2), spuštění unwind kód index 0x00 a podmínku 0x0E (vždy)  
  
-   Unwind kódy, počínaje Word 2: (sdílené mezi prologu/epilogu)  
  
    -   Unwind kód 0 = 0xC6: sp = r6  
  
    -   Unwind kód 1 = 0xDC: pop {r4 r8, lr}  
  
    -   Unwind kód 2 = 0x04: sp += (4 << 2)  
  
    -   Unwind kódu 3 = 0xFD: end, počty jako 16bitové instrukce pro epilogu  
  
### <a name="example-6-function-with-exception-handler"></a>Příklad 6: Funkce se obslužná rutina výjimky  
  
```  
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
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x00088C24 (= 0x00488C24 0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 0, označující .xdata záznam k dispozici (je potřeba kvůli více epilogů)  
  
    -   *Adresa .xdata* -0x00400000  
  
 .xdata (proměnné, 5 slova):  
  
-   Word 0  
  
    -   *Funkce délka* = 0x000027 (= 0x00004E/2)  
  
    -   *Vladače* = 0, která určuje první verze součásti xdata  
  
    -   *X* = 1, označující přítomen data výjimky  
  
    -   *E* = 1, označující jeden epilogu  
  
    -   *F* = 0, označující popis úplné funkce, včetně prologu  
  
    -   *Počet epilogu* = 0x00, označující epilogu unwind kódy spustit na posunu 0x00  
  
    -   *Kód slova* = 0x02, označující dva 32-bit slova unwind kódů  
  
-   Unwind kódy, počínaje Word 1:  
  
    -   Unwind kód 0 = 0xC7: sp = r7  
  
    -   Unwind kód 1 = 0x05: sp += (5 << 2).  
  
    -   Unwind kód 2 = 0xed bez možnosti odinstalování/0x90: pop {r4, r7, lr}  
  
    -   Unwind kód 4 = 0xFF: end  
  
-   Word 3 určuje obslužné rutiny výjimek = 0x0019A7ED (= 0x0059A7ED - 0x00400000)  
  
-   Slova 4 a novější jsou data vložená výjimky  
  
### <a name="example-7-funclet"></a>Příklad 7: Funclet  
  
```  
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
  
-   Word 0  
  
    -   *Spuštění funkce RVA* = 0x00088C72 (= 0x00488C72 0x00400000)  
  
-   Word 1  
  
    -   *Příznak* = 1, označující kanonický formáty prologu a epilogu  
  
    -   *Funkce délka* = 0x0B (= 0x16/2)  
  
    -   *Vrácená hodnota* = 0, označující pop {pc} návratový  
  
    -   *H* = 0, označující parametry nebyly adresami  
  
    -   *R*= 0 a *Reg* = 7, označující žádné registry měla uložit/obnovit  
  
    -   *L* = 1, označující LR byl uložit/obnovit  
  
    -   *C* = 0, označující žádné rámce řetězení  
  
    -   *Zásobník upravit* = 1, označující 1 × 4 bajtů zásobník úpravy  
  
## <a name="see-also"></a>Viz také  
 [Přehled konvencí ABI ARM](../build/overview-of-arm-abi-conventions.md)   
 [Běžné problémy s migrací ARM v prostředí Visual C++](../build/common-visual-cpp-arm-migration-issues.md)