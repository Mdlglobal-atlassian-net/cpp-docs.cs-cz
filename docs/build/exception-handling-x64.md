---
title: x64 – ošetření výjimek
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: c1936e51630c78de3e7b9dc8a5c7d141ea01ad4b
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444862"
---
# <a name="x64-exception-handling"></a>x64 – ošetření výjimek

Přehled strukturovaného zpracování výjimek a C++ zpracování výjimek a chování kódování v x64. Obecné informace o zpracování výjimek naleznete v tématu [zpracování výjimek v jazyce C++Visual ](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Unwind data pro zpracování výjimek, podpora ladicího programu

Pro zpracování výjimek a podporu ladění je potřeba několik datových struktur.

### <a name="struct-runtime_function"></a>struct RUNTIME_FUNCTION

Zpracování výjimek založené na tabulkách vyžaduje zadání tabulky pro všechny funkce, které přidělují místo na zásobníku, nebo volají jinou funkci (například nelistové funkce). Položky v tabulce funkcí mají formát:

|||
|-|-|
|ULONG|Počáteční adresa funkce|
|ULONG|Koncová adresa funkce|
|ULONG|Adresa unwind informace|

Struktura RUNTIME_FUNCTION musí být zarovnaná na DWORD v paměti. Všechny adresy jsou relativní vzhledem k obrázkům, to znamená, že jsou 32, posuny od počáteční adresy obrázku, který obsahuje položku tabulky funkcí. Tyto položky jsou seřazené a jsou vloženy do oddílu. pdata obrázku PE32 +. Pro dynamicky generované funkce [kompilátory JIT] musí modul runtime pro podporu těchto funkcí použít RtlInstallFunctionTableCallback nebo RtlAddFunctionTable k poskytnutí těchto informací do operačního systému. K tomuto selhání dojde v důsledku nespolehlivého zpracování výjimek a ladění procesů.

### <a name="struct-unwind_info"></a>struct UNWIND_INFO

Struktura informací o unwind datech se používá k zaznamenání vlivů funkce na ukazatel zásobníku a na to, kde jsou uloženy nestálé Registry v zásobníku:

|||
|-|-|
|UBYTE: 3|Version|
|UBYTE: 5|Příznaky|
|UBYTE|Velikost prologu|
|UBYTE|Počet unwind kódů|
|UBYTE: 4|Registr snímků|
|UBYTE: 4|Posunutí registru snímků (zvětšeno)|
|USHORT \* n|Pole unwind kódů|
|proměnná|Může být buď forma (1) nebo (2) níže.|

(1) obslužná rutina výjimky

|||
|-|-|
|ULONG|Adresa obslužné rutiny výjimky|
|proměnná|Data obslužné rutiny specifické pro jazyk (volitelné)|

(2) zřetězené unwind informace

|||
|-|-|
|ULONG|Počáteční adresa funkce|
|ULONG|Koncová adresa funkce|
|ULONG|Adresa unwind informace|

Struktura UNWIND_INFO musí být zarovnaná na DWORD v paměti. Každé pole znamená:

- **Verze**

   Číslo verze unwind dat, aktuálně 1.

- **Flag**

   V současné době jsou definovány tři příznaky:

   |příznaků|Popis|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Funkce má obslužnou rutinu výjimky, která by měla být volána při hledání funkcí, které potřebují prošetřit výjimky.|
   |`UNW_FLAG_UHANDLER`| Funkce má obslužnou rutinu ukončení, která by měla být volána při odvíjení výjimky.|
   |`UNW_FLAG_CHAININFO`| Tato struktura unwind informace není primární pro proceduru. Místo toho Položka zřetězené unwind informace je obsahem předchozí položky RUNTIME_FUNCTION. Informace naleznete v tématu [Zřetězené struktury unwind info](#chained-unwind-info-structures). Pokud je tento příznak nastaven, musí být zaškrtnuty příznaky UNW_FLAG_EHANDLER a UNW_FLAG_UHANDLER. Také v registru rámců a polích alokace pevného zásobníku musí být stejné hodnoty jako v primárních informacích o unwind.|

- **Velikost prologu**

   Délka prologu funkce v bajtech

- **Počet unwind kódů**

   Počet slotů v poli unwind kódů. Některé unwind kódy, například UWOP_SAVE_NONVOL, vyžadují více než jednu pozici v poli.

- **Registr snímků**

   Pokud je hodnota nenulová, funkce použije ukazatel na rámec (FP) a toto pole je číslo nestálého registru, který se používá jako ukazatel na rámec, a to pomocí stejného kódování pro pole informace o operaci v uzlech UNWIND_CODE.

- **Posunutí registru snímků (zvětšeno)**

   Pokud je pole registru rámce nenulové, toto pole je posun s měřítkem od RSP, který je použit pro registr FP při jeho navázání. Skutečný registr FP je nastaven na RSP + 16 \* tohoto čísla, což umožňuje posuny od 0 do 240. Tento posun umožňuje ukazovat registraci FP do středu přidělení místního zásobníku pro dynamické rámce zásobníku, což umožňuje lepší hustotu kódu prostřednictvím kratších instrukcí. (To znamená, že další pokyny můžou používat 8bitový odsazený posun se znaménkem.)

- **Pole unwind kódů**

   Pole položek, které vysvětlují účinek prologu na netěkavých registrech a RSP. Význam jednotlivých položek najdete v části UNWIND_CODE. Pro účely zarovnání má toto pole vždycky sudý počet položek a konečná položka je potenciálně nevyužitá. V takovém případě je pole o jednu dobu delší, než je uvedeno v poli Počet unwind kódů.

- **Adresa obslužné rutiny výjimky**

   Relativní ukazatel na obrázek buď k obslužné rutině výjimky nebo ukončení konkrétního jazyka, pokud je příznak UNW_FLAG_CHAININFO jasný a je nastavena jedna z příznaků UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER.

- **Data obslužné rutiny specifické pro jazyk**

   Data obslužné rutiny specifické pro jazyk funkce. Formát těchto dat není specifikován a zcela určen specifickou obslužnou rutinou výjimky, která je používána.

- **Zřetězené unwind informace**

   Pokud je nastaven příznak UNW_FLAG_CHAININFO, pak struktura UNWIND_INFO končí třemi UWORDs.  Tyto UWORDs reprezentují RUNTIME_FUNCTION informace pro funkci zřetězeného unwind.

### <a name="struct-unwind_code"></a>struct UNWIND_CODE

Pole unwind kódu slouží k zaznamenání posloupnosti operací v prologu, který má vliv na netěkavé registry a RSP. Každá položka kódu má tento formát:

|||
|-|-|
|UBYTE|Posun v prologu|
|UBYTE: 4|Kód operace unwind|
|UBYTE: 4|Informace o operaci|

Pole je seřazené podle sestupného pořadí posunu v prologu.

#### <a name="offset-in-prolog"></a>Posun v prologu

Posun (od začátku prologu) konce instrukce, která provádí tuto operaci, plus 1 (tj. posun začátku další instrukce).

#### <a name="unwind-operation-code"></a>Kód operace unwind

Poznámka: některé provozní kódy vyžadují posun bez znaménka k hodnotě v rámci místního zásobníku zásobníku. Tento posun je od začátku, tedy od nejnižší adresy pevného přidělení zásobníku. Pokud je pole registru rámce v UNWIND_INFO nula, posun je od RSP. Pokud je pole registru rámce nenulové, je tento posun z místa, kde byl nalezen RSP, když byl vytvořen registr FP. Je rovna registru FP minus offset registru FP (16 \* posun snímku s měřítkem v UNWIND_INFO). Pokud je použit registr FP, pak jakýkoliv unwind kód, který přebírá posun, musí být použit pouze poté, co je v prologu vytvořen registr FP.

Pro všechny operační kódy s výjimkou `UWOP_SAVE_XMM128` a `UWOP_SAVE_XMM128_FAR` je posun vždy násobkem 8, protože všechny hodnoty zásobníku jsou uloženy na hranici 8 bajtů (samotný zásobník je vždy zarovnán na 16 bajtů). U kódů operací, které mají krátký posun (méně než 512K), má konečný USHORT v uzlech pro tento kód posun dělený číslem 8. U kódů operací, které mají dlouhý posun (512K < = offset < 4GB), si poslední dva uzly USHORT pro tento kód podrží posun (ve formátu Little Endian).

Pro operační kódy `UWOP_SAVE_XMM128` a `UWOP_SAVE_XMM128_FAR` je posun vždy násobek 16, protože všechny 128 operace XMM se musí nacházet v paměti zarovnané na 16 bajtů. Proto je faktor škálování 16 použit pro `UWOP_SAVE_XMM128`, což povoluje posuny menší než 1 milion.

Kód operace unwind je jednou z těchto hodnot:

- `UWOP_PUSH_NONVOL` (0) 1 uzel

  Vyhrajte nestálý celočíselný registr, čímž se sníží hodnota RSP o 8. Informace o operaci je číslo registru. Z důvodu omezení epilogů musí být nenávratové kódy `UWOP_PUSH_NONVOL` nejprve uvedeny v prologu a odpovídajícím způsobem, nakonec v poli unwind kódu. Toto relativní řazení platí pro všechny ostatní kódy unwind s výjimkou `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 nebo 3 uzly

  Přidělte v zásobníku velkou oblast. Existují dvě formy. Pokud se informace o operaci rovná 0, pak je v další pozici zaznamenána velikost přidělení dělená 8. to umožňuje přidělení až 512K-8. Pokud se informace o operaci rovná 1, pak je velikost přidělení bez měřítka zaznamenána v následujících dvou slotech ve formátu Little endian a umožňuje přidělení až 4 GB-8.

- `UWOP_ALLOC_SMALL` (2) 1 uzel

  Přidělte oblast v zásobníku o malou velikost. Velikost přidělení je pole informace o operaci \* 8 + 8, což umožňuje přidělení od 8 do 128 bajtů.

  Unwind kód pro přidělení zásobníku by měl vždy používat nejkratší možné kódování:

  |**Velikost přidělení**|**Unwind kód**|
  |-|-|
  |8 až 128 bajtů|`UWOP_ALLOC_SMALL`|
  |136 až 8 bajtů 512K|`UWOP_ALLOC_LARGE`, informace o operaci = 0|
  |512K na 4G-8 bajtů|`UWOP_ALLOC_LARGE`, informace o operaci = 1|

- `UWOP_SET_FPREG` (3) 1 uzel

  Vytvořte registr ukazatele na rámec nastavením registru na určitý posun aktuálního RSP. Posun je roven poli posunutí registru rámce (škálované) v UNWIND_INFO \* 16, což umožňuje posuny od 0 do 240. Použití posunu umožňuje vytvořit ukazatel na rámec, který odkazuje na střed pevného přidělení zásobníku, což přispívá ke hustotě kódu tím, že umožňuje přístup k používání krátkých forem instrukcí. Pole informace o operaci je rezervované a nemělo by se používat.

- `UWOP_SAVE_NONVOL` (4) 2 uzly

  Uloží do zásobníku nestálý celočíselný registr pomocí MOV místo vložení. Tento kód se primárně používá pro *zúžení zalamování*, kde je uložen nestálý registr do zásobníku na pozici, která byla dříve přidělena. Informace o operaci je číslo registru. Posunutí zásobníku škálované až 8 se zaznamenává v dalším slotu unwind kódu operace, jak je popsáno v poznámce výše.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 uzly

  Uložte do zásobníku nestálý celočíselný registr s dlouhým posunem místo vložení pomocí MOV. Tento kód se primárně používá pro *zúžení zalamování*, kde je uložen nestálý registr do zásobníku na pozici, která byla dříve přidělena. Informace o operaci je číslo registru. Posun zásobníku bez měřítka je zaznamenán v následujících dvou slotech kódu unwind operace, jak je popsáno v poznámce výše.

- `UWOP_SAVE_XMM128` (8) 2 uzly

  Uloží všechny 128 bitů v nestálém registru XMM do zásobníku. Informace o operaci je číslo registru. Posunutí zásobníku se škálováním na 16 se zaznamenává v dalším slotu.

- `UWOP_SAVE_XMM128_FAR` (9) 3 uzly

  Uloží všechny 128 bitů s nestálým registrem XMM v zásobníku s dlouhým posunem. Informace o operaci je číslo registru. Posun zásobníku bez měřítka je zaznamenán v následujících dvou slotech.

- `UWOP_PUSH_MACHFRAME` (10) 1 uzel

  Nahrajte rám počítače.  Tento unwind kód se používá k zaznamenání účinku hardwarového přerušení nebo výjimky. Existují dvě formy. Pokud se informace o operaci rovná 0, jeden z těchto snímků byl vložen do zásobníku:

  |||
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|Starý RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|Vložil|

  Pokud se informace o operaci rovná 1, pak byl jeden z těchto snímků vložen:

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|Starý RSP|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|Vložil|
  |RSP|Kód chyby|

  Tento unwind kód se vždy zobrazí v zástupném prologu, který není nikdy proveden, ale zobrazí se před skutečným vstupním bodem rutiny přerušení a existuje pouze místo pro simulaci vložení rámce počítače. `UWOP_PUSH_MACHFRAME` zaznamenává tuto simulaci, která indikuje, že počítač tuto operaci provedl.

  1. Odblokovaná zpáteční adresa RIP z vrcholu zásobníku do *tempa*
  
  1. Vložení SS

  1. Vložit starý RSP

  1. EFLAGS push

  1. Nabízení CS

  1. Doručovat *dočasné*

  1. Kód chyby při vložení (Pokud se informace o op rovná 1)

  Simulovaná operace `UWOP_PUSH_MACHFRAME` snižuje hodnotu RSP 40 (op info Equals 0) nebo 48 (op info Equals 1).

#### <a name="operation-info"></a>Informace o operaci

Význam bitů informací o operaci závisí na kódu operace. Pro kódování registru pro obecné účely (celé číslo) se používá toto mapování:

|||
|-|-|
|0,8|RAX|
|první|RCX|
|odst|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|čl|RDI|
|8 až 15|R8 do R15|

### <a name="chained-unwind-info-structures"></a>Zřetězené struktury unwind info

Pokud je nastaven příznak UNW_FLAG_CHAININFO, pak je struktura unwind info sekundární a v poli sdílená výjimka-obslužná rutina/zřetězené-info adresa obsahuje primární informace o unwind. Tento ukázkový kód načte primární unwind informace za předpokladu, že `unwindInfo` je struktura, která má nastaven příznak UNW_FLAG_CHAININFO.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Zřetězené informace jsou užitečné ve dvou situacích. Nejprve je možné ji použít pro nesouvislé segmenty kódu. Pomocí zřetězených informací můžete zmenšit velikost požadovaných unwind informací, protože nemusíte duplikovat pole unwind Code z primární informace o unwind.

Můžete také použít zřetězené informace k seskupení nestálých uložení registru. Kompilátor může zpozdit uložení některých nestálých registrů, dokud není mimo prolog vstupu funkce. Můžete je zaznamenat pomocí primárního unwind informace pro část funkce před seskupeným kódem a pak nastavit zřetězené informace s nenulovou velikostí prologu, kde unwind kódy v zřetězených informacích odrážejí uložení nestálých registrů. V takovém případě jsou unwind kódy všechny instance UWOP_SAVE_NONVOL. Seskupení, které ukládá nestálé Registry pomocí nabízeného oznámení nebo upravuje registraci RSP pomocí dalšího pevného přidělení zásobníku není podporováno.

Položka UNWIND_INFO, která má UNW_FLAG_CHAININFO sadu, může obsahovat položku RUNTIME_FUNCTION, jejíž položka UNWIND_INFO má také UNW_FLAG_CHAININFO sadu, někdy se jim říká *vícenásobné zalamování*. Nakonec zřetězené informace o zřetězení unwind přicházejí na položku UNWIND_INFO, která má nezaškrtnuté UNW_FLAG_CHAININFO. Tato položka je primární UNWIND_INFO položka, která odkazuje na skutečný vstupní bod procedury.

## <a name="unwind-procedure"></a>Unwind – procedura

Pole unwind kódu je seřazeno v sestupném pořadí. Pokud dojde k výjimce, kompletní kontext je uložen operačním systémem v záznamu kontextu. Poté je vyvolána logika odeslání výjimky, která opakovaně spouští tyto kroky pro nalezení obslužné rutiny výjimky:

1. Pomocí aktuálního protokolu RIP uloženého v záznamu kontextu vyhledejte položku tabulky RUNTIME_FUNCTION, která popisuje aktuální funkci (nebo část funkce pro zřetězené UNWIND_INFO položky).

1. Pokud není nalezena žádná položka tabulky funkcí, pak je v listu funkce a RSP přímo adresuje návratový ukazatel. Návratový ukazatel na [RSP] je uložen v aktualizovaném kontextu, simulovaný RSP RSP se zvýší o 8 a krok 1 se opakuje.

1. Pokud je nalezena položka tabulky funkcí, může protokol RIP spadat do tří oblastí: a) v epilogu, b) v prologu nebo c) v kódu, který může být pokryt obslužnou rutinou výjimky.

   - Případ a) Pokud je RIP v rámci epilogu, pak řízení opouští funkci, pro tuto funkci nemůže být k této výjimce přidružena žádná obslužná rutina výjimky a účinky epilogu musí být nadále k výpočtu kontextu volající funkce. Aby bylo možné zjistit, zda je protokol RIP v rámci epilogu, je prověřen datový proud z RIP. Pokud by tento datový proud kódu mohl odpovídat koncové části oprávněného epilogu, pak je v epilogu a zbývající část epilogu je simulovaná, se záznamem kontextu aktualizovaným při zpracování jednotlivých instrukcí. Po tomto zpracování se krok 1 opakuje.

   - Případ b) Pokud protokol RIP leží v rámci prologu, pak ovládací prvek nezadal funkci, pro tuto funkci nemůže být přidružena žádná obslužná rutina výjimky a účinky prologu musí být vráceny pro výpočet kontextu volající funkce. Protokol RIP je v rámci prologu, pokud vzdálenost od funkce začíná na protokolu RIP je menší nebo rovna velikosti prologu kódované v informacích o unwind. Účinky prologu jsou oddálené kontrolou vpřed pole unwind Codes pro první položku s posunem menším nebo rovným posunem protokolu RIP od spuštění funkce a následným zrušením účinku všech zbývajících položek v poli unwind kódu. Krok 1 se pak opakuje.

   - Případ c) Pokud protokol RIP není v rámci prologu nebo epilogu a funkce má obslužnou rutinu výjimky (UNW_FLAG_EHANDLER je nastavena), je volána obslužná rutina specifická pro jazyk. Obslužná rutina zkontroluje svá data a volá funkce filtru podle potřeby. Obslužná rutina specifická pro jazyk může vrátit, že byla výjimka zpracována nebo zda má pokračovat hledání. Může také inicializovat unwind přímo.

1. Pokud obslužná rutina specifická pro jazyk vrátí zpracovaný stav, pak provádění pokračuje pomocí původního záznamu kontextu.

1. Pokud není k dispozici žádná obslužná rutina specifická pro jazyk nebo obslužná rutina vrátí stav "pokračovat v hledání", záznam kontextu musí být vrácen do stavu volajícího. Provede se zpracováním všech prvků pole unwind kódu, které vrátí účinek každého z nich. Krok 1 se pak opakuje.

V případě zřetězení informací o unwind jsou tyto základní kroky stále následovány. Jediným rozdílem je, že při procházení pole unwind kódu pro unwind efektů prologu je po dosažení konce pole propojeno s nadřazenými informacemi o unwind a celé pole unwind kódu, které se nachází vás provedl. Toto propojení pokračuje, dokud se dorazí na unwind informace bez příznaku UNW_CHAINED_INFO a pak se dokončí procházení pole unwind kódu.

Nejmenší sada unwind dat je 8 bajtů. To by představovalo funkci, která zaznamenala pouze 128 bajtů v zásobníku nebo méně a případně uložila jeden nestálý registr. Je také velikost Zřetězené struktury unwind informací pro Prolog s nulovou délkou bez jakýchkoli unwind kódů.

## <a name="language-specific-handler"></a>Obslužná rutina specifická pro jazyk

Relativní adresa obslužné rutiny specifické pro jazyk je přítomna v UNWIND_INFO vždy, když jsou nastaveny příznaky UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER. Jak je popsáno v předchozí části, obslužná rutina specifická pro jazyk je volána jako součást hledání obslužné rutiny výjimky nebo jako součást objektu unwind. Má tento prototyp:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**Datový ExceptionRecord** poskytuje ukazatel na záznam výjimky, který má standardní definici prostředí win64.

**EstablisherFrame** je adresa základu pevné alokace zásobníku pro tuto funkci.

**ContextRecord** odkazuje na kontext výjimky v době, kdy byla výjimka vyvolána (v případu obslužné rutiny výjimky) nebo v aktuálním kontextu unwind (v případě obslužné rutiny ukončení).

**DispatcherContext** odkazuje na kontext dispečera této funkce. Má tuto definici:

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

**ControlPc** je hodnota RIP v rámci této funkce. Tato hodnota je buď adresa výjimky, nebo adresa, na které ovládací prvek opustil funkci navázání. Protokol RIP slouží k určení, zda je ovládací prvek v některém chráněném konstruktoru uvnitř této funkce, například blok `__try` pro `__try` @ no__t-2 @ no__t-3 nebo `__try` @ no__t-5 @ no__t-6.

**ImageBase** je základní bitová kopie (zátěžová adresa) modulu obsahujícího tuto funkci, která se má přidat k 32m posunům použitým v položce funkce a unwind informacím pro zaznamenávání relativních adres.

**FunctionEntry** poskytuje ukazatel na položku funkce RUNTIME_FUNCTION, která drží funkci a unwind informace o relativních adresách pro tuto funkci.

**EstablisherFrame** je adresa základu pevné alokace zásobníku pro tuto funkci.

**TargetIp** Poskytuje volitelnou adresu instrukce, která určuje adresu pokračování unwind. Tato adresa se ignoruje, pokud není zadaný **EstablisherFrame** .

**ContextRecord** odkazuje na kontext výjimky, aby jej mohl použít kód pro odeslání/unwind systémové výjimky.

**LanguageHandler** odkazuje na volanou rutinu jazykově specifického jazyka.

**HandlerData** odkazuje na data obslužných rutin konkrétního jazyka pro tuto funkci.

## <a name="unwind-helpers-for-masm"></a>Unwind pomocníka pro MASM

Aby bylo možné zapisovat správné rutiny sestavení, je k dispozici sada pseudo operací, které lze použít paralelně se skutečnými pokyny pro sestavení k vytvoření odpovídajících vlastností. pdata a. xdata. A existují sady maker, které poskytují zjednodušené používání pseudo operací pro jejich Nejběžnější použití.

### <a name="raw-pseudo-operations"></a>Nezpracované pseudo operace

|Pseudo – operace|Popis|
|-|-|
|@No__t rámce procedury-0:*ehandler*]|Způsobí, že MASM vygeneruje položku tabulky funkce v. pdata a unwind informace v. xdata pro strukturované zpracování výjimek funkce unwind.  Pokud je přítomen *ehandler* , je tato procedura zadána v. xdata jako obslužná rutina specifická pro jazyk.<br /><br /> Pokud je použit atribut FRAME, musí následovat po. Direktiva ENDPROLOG  Pokud je funkce listová funkce (jak je definována v [typech funkcí](../build/stack-usage.md#function-types)), atribut rámce není zbytečný, stejně jako zbytek těchto pseudo operací.|
|. PUSHREG *registraci*|Vygeneruje položku UWOP_PUSH_NONVOL unwind kódu pro zadané číslo registru pomocí aktuálního posunu v prologu.<br /><br /> Použijte ji pouze s nestálými Registry celých čísel.  Pro vložení těkavých registrů použijte. ALLOCSTACK 8 místo toho|
|. SETFRAME *registr*, *posun*|Vyplní pole registru rámce a posune v informacích o unwind pomocí zadaného registru a posunutí. Posun musí být násobkem 16 a menší nebo roven 240. Tato direktiva také generuje položku UWOP_SET_FPREG unwind kódu pro zadaný registr pomocí aktuálního posunu prologu.|
|. *Velikost* ALLOCSTACK|Generuje UWOP_ALLOC_SMALL nebo UWOP_ALLOC_LARGE s určenou velikostí pro aktuální posun v prologu.<br /><br /> Operandem *velikosti* musí být násobek osmi.|
|. SAVEREG *registr*, *posun*|Generuje položku UWOP_SAVE_NONVOL nebo UWOP_SAVE_NONVOL_FAR unwind kódu pro zadaný registr a posun pomocí aktuálního posunutí prologu. MASM zvolí nejúčinnější kódování.<br /><br /> hodnota *posunu* musí být kladná a násobkem 8. *posun* je relativní vzhledem ke základu rámce procedury, který je obecně v RSP, nebo pokud používáte ukazatel na rámec, ukazatel na rámec bez měřítka.|
|. SAVEXMM128 *registr*, *posun*|Generuje položku UWOP_SAVE_XMM128 nebo UWOP_SAVE_XMM128_FAR unwind kódu pro zadaný XMM registr a posun pomocí aktuálního posunu prologu. MASM zvolí nejúčinnější kódování.<br /><br /> hodnota *posunu* musí být kladná a násobkem 16.  *posun* je relativní vzhledem ke základu rámce procedury, který je obecně v RSP, nebo pokud používáte ukazatel na rámec, ukazatel na rámec bez měřítka.|
|. PUSHFRAME \[*kód*]|Generuje položku UWOP_PUSH_MACHFRAME unwind kódu. Pokud je zadán volitelný *kód* , je položka unwind kódu dána modifikátorem 1. V opačném případě je modifikátor 0.|
|.ENDPROLOG|Signalizuje konec deklarací prologu.  Musí se nacházet v prvních 255 bajtech funkce.|

Zde je ukázkový prolog funkce s řádným využitím většiny operačních kódů:

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

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

Další informace o příkladu epilogu naleznete v tématu [epilog Code](prolog-and-epilog.md#epilog-code) in [x64 prolog a epilog](prolog-and-epilog.md).

### <a name="masm-macros"></a>Makra MASM

Aby bylo možné zjednodušit používání [nezpracovaných pseudo operací](#raw-pseudo-operations), je k dispozici sada maker definovaná v ksamd64. Inc, kterou lze použít k vytvoření typických procedur prologues a epilogues.

|Podokně|Popis|
|-|-|
|alloc_stack (n)|Přidělí rámec zásobníku n bajtů (pomocí `sub rsp, n`) a vygeneruje příslušné informace unwind (. allocstack n).|
|save_reg *reg*, *Loc*|Uloží do zásobníku nestálý registr *reg* v zásobníku na posunutí RSP *Loc*a vygeneruje příslušné informace o unwind. (. Savereg reg; Loc)|
|push_reg *reg*|Vloží do zásobníku nestálý registr *reg* a vygeneruje příslušné informace o unwind. (. pushreg reg)|
|rex_push_reg *reg*|Uloží do zásobníku nestálý registr pomocí dvou bajtů push a vygeneruje příslušné informace unwind (. pushreg reg).  Toto makro použijte v případě, že je nabízena první instrukcí ve funkci, aby se zajistilo, že je funkce Hot-patchovaná.|
|save_xmm128 *reg*, *Loc*|Uloží do zásobníku nestálou *registraci registru XMM na* posunutí RSP *Loc*a vygeneruje příslušné informace unwind (. savexmm128 reg, Loc).|
|set_frame *reg*, *offset*|Nastaví Registry registru *reg* na hodnotu RSP + *offset* (pomocí `mov` nebo `lea`) a vygeneruje příslušné informace unwind (. set_frame reg, offset).|
|push_eflags|Vloží eflags s instrukcí `pushfq` a vygeneruje příslušné informace unwind (. alloc_stack 8).|

Tady je ukázkový prolog funkce se správným využitím maker:

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
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

Zde je uveden popis C unwind dat:

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
