---
title: x64 zpracování výjimek
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 7dab7f3b6593bf4eaed1b8c804deb915677ccf5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195202"
---
# <a name="x64-exception-handling"></a>x64 zpracování výjimek

Přehled strukturované zpracování výjimek a kódování konvence a chování x64 zpracování výjimek jazyka C++. Obecné informace o zpracování výjimek naleznete v tématu [zpracování výjimek v jazyce Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Unwind data pro zpracování výjimek, podpora ladění

Několik datové struktury jsou požadovány pro zpracování výjimek a podporu ladění.

### <a name="struct-runtimefunction"></a>struct RUNTIME_FUNCTION

Zpracování výjimek v tabulce vyžaduje záznam tabulky pro všechny funkce, které přidělit místo v zásobníku nebo volat jiné funkci (například úrovni funkcí). Položky tabulky funkce mají formát:

|||
|-|-|
|ULONG|Počáteční adresa – funkce|
|ULONG|Koncová adresa – funkce|
|ULONG|Adresa unwind info|

RUNTIME_FUNCTION struktura musí být typu DWORD v paměti. Všechny adresy jsou relativní bitové kopie, to znamená, jsou 32bitový posun od počáteční adresu obrázku, který obsahuje záznam tabulky funkcí. Tyto položky jsou seřazené a vložit do části .pdata bitové kopie PE32 +. Pro dynamicky generované funkcí [kompilátorů JIT] modul runtime pro podporu těchto funkcí musí použít RtlInstallFunctionTableCallback nebo RtlAddFunctionTable poskytnout tyto informace pro operační systém. Pokud tak neučiníte způsobí nespolehlivé zpracování výjimek a ladění procesů.

### <a name="struct-unwindinfo"></a>struct UNWIND_INFO

Datová struktura informací o uvolnění se používá k zaznamenání efekty, které funkce má ukazatel na zásobník a kde jsou uloženy do zásobníku stálé registry:

|||
|-|-|
|UBYTE: 3|Version|
|UBYTE: 5|Příznaky|
|UBYTE|Velikost kódu prologu|
|UBYTE|Počet kódy unwind|
|UBYTE: 4|Rámec registru|
|UBYTE: 4|Odsazení rámce registr (škálovat)|
|USHORT \* n|Pole kódy unwind|
|proměnná|Buď formuláře (1) nebo (2) níže může být|

(1) obslužná rutina výjimky

|||
|-|-|
|ULONG|Adresa obslužné rutiny výjimek|
|proměnná|Data obslužné rutiny pro konkrétní jazyk (volitelné)|

(2) zřetězené Unwind Info

|||
|-|-|
|ULONG|Počáteční adresa – funkce|
|ULONG|Koncová adresa – funkce|
|ULONG|Adresa unwind info|

UNWIND_INFO struktura musí být typu DWORD v paměti. Zde je, co znamená jednotlivá pole:

- **Verze**

   Číslo verze dat uvolnění nepovedlo aktuálně 1.

- **příznaky**

   Aktuálně jsou definovány tři příznaky:

   |Příznak|Popis|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Funkce má obslužná rutina výjimky, která by měla být volána při vyhledávání pro funkce, které muset zkoumat výjimky.|
   |`UNW_FLAG_UHANDLER`| Funkce má obslužné rutiny ukončení, která by měla být volána při uvolnění výjimku.|
   |`UNW_FLAG_CHAININFO`| Unwind info, že struktura není primární jedné postupem. Zřetězené unwind místo toho informace, že položka je obsah předchozí RUNTIME_FUNCTION položky. Informace, najdete v části [Chained struktury unwind info](#chained-unwind-info-structures). Pokud je tento příznak nastaven, musí být zrušeno UNW_FLAG_EHANDLER a UNW_FLAG_UHANDLER příznaky. Pole přidělení registru a – zásobník snímků taky, musí mít stejné hodnoty jako primární unwind info.|

- **Velikost kódu prologu**

   Délka sekvence prologu funkce v bajtech.

- **Počet kódy unwind**

   Počet slotů v kódy unwind. Některé kódy, například UWOP_SAVE_NONVOL unwind vyžadují více než jedné pozice v poli.

- **Rámec registru**

   Pokud nenulovou hodnotu, použije funkce ukazatel na rámec (FP), a toto pole je počet stálé registr používaný jako ukazatel na rámec, pomocí stejné kódování pro pole informace o operaci UNWIND_CODE uzlů.

- **Posun (škálovat) registru rámce**

   Pokud je pole rámce registru nenulovou hodnotu, toto pole je škálován posunem oproti RSP, který se použije na formátu zaregistrovat po jeho vytvoření. Skutečné registr FP je nastavena na RSP + 16 \* toto číslo, což umožňuje posun od 0 do 240. Tento posun umožňuje ukázání registr FP doprostřed přidělení místního zásobníku pro dynamické zásobníku, umožňující lepší hustoty kódu prostřednictvím kratší pokyny (Další pokyny slouží formuláři znaménkem posunutí 8 bitů).

- **Pole kódy unwind**

   Pole položek, které vysvětluje efekt prologu na stálé registry a RSP. V části na UNWIND_CODE pro význam jednotlivých položek. Pro účely zarovnání toto pole má vždy sudý počet položek a poslední položka je potenciálně nevyužité. V takovém případě pole je jedním déle, než udávají počet pole kódy unwind.

- **Adresa obslužné rutiny výjimek**

   Relativní bitové kopie ukazatele funkce jazykově specifické výjimky nebo obslužná rutina ukončení, pokud UNW_FLAG_CHAININFO příznak není zaškrtnut a příznaky UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER je nastavená.

- **Data obslužné rutiny pro konkrétní jazyk**

   Data obslužné rutiny výjimek specifické pro jazyk funkce. Formát dat je tento parametr zadán a zcela určeno obslužnou rutinu výjimky používá.

- **Zřetězené Unwind Info**

   Pokud je nastavený příznak UNW_FLAG_CHAININFO Struktura UNWIND_INFO končí řetězcem tři UWORD.  Tyto UWORD představují RUNTIME_FUNCTION informace o funkci zřetězené unwind.

### <a name="struct-unwindcode"></a>struct UNWIND_CODE

Unwind kódu se používá k zaznamenání posloupnost operací v úvodní části, které by ovlivnily stálé registry a RSP. Každá položka kódu má tento formát:

|||
|-|-|
|UBYTE|Posunutí v prologu|
|UBYTE: 4|Kód operace unwind|
|UBYTE: 4|Informace o operaci|

Pole je seřazeno sestupně posun v prologu.

#### <a name="offset-in-prolog"></a>Posunutí v prologu

Posun od začátku této úvodní části koncem instrukce, který provádí tuto operaci, plus 1 (to znamená posun počáteční další instrukci).

#### <a name="unwind-operation-code"></a>Kód operace unwind

Poznámka: Některé kódy operací vyžadují posun bez znaménka na hodnotu v místní zásobníku. Tento posun je od samého začátku, to znamená nejnižší adresu pevné přidělení zásobníku. Pokud pole registru rámce v UNWIND_INFO je nula, je tento posun z RSP. Pokud pole registru rámce je nenulová, jedná se posun od kdy nacházel RSP při registr FP bylo vytvořeno. Se rovná registr FP minus posun registr FP (16 \* registru rámce posun v UNWIND_INFO). Pokud se používá registr FP, pak žádný kód unwind trvá posunu musí použít pouze po registr FP pokládáme stav, v prologu.

Pro všechny operační kódy s výjimkou `UWOP_SAVE_XMM128` a `UWOP_SAVE_XMM128_FAR`posun je vždy jednat o násobek 8, protože všechny zásobníku na hranice 8 bajtů (samotného zásobník je vždy 16 bajtů zarovnána) se ukládají hodnoty, které vás zajímají. Pro operační kódy, které berou krátké posun (méně než 512 kB) obsahuje finální USHORT uzly pro tento kód posun dělený 8. Pro operační kódy, které trvat dlouho posun (512 kB < = posun < 4GB), poslední dva uzly USHORT pro tento kód volí posun (ve formátu little endian).

Pro operační kódy `UWOP_SAVE_XMM128` a `UWOP_SAVE_XMM128_FAR`, posun je vždy násobkem 16, protože všechny operace XMM 128 bitů se musí vyskytovat na paměti, zarovnané 16 bajtů. Proto se používá měřítko 16 pro `UWOP_SAVE_XMM128`, jejímu posuny menší než 1 milion.

Kód operace unwind je jedna z těchto hodnot:

- `UWOP_PUSH_NONVOL` (0) 1 uzel

  Nabízená oznámení registru stálé celých čísel, snížením RSP o 8. Informace o operaci se číslo do registru. Z důvodu omezení na epilogů `UWOP_PUSH_NONVOL` kódy unwind musí být nejdříve uveden v prologu a odpovídajícím způsobem, poslední v kódu unwind. Relativní řazení se vztahuje na všechny ostatní kódy unwind s výjimkou `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 a 3 uzly

  Přidělte oblasti velké velikosti v zásobníku. Existují dva typy. Pokud se o operaci rovná 0, pak je velikost přidělení dělený 8 je zaznamenán v dalším slotem umožňuje přidělení až 512 kB – 8. Pokud operace informace, které se rovná 1, pak bez měřítka velikosti alokace je zaznamenán v následujících dvou sloty ve formátu little endian, což přidělení až 4GB - 8.

- `UWOP_ALLOC_SMALL` (2) 1 uzel

  Přidělení prostoru malé velikosti v zásobníku. Pole informace o operaci se velikost přidělení \* 8 + 8, povolení přidělení od 8 do 128 bajtů.

  Přidělení zásobníku unwind kód by měl vždy používat co nejkratší možné kódování:

  |**Velikost alokační**|**Uvolnění kódu**|
  |-|-|
  |8 až 128 bajtů|`UWOP_ALLOC_SMALL`|
  |136 na 512 kB – 8 bajtů|`UWOP_ALLOC_LARGE`, informace o operaci = 0|
  |512 kB až 4G - 8 bajtů|`UWOP_ALLOC_LARGE`, informace o operaci = 1|

- `UWOP_SET_FPREG` (3) 1 uzel

  Vytvořte registr ukazatele na rámec nastavením registru na některé posun aktuální RSP. Posun je rovna hodnotě registru rámce (škálován) pole posunu v UNWIND_INFO \* 16, což umožňuje posun od 0 do 240. Použití Posun umožňuje zřízení ukazatel na rámec, který odkazuje na střední pevné přidělení zásobníku, pomáhá hustota kód tím, že další přístupy k použití krátkých instrukce formulářů. Pole informace o operaci je vyhrazen a neměl by se používat.

- `UWOP_SAVE_NONVOL` (4) 2 uzly

  Uložení stálé celé číslo registru do zásobníku MOV místo PUSH. Tento kód používá primárně u *shrink-wrapping*, kde je uložen stálé registru do zásobníku v pozici, která byla dříve přidělena. Informace o operaci se číslo do registru. Posun škálovat podle 8 zásobníku je zaznamenán v příštích unwind operační kód datovou oblast, jak je popsáno v poznámce výše.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 uzly

  Uložení stálé celé číslo registru do zásobníku s dlouhým posunem MOV místo PUSH. Tento kód používá primárně u *shrink-wrapping*, kde je uložen stálé registru do zásobníku v pozici, která byla dříve přidělena. Informace o operaci se číslo do registru. Posun bez měřítka zásobníku je zaznamenán v následujících dvou unwind operační kód sloty, jak je popsáno v poznámce výše.

- `UWOP_SAVE_XMM128` (8) 2 uzly

  Uložte všechny 128 bitů stálý XMM registr v zásobníku. Informace o operaci se číslo do registru. Posun škálovat podle 16 zásobníku je zaznamenán v dalším slotu.

- `UWOP_SAVE_XMM128_FAR` (9) 3 uzly

  Uložte všechny 128 bitů stálý XMM registr v zásobníku s dlouhým posunem. Informace o operaci se číslo do registru. Posun bez měřítka zásobníku je zaznamenán v následujících dvou sloty.

- `UWOP_PUSH_MACHFRAME` (10) 1 uzel

  Vložit blok počítače.  To se používá k zaznamenání účinek přerušení hardwaru nebo výjimky. Existují dva typy. Pokud se o operaci rovná 0, jeden z těchto snímků bylo vloženo do zásobníku:

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|Starý RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|RIP|

  Pokud se o operaci rovná 1, pak jednu z těchto snímků bylo vloženo:

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|Starý RSP|
  |RSP+24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|RIP|
  |RSP|Kód chyby|

  Tento kód unwind se vždy zobrazí ve fiktivní prologu, který je ve skutečnosti nikdy proveden, ale místo toho se zobrazí před skutečné vstupní bod rutiny přerušení a existuje jenom k poskytování místo, kde můžete simulovat nasdílení změn rámce počítače. `UWOP_PUSH_MACHFRAME` zaznamenává tuto simulaci, která indikuje, že je počítač koncepčně dokončení této operace:

  1. Vyvolat přes POP RIP návratovou hodnotu z horní části zásobníku do *Temp*
  
  1. Push SS

  1. Starý RSP nabízených oznámení

  1. Push EFLAGS

  1. Push CS

  1. Push *Temp*

  1. Vložit kód chyby (Pokud se informace op rovná 1)

  Simulované `UWOP_PUSH_MACHFRAME` operace sníží RSP podle 40 (informace o op se rovná 0) nebo 48 (informace o op se rovná 1).

#### <a name="operation-info"></a>Informace o operaci

Význam bits informace o operaci, závisí na kódu operace. Ke kódování registru pro obecné účely (integer), je použít toto mapování:

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 až 15|R8 k R15|

### <a name="chained-unwind-info-structures"></a>Zřetězené struktury unwind info

Pokud je nastavený příznak UNW_FLAG_CHAININFO, je sekundární struktury unwind info a sdílenou – obslužná rutina/zřetězené – informace o výjimce adresu pole obsahuje informace o primární unwind. Tento ukázkový kód načte primární unwind informace za předpokladu, že `unwindInfo` je nastaven příznak, který má UNW_FLAG_CHAININFO strukturu.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Zřetězené informace jsou užitečné ve dvou situacích. Nejdřív může sloužit pro segmenty nesouvislé kódu. Pomocí zřetězené informace můžete zmenšit velikost požadované unwind informací, protože není nutné duplikovat unwind kódů z primárního unwind info.

Zřetězené informace můžete použít také k seskupení uložení volatile registrů. Kompilátor může způsobit prodlevu při ukládání některé závislé registry, dokud není mimo položky prologu funkce. Můžete zaznamenat to tak, že primární unwind informace pro část funkce před seskupené kódu a následným nastavováním zřetězené informace o s nenulovou hodnotu size prologu, kde kódy unwind v zřetězené informace, které odrážejí uložení stálé registrů. V takovém případě jsou kódy unwind všechny výskyty UWOP_SAVE_NONVOL. Seskupení, který ukládá stálé registry s využitím PUSH nebo upravuje RSP registru pomocí dalších pevné zásobníku přidělení se nepodporuje.

UNWIND_INFO položku, která má UNW_FLAG_CHAININFO sada může obsahovat RUNTIME_FUNCTION položku, jejíž položku UNWIND_INFO má také UNW_FLAG_CHAININFO nastavit, říká se jim *více shrink-wrapping*. Nakonec zřetězených unwind informací, že ukazatele dospět UNWIND_INFO položku, která má UNW_FLAG_CHAININFO vymazána; Toto je primární UNWIND_INFO položka, která odkazuje na vstupní bod skutečný procedury.

## <a name="unwind-procedure"></a>Unwind – procedura

Unwind kódu je seřazen v sestupném pořadí. Když dojde k výjimce, úplný kontext uložený v kontextového záznamu v operačním systému. Odeslání logiky výjimka je následně vyvolány, která provádí tyto kroky k nalezení obslužné rutiny výjimky:

1. Aktuální RIP uložené v záznamu o kontextu slouží k vyhledání položky v tabulce runtime, která popisuje aktuální funkci (nebo část funkce pro zřetězené UNWIND_INFO položky).

1. Pokud se nenajde žádný záznam tabulky funkcí, pak je ve funkci typu list a RSP řeší návratový ukazatel. Vrácené ukazatel na [RSP] je uložen v rámci aktualizované, simulované RSP je zvýšen o 8 a opakovat krok 1.

1. Pokud se najde záznam tabulky funkcí, RIP může nacházet ve třech oblastech: a) v epilogu, (b) v prologu nebo c) v kódu, který může být pokryté komponentami obslužné rutiny výjimky.

   - Case) Pokud RIP je v rámci epilogu, pak opouští funkce ovládacího prvku, může být žádná obslužná rutina výjimky, který je přidružený k této výjimky pro tuto funkci a efekty epilogu musí být nadále výpočetního kontextu volající funkce. Chcete-li zjistit, pokud je v rámci epilogu datový proud kódu z RIP RIP na je zkontrolován. Pokud tento datový proud kódu je možné přiřadit ke konci části legitimní epilogu pak je v epilog a zbývající část epilogu simulujeme, s kontextového záznamu, aktualizovat, protože každou instrukci jsou zpracovávána. Potom se opakuje kroku 1.

   - Případ b) Pokud RIP leží v prologu, nemá -li ovládací prvek není vložené funkce, může být žádná obslužná rutina výjimky, který je přidružený k této výjimky pro tuto funkci a efekty prologu musí vrátit zpět k výpočetním kontextu volající funkce. RIP se v prologu, pokud vzdálenost od zahájení funkce do RIP je menší než nebo roven velikosti prologu kódována unwind info. Účinky prologu jsou odděleny prohledávání vpřed prostřednictvím unwind kódů pro první položku s posunem menší než nebo rovný posunu RIP od samého začátku funkce a pak vracením všechny zbývající položky v kódu unwind. Krok 1 se pak opakuje.

   - Případu c) Pokud RIP se nenachází v prologu nebo epilogu a funkci má obslužné rutiny výjimek (UNW_FLAG_EHANDLER nastavuje), pak se nazývá obslužné rutiny specifické pro jazyk. Obslužná rutina vyhledá svoje data a volání funkce jako odpovídající filtru. Obslužné rutiny specifické pro jazyk může vrátit, že výjimka byla zpracována nebo, že má být pokračování hledání. Unwind ho také můžete spustit přímo.

1. Pokud vrátí zpracované stav obslužné rutiny specifické pro jazyk, pak se pokračuje pomocí původního záznamu o kontextu.

1. Pokud neexistuje žádná obslužná rutina konkrétní jazyk nebo obslužná rutina vrátí stav "pokračuje v hledání", musí být oddělen stav volajícího kontextového záznamu. Toho lze dosáhnout zpracování všech prvků pole kód unwind vracením každého. Krok 1 se pak opakuje.

Při řetězení unwind info je zahrnuta, stále postupovali podle těchto základních kroků. Jediným rozdílem je, že při procházení unwind kódu k provedení operace unwind prologu efekty, jakmile je dosaženo konce pole, je nadřazená unwind informace pak propojen a šel celý unwind kódu můžete najít zde. Toto propojení pokračuje, dokud přicházejících u unwind informace bez příznaku UNW_CHAINED_INFO a pak dokončí walking jeho unwind kódu.

Nejmenší sadu unwind dat je 8 bajtů. To představuje funkci, která jen přidělených 128 bajtů zásobníku nebo méně a může být uložen jeden stálé registr. Toto je také velikost zřetězené struktury unwind informace prologu nulové délky s žádné kódy unwind.

## <a name="language-specific-handler"></a>Obslužné rutiny specifické pro jazyk

Relativní adresa obslužné rutiny specifické pro jazyk je k dispozici v UNWIND_INFO pokaždé, když jsou nastaveny příznaky UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER. Jak je popsáno v předchozí části, se nazývá obslužné rutiny specifické pro jazyk jako součást hledání pro obslužnou rutinu výjimky, nebo jako součást unwind. Má tento prototyp:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** poskytuje ukazatel na záznam o výjimce, která má standardní definice Win64.

**EstablisherFrame** je adresa base pevné přidělení zásobníku pro tuto funkci.

**ContextRecord** body ke kontextu výjimky v době byla vyvolána výjimka (v případě obslužné rutiny výjimek) nebo aktuální kontext (v případě obslužné rutiny ukončení) "unwind".

**DispatcherContext** odkazuje na dispečer kontext pro tuto funkci. Má tato definice:

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** je hodnota RIP v rámci této funkce. Tato hodnota je adresa výjimky nebo adresu, ve kterém ovládací prvek vlevo o funkce. RIP slouží k určení, zda ovládací prvek je v rámci některé chráněné konstrukce v této funkci, například `__try` blokovat `__try` / `__except` nebo `__try` / `__finally`.

**Hodnotu ImageBase** je obrázek základní (zatížení adresa) modul obsahující tuto funkci, a přidat do 32-bit odsazení použité v položce funkce unwind info k zaznamenání relativní adresy.

**FunctionEntry** poskytuje ukazatel RUNTIME_FUNCTION funkce položka uchovávající funkce a unwind info relativní adresy základní image pro tuto funkci.

**EstablisherFrame** je adresa base pevné přidělení zásobníku pro tuto funkci.

**TargetIp** poskytuje adresu volitelné instrukce, která určuje adresu pokračování procesu odvíjení. Tato adresa se ignoruje, pokud **EstablisherFrame** není zadán.

**ContextRecord** odkazuje na kontext výjimky pro použití kódem odeslání/unwind výjimek systému.

**LanguageHandler** odkazuje na konkrétní jazyk obslužné rutině, volána.

**HandlerData** odkazuje na obslužné rutiny specifické pro jazyk data pro tuto funkci.

## <a name="unwind-helpers-for-masm"></a>Unwind pomocníci pro MASM

Chcete-li rutiny správné sestavení, je sada pseudo operací, které je možné souběžně s skutečné sestavení pokyny k vytvoření odpovídající .pdata a .xdata. Existuje také sada maker, která poskytuje zjednodušené použití pseudo operací pro jejich většiny běžných použití.

### <a name="raw-pseudo-operations"></a>Nezpracovaná operace pseudo

|Operace pseudostavů.|Popis|
|-|-|
|PROC rámce \[:*ehandler*]|Způsobí, že MASM generovat funkci položka v .pdata tabulky a vrátit se zpět informace v .xdata funkce uživatele strukturované zpracování výjimek unwind chování.  Pokud *ehandler* je k dispozici, tento proces je zadána v .xdata jako obslužné rutiny specifické pro jazyk.<br /><br /> Při použití atributu rámce, musí být následován znakem. ENDPROLOG směrnice.  Pokud je funkce – funkce typu list (jak je definováno v [funkce typy](../build/stack-usage.md#function-types)) atribut rámce je zbytečné, jako jsou zbývající část těchto pseudo operací.|
|. PUSHREG *zaregistrovat*|Vytvoří položku UWOP_PUSH_NONVOL unwind kódu pro zadaný registr číslo pomocí aktuální posun v prologu.<br /><br /> To by měla sloužit pouze s registry stálé celé číslo.  Nabízená oznámení volatile registrů, použijte. ALLOCSTACK 8 místo|
|. SETFRAME *zaregistrovat*, *posun*|Výplně v rámci registrace pole a posun v informacích o unwind pomocí zadaného registru a posun. Posun musí být násobkem 16 a menší než nebo rovna 240. Tato direktiva generuje také položku UWOP_SET_FPREG unwind kódu pro zadaný registr pomocí aktuální posun prologu.|
|. ALLOCSTACK *velikost*|Generuje UWOP_ALLOC_SMALL nebo UWOP_ALLOC_LARGE se zadanou velikostí pro aktuální posun v prologu.<br /><br /> *Velikost* operand musí být násobkem 8.|
|. SAVEREG *zaregistrovat*, *posun*|Generuje UWOP_SAVE_NONVOL nebo položku UWOP_SAVE_NONVOL_FAR unwind kódu pro zadaný registr a posun pomocí aktuální posun prologu. MASM zvolí nejúčinnější kódování.<br /><br /> *Posun* musí být kladná a násobkem 8. *Posun* je relativní vzhledem k základní třídě rámce podle postupu, který je obvykle ve RSP, nebo pokud používáte rámcový ukazatel ukazatel na rámec bez měřítka.|
|. SAVEXMM128 *zaregistrovat*, *posun*|Generuje UWOP_SAVE_XMM128 nebo položku UWOP_SAVE_XMM128_FAR unwind kódu pro zadaný Registr XMM a posun pomocí aktuální posun prologu. MASM zvolí nejúčinnější kódování.<br /><br /> *Posun* musí být kladná a násobkem 16.  *Posun* je relativní vzhledem k základní třídě rámce podle postupu, který je obvykle ve RSP, nebo pokud používáte rámcový ukazatel ukazatel na rámec bez měřítka.|
|. PUSHFRAME \[ *kód*]|Vytvoří položku UWOP_PUSH_MACHFRAME unwind kódu. Pokud volitelný *kód* je zadán kód položka unwind dostane Modifikátor 1. V opačném případě Modifikátor je 0.|
|.ENDPROLOG|Signalizuje konec deklarace prologu.  Musí proběhnout v první 255 bajtů funkce.|

Tady je ukázkový prolog funkce s správné použití většiny operační kódy:

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>MASM – makra

Pro zjednodušení používání [nezpracovaná operace pseudo](#raw-pseudo-operations), je sada makra, definovaná v ksamd64.inc, která slouží k vytvoření prologů typický postup a epilogů.

|– Makro|Popis|
|-|-|
|alloc_stack(n)|Přiděluje blok zásobníku n bajtů (pomocí `sub rsp, n`) a vysílá příslušné unwind informace (.allocstack n)|
|save_reg *reg*, *loc*|Uloží stálé registru *reg* v zásobníku volání na RSP posun *loc*a vysílá unwind příslušné informace. (.savereg reg umístění)|
|push_reg *reg*|Stálé registrace nabízených oznámení *reg* v zásobníku a vysílá unwind příslušné informace. (.pushreg registru)|
|rex_push_reg *reg*|Uložení stálé registru do zásobníku pomocí operace push 2 bajtů a vydává příslušné unwind informace (.pushreg reg) by měl ten použije, pokud je první instrukci ve funkci tak, aby byl funkci horká-opravitelnou za provozu.|
|save_xmm128 *reg*, *umístění*|Uloží stálé registru XMM *reg* v zásobníku volání na RSP posun *loc*a vysílá příslušné unwind informace (.savexmm128 reg, umístění)|
|set_frame *reg*, *offset*|Nastaví rámec registru *reg* bude RSP + *posun* (použití `mov`, nebo `lea`) a vysílá příslušné unwind informace (.set_frame reg, odsazení)|
|push_eflags|Eflags pomocí nabízených oznámení `pushfq` instrukce a vysílá příslušné unwind informace (.alloc_stack 8)|

Tady je ukázkový prolog funkce s správné použití makra:

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Definice unwind dat v jazyce C

Tady je popis C unwind dat:

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>Viz také:

[x64 – softwarové konvence](../build/x64-software-conventions.md)
