---
title: 'TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyce Visual C++'
ms.date: 11/04/2016
f1_keywords:
- vc.resources
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
ms.openlocfilehash: 0493dd45caf5eb78da435987a4590442a908a5a3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772761"
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyce Visual C++

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje způsob, jakým editor prostředků Visual C++ podporuje více souborů prostředků a soubory hlaviček, které jsou sdíleny v jednom projektu nebo mezi více projekty a jak můžete využít výhod, které podporují. Tato poznámka odpovídá na tyto otázky:

- Když budete chtít rozdělit projekt do více souborů prostředků nebo souborů záhlaví a jak to provedete

- Jak můžete sdílet společné záhlaví. H soubor mezi dvěma. RC – soubory

- Jak rozdělíte zdroje projektu do několika. RC – soubory

- Jak můžete vy (a nástroje) spravovali závislosti sestavení mezi. VERZE RC. CPP, a. Soubory H

Byste měli vědět, že pokud přidáte do projektu další soubor prostředků, ClassWizard nerozpozná prostředky v přidaném souboru.

Tato poznámka je strukturována tak, aby na výše uvedené otázky následujícím způsobem:

- **Přehled o tom, jak Visual C++ spravuje soubory prostředků a hlavičkových souborů** poskytuje přehled, jak příkaz Soubor prostředků obsahuje v jazyce Visual C++ vám umožní používat více zdrojových souborů a hlavičkových souborů ve stejném projektu.

- **Analýza vytvořených pomocí AppWizard. RC a. Soubory H** zkoumá více zdroji a záhlavími, které používají aplikace vytvořená Průvodcem AppWizard souborů. Tyto soubory slouží jako vhodný model pro další zdrojové soubory a soubory hlaviček, které chcete přidat do projektu.

- **Včetně další souborů záhlaví** popisuje, kde můžete chtít zahrnout více souborů záhlaví a poskytuje podrobnosti o tom, jak to provést.

- **Sdílení souboru hlaviček mezi dvěma. Soubory RC** ukazuje, jak můžete sdílet soubor hlavičky více. RC – soubory v různých projektech, nebo případně ve stejném projektu.

- **Použití více souborů prostředků ve stejném projektu** popisuje, kde můžete chtít rozdělit projekt do několika. RC soubory a poskytuje podrobnosti o tom, jak to provést.

- **Vynucení Non-upravovat soubory Visual C++** popisuje, jak zajistit Visual C++ nemohlo upravit a neúmyslně změnit formát vlastního prostředku.

- **Správa symbolů sdílených ve více Visual C++ upravit. Soubory RC** popisuje, jak sdílet stejné symboly napříč více. RC – soubory a jak se vyhnout přiřazení duplicitních číselných hodnot ID.

- **Správa závislostí mezi. VERZE RC. CPP, a. Soubory H** popisuje, jak ve Visual C++ vyhnete zbytečným opětovné kompilace. Souborů CPP, které jsou závislé na souborech prostředků symbolů.

- **Jak Visual C++ spravuje sadu zahrnuje informace** poskytuje technické podrobnosti o tom, jak Visual C++ uchovává informace o více (vnořených). RC – soubory a více souborů záhlaví, které jsou # include 'D podle. Soubor RC.

**Přehled způsobu, jakým Visual C++ spravuje zdrojové soubory a soubory hlaviček**

Visual C++ spravuje jeden. Soubor RC prostředků a odpovídající. Soubor hlaviček H jako dvojici těsně vázaných souborů. Když upravujete a ukládáte zdroje v. Soubor RC, nepřímo upravíte a uložte symboly v odpovídající. Soubor H. Ačkoli můžete otevřít a upravit více. RC – soubory najednou (použitím uživatelského rozhraní MDI Visual C++) pro všechny uvedené. Soubor RC, nepřímo upravíte právě jeden odpovídající soubor záhlaví.

**Hlavičkový soubor symbolů**

Ve výchozím nastavení Visual C++ vždy pojmenuje odpovídající soubor záhlaví prostředků. H, bez ohledu na název souboru prostředků (například MYAPP. RC). Použití **prostředek zahrnuje** příkaz **zobrazení** nabídky v jazyce Visual C++, můžete změnit název tohoto souboru záhlaví aktualizací souboru hlavičkový soubor symbolů v **Set Includes**dialogové okno.

**Směrnice souborů jen pro čtení**

I když Visual C++ Edituje pouze jeden soubor záhlaví pro všechny uvedené. Soubor RC, Visual C++ podporuje odkazy na symboly definované v souborech další záhlaví jen pro čtení. Použití **prostředek zahrnuje** příkaz **zobrazení** nabídky v jazyce Visual C++ můžete zadat libovolný počet souborů další záhlaví jen pro čtení jako směrnice symbolů jen pro čtení. Omezení "jen pro čtení" znamená, že při přidání nového prostředku v. Soubor RC můžete použít symbol definovaný v souboru záhlaví jen pro čtení. ale pokud prostředek odstraníte, symbol stále zůstává definovaný v souboru hlaviček jen pro čtení. Nelze změnit číselnou hodnotu přiřazenou symbolu jen pro čtení.

**Směrnice času kompilace**

Visual C++ podporuje také vnořené soubory prostředků, pokud jeden. Soubor RC je # include 'D v rámci jiného. Při úpravách daný. Soubor RC pomocí Visual C++, všechny prostředky v # include 'D soubory nejsou viditelné. Pokud kompilujete, ale. Soubor RC # include 'D jsou také zkompilovány soubory. Použití **prostředek zahrnuje** příkaz **zobrazení** nabídky v jazyce Visual C++ můžete zadat libovolný počet # include 'D. RC – soubory jako směrnice času kompilace.

Všimněte si, co se stane, pokud načtete do jazyka Visual C++. RC soubor, který #include jiný. RC soubor, který je *není* zadán jako direktiva v době kompilace. Tato situace může nastat při opětovném připojení k Visual C++. RC soubor, který vám byl dříve spravován ručně pomocí textového editoru. Když Visual C++ čte # include 'D. Soubor RC, sloučení # prostředky #include do nadřazeného objektu. Soubor RC. Při ukládání nadřazeného objektu. Soubor RC #include příkaz, v platnosti, budou nahrazeny # prostředky #include. Pokud nechcete, aby k tomuto sloučení došlo, měli byste odebrat #include z nadřazeného příkazu. Soubor RC *předchozí* jeho načtením do Visual C++; potom pomocí Visual C++ přidat zpět stejný #include příkaz jako direktiva v době kompilace.

Visual C++ uloží do. Soubor RC tři druhy výše uvedených informací Set Includes (soubor hlaviček symbolu, směrnice symbolu jen pro čtení a směrnice času kompilace) v #include *a* v prostředcích TEXTINCLUDE. Prostředky TEXTINCLUDE, podrobnosti implementace, které obvykle nepotřebujete řešit, jsou vysvětlené v [jak Visual C++ spravuje sadu obsahující informace](#_mfcnotes_tn035_set_includes).

**Analýza vytvořených pomocí AppWizard. RC a. Soubory H**

Zkoumání kódu aplikace vytvořeného pomocí AppWizard poskytuje přehled o tom, jak Visual C++ spravuje více zdrojových souborů a hlavičkových souborů. Ukázky kódu zkoumané níže jsou z aplikace MYAPP získané přes AppWizard pomocí výchozích možností.

Aplikace vytvořená Průvodcem AppWizard používá více souborů prostředků a více souborů záhlaví, jak je patrné na obrázku níže:

```
RESOURCE.H     AFXRES.H
\       /
\     /
    MYAPP.RC
|
|
    RES\MYAPP.RC2
    AFXRES.RC
    AFXPRINT.RC
```

Můžete zobrazit tyto více vztahů souborů pomocí příkazu Visual C++ File/Set Includes.

MOJE APLIKACE. RC soubor prostředků aplikace, které můžete upravit pomocí Visual C++.

PROSTŘEDEK. H je soubor záhlaví specifický pro aplikaci. Je vždy pojmenováno prostředků. H AppWizard konzistentní s Visual C++ výchozím pojmenováním souboru záhlaví. #Include pro tento soubor hlavičky je prvním příkazem v souboru prostředků (MYAPP. RC):

```
//Microsoft Visual C++ generated resource script
//
#include "resource.h"
```

RES\MYAPP. RC2 obsahuje prostředky, které nebudou upraveny pomocí aplikace Visual C++, ale budou zahrnuty v konečné zkompilován. Soubor EXE. AppWizard nevytvoří žádné takové prostředky ve výchozím nastavení, protože Visual C++ může upravit všechny standardní prostředky, včetně prostředku verze (nová funkce v této verzi). V případě, že chcete přidat vlastní formátované zdroje do tohoto souboru AppWizard vygeneruje prázdný soubor.

Pokud používáte vlastní formátované prostředky, můžete je přidat do RES\MYAPP. RC2 a upravovat pomocí textového editoru Visual C++.

AFXRES. RC a AFXPRINT. RC obsahují standardní prostředky vyžadované některými funkcemi rozhraní. Stejně jako RES\MYAPP. RC2, jsou tyto dva soubory prostředků poskytované rozhraním # include 'D na konci MYAPP. RC a že jsou uvedeny v směrnice času kompilace v dialogovém okně Set Includes. Proto není přímo zobrazit nebo upravit tyto prostředky architektury při úpravě MYAPP. RC v Visual C++, ale jsou zkompilovány do binárního souboru aplikace. Soubor RES a finální. Soubor EXE. Další informace o standardních prostředcích rozhraní, včetně postupů pro jejich úpravu, naleznete v tématu [Technická poznámka 23](../mfc/tn023-standard-mfc-resources.md).

AFXRES. H definuje standardní symboly, jako například `ID_FILE_NEW`, používané rozhraním a používané specificky v AFXRES. RC. AFXRES. H také #include WINRES. H, který obsahuje podmnožinu systému WINDOWS. H, která jsou potřeba pro vygenerovaný Visual C++. RC – soubory také AFXRES. RC. Symboly definované v AFXRES. H jsou k dispozici při úpravách souboru prostředků aplikace (MYAPP. RC). Například `ID_FILE_NEW` se používá pro položku nabídky nový soubor v MYAPP. RC na nabídce prostředků. Nelze změnit ani odstranit tyto symboly definované v rámci rozhraní.

## <a name="_mfcnotes_tn035_including"></a> Včetně další souborů záhlaví

Aplikace vytvořená Průvodcem AppWizard obsahuje pouze dva soubory hlaviček: PROSTŘEDEK. H a AFXRES. H. Pouze zdroj. H je specifické pro aplikaci. Je třeba zahrnout další záhlaví jen pro čtení souborů v následujících případech:

Soubor hlavičky pochází od externího zdroje nebo ho chcete sdílet mezi více projekty nebo více částí stejného projektu.

Soubor hlavičky obsahuje formátování a komentáře, že nechcete, aby Visual C++ změní nebo odfiltruje při uložení souboru. Například možná chcete zachovat #define, používající jako symbolickou aritmetiku, jako:

```
#define RED 0
#define BLUE 1
#define GREEN 2
#define ID_COLOR_BUTTON 1001
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)
```

Můžete zahrnout další záhlaví jen pro čtení souborů pomocí **prostředek zahrnuje** příkazu, abyste určili #include příkaz jako druhou směrnici symbolů, jako:

```
#include "afxres.h"
#include "second.h"
```

Nový diagram vztahů souborů nyní vypadá takto:

```
    AFXRES.H
RESOURCE.H     SECOND.H
\       /
\     /
    MYAPP.RC
|
|
    RES\MYAPP.RC2
    AFXRES.RC
    AFXPRINT.RC
```

**Sdílení souboru hlaviček mezi dvěma. RC – soubory**

Chcete sdílení souboru hlaviček mezi dvěma. RC – soubory, které jsou v různých projektech, případně stejném projektu. Uděláte to tak, jednoduše použijte pouze techniku směrnic je popsáno výše na obě. Soubory RC. V případě, kdy dva. RC – soubory jsou určené pro různé aplikace (různé projekty), výsledek je znázorněn v následujícím diagramu:

```
    RESOURCE.H AFXRES.H   RESOURCE.H
(for MYAPP1) SECOND.H   (for MYAPP2)
\       /     \       /
\     /       \     /
    MYAPP1.RC MYAPP2.RC */    \        /     \ */      \      /       \
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2
    AFXPRINT.RC
```

Případ, kdy druhý soubor záhlaví je sdílen dvěma. RC – soubory ve stejné aplikaci (projektu), jsou popsány níže.

**Použití více souborů prostředků ve stejném projektu**

Visual C++ a kompilátor prostředků podporují více. RC – soubory ve stejném projektu prostřednictvím #include jednoho. RC souboru v jiném. Je povoleno vícenásobné vnoření. Existují různé důvody pro rozdělení zdrojů projektu do několika. RC – soubory:

- Je jednodušší spravovat velké množství prostředků mezi více členy projektového týmu, pokud rozdělíte prostředky do více. Soubory RC. Pokud používáte sady management package zdrojového ovládacího prvku pro rezervování souborů a vrácení změn, rozdělení prostředků do více. RC – soubory vám dá lepší kontrolu nad správou změn prostředků.

- Pokud chcete použít direktivy preprocesoru, například #ifdef, #endif, a #define, pro části prostředků, musíte je izolovat do prostředků jen pro čtení, které budou zkompilovány kompilátorem prostředku.

- Komponenta. RC – soubory se načtou a ukládat rychleji v aplikaci Visual C++ než jeden složený. Soubor RC.

- Pokud chcete spravovat zdroje pomocí textového editoru v čitelné formě, je třeba mít na. Soubor RC odděleně od jednoho úpravy Visual C++.

- Pokud potřebujete zachovat uživatelem definovaný zdroj v textové nebo binární formě, která je interpretovatelná pomocí jiného specializovaného editoru dat, pak byste jej zachovat v samostatném. Soubor RC, Visual C++ nezměnila formát šestnáctkových dat. Na. Prostředky souborů WAV (zvuk) v ukázce MFC Advanced Concepts [SPEAKN](../overview/visual-cpp-samples.md) jsou dobrým příkladem.

Můžete si #include sekundy. RC v směrnice času kompilace v dialogovém okně nastavení zahrnuje:

```
#include "res\myapp.rc2"  // non-Visual C++ edited resources
#include "second.rc"  // THE SECOND .RC FILE

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
```

Výsledek je znázorněn v následujícím diagramu:

```
RESOURCE.H     AFXRES.H
\       /
\     /
    MYAPP.RC
|
|
    RES\MYAPP.RC2
    SECOND.RC
    AFXRES.RC
    AFXPRINT.RC
```

Pomocí směrnice času kompilace můžete uspořádat Visual C++ upravitelné a neupravitelné prostředky do více. RC – soubory, kde "hlavní" MYAPP. Nemá žádný účinek, RC ale #include Další. Soubory RC. Pokud použijete projekt jazyka Visual C++. Soubor klíče k vícenásobné aktivaci a potom by měl obsahovat "hlavní". RC souboru v projektu tak, všechny # include 'D prostředky jsou kompilovány s vaší aplikací.

**Vynucení soubory vynutí neupravitelné Visual C++**

RES\MYAPP vytvořených pomocí AppWizard. Soubor RC2 je příkladem souboru, který obsahuje prostředky, které *není* mají náhodou načetly do Visual C++ a potom se zapsaly zpět se ztrátou informací o formátování. Abyste tomu předešli, vložte následující řádky na začátek RES\MYAPP. Soubor RC2:

```
#ifdef APSTUDIO_INVOKED
#error this file is not editable by Visual C++
#endif //APSTUDIO_INVOKED
```

Když Visual C++ kompiluje. Soubor RC definuje `APSTUDIO_INVOKED` stejně jako `RC_INVOKED`. Pokud struktura souborů vytvořených pomocí AppWizard je poškozena a Visual C++ načte řádek #error výše, ohlásí závažnou chybu a přerušení čtení. Soubor RC.

**Správa symbolů sdílených ve více Visual C++ upravit. RC – soubory**

Při rozdělení prostředků do více mohou vzniknout dva problémy. RC – soubory, které chcete v aplikaci Visual C++ upravit samostatně:

- Můžete chtít sdílet stejné symboly napříč více. Soubory RC.

- Je třeba pomoci Visual C++, nepřiřazujte stejné číselné hodnoty ID do různým zdrojům (symbolům).

Následující diagram znázorňuje uspořádání. RC a. H soubory, které se zabývá prvním problémem:

```
    MYAPP.RC */         \ */           \
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H
\    /    /      \   \    \
\  /    /        \   \    \
    MYSTRS.RC MYMENUS.RC
```

V tomto příkladu prostředky řetězců jsou uloženy v jednom souboru prostředku, MYSTRS. RC a nabídky jsou uloženy v jiném MYMENUS. RC. Některé symboly, například konkrétní příkazy, možná muset sdílet mezi dvěma soubory. Například ID_TOOLS_SPELL může být ID nabídky příkazu pro položku pravopisu v nabídce Nástroje; a může být také ID řetězce příkazového řádku zobrazeném rozhraním ve stavovém řádku hlavního okna aplikace.

ID_TOOLS_SPELL symbol je uchováván ve sdíleném souboru hlavičky, MYSHARED. H. Ručně udržovat tento sdílený soubor hlavičky v textovém editoru; Visual C++ neupravuje přímo ji. V prostředku dva soubory MYSTRS. RC a MYMENUS. Zadáte RC, #include MYSHARED. H ve směrnicích jen pro čtení pro Moje aplikace. RC, pomocí **prostředek zahrnuje** příkaz, jak je popsáno výše.

Je nejvhodnější pro předvídání symbolu, který bude sdílet dříve, než se pokusíte použít ho k identifikaci všech prostředků. Přidejte symbol do souboru sdíleného záhlaví a pokud nemáte # include 'D souboru sdíleného záhlaví ve směrnicích jen pro čtení pro. RC soubor, učiňte tak před použitím symbolu. Pokud jste nepředpokládali, sdílení symbolu tímto způsobem, pak budete muset ručně (pomocí textového editoru) přesunout # příkaz pro symbol z, Řekněme, že, MYMENUS define. H, abyste MYSHARED. H před jeho použitím v MYSTRS. RC.

Při správě symbolů ve více. RC – soubory, je také třeba pomoci Visual C++ nepřiřazujte stejné číselné hodnoty ID do různým zdrojům (symbolům). Pro všechny zadané. Soubor RC, Visual C++ postupně přiřadí ID do každé ze čtyř ID domén. Mezi úpravy relace, Visual C++ uchovává informace o posledním ID, které je přiřazeno ve všech doménách v souboru záhlaví symbolu pro. Soubor RC. Zde je, jaké hodnoty APS_NEXT jsou pro prázdný (Nový). Soubor RC:

```
#define _APS_NEXT_RESOURCE_VALUE  101
#define _APS_NEXT_COMMAND_VALUE   40001
#define _APS_NEXT_CONTROL_VALUE   1000
#define _APS_NEXT_SYMED_VALUE     101
```

`_APS_NEXT_RESOURCE_VALUE` je hodnota dalšího symbolu, který se použije pro prostředku dialogového okna, prostředku nabídky a tak dále. Platný rozsah hodnot symbolů prostředků je 1 – 0x6FFF.

`_APS_NEXT_COMMAND_VALUE` je hodnota dalšího symbolu, který se použije pro identifikaci příkazu. Platný rozsah hodnot symbolů příkazu je 0x8000 – 0xDFFF.

`_APS_NEXT_CONTROL_VALUE` je hodnota dalšího symbolu, který se použije pro ovládání dialogu. Platný rozsah hodnot symbolů ovládacích prvků dialogu je 8 – 0xDFFF.

`_APS_NEXT_SYMED_VALUE` je hodnota dalšího symbolu, který bude vydána, když ručně přiřadíte hodnotu symbolu pomocí příkazu Nový v prohlížeči symbolů.

Visual C++ začíná s mírně vyššími hodnoty, než nejnižší platná hodnotu při vytvoření nového. Soubor RC. AppWizard také inicializuje tyto hodnoty na jinou, vhodnější pro aplikace MFC. Další informace o rozsahu hodnot ID naleznete v tématu [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md).

Nyní pokaždé, když vytvoříte nový soubor prostředků, dokonce i ve stejném projektu, Visual C++ definuje stejné `_APS_NEXT_` hodnoty. To znamená, že pokud chcete přidat například více dialogů ve dvou různých. Soubory RC je vysoce pravděpodobné, který stejné #define hodnota bude přiřazena k jiným dialogům. Například IDD_MY_DLG1 v prvním. Soubor RC může být přiřazeno stejné číslo, 101, jako IDD_MY_DLG2 za sekundu. Soubor RC.

Abyste tomu předešli, měli byste rezervovat samostatný číselný rozsah pro každý ze čtyř domén ID v příslušné. Soubory RC. To můžete provést ruční aktualizaci `_APS_NEXT` hodnoty v jednotlivých. RC – soubory **před** začnete přidávat zdroje. Například pokud první. Soubor RC používá výchozí `_APS_NEXT` hodnoty, pak můžete přiřadit následující `_APS_NEXT` hodnoty na druhý. Soubor RC:

```
#define _APS_NEXT_RESOURCE_VALUE  2000
#define _APS_NEXT_COMMAND_VALUE   42000
#define _APS_NEXT_CONTROL_VALUE   2000
#define _APS_NEXT_SYMED_VALUE     2000
```

Samozřejmě je stále možné, že Visual C++ přiřadí tolik ID v prvním. RC soubor, který číselné hodnoty začnou překrývat, jsou vyhrazena pro druhý. Soubor RC. Měli byste rezervovat dostatečně velké rozsahy tak, aby se to nestalo.

**Správa závislostí mezi. VERZE RC. CPP, a. Soubory H**

Když Visual C++ uloží. Soubor RC ho také uloží změny symbolu do odpovídajícího zdroje. Soubor H. Některé z vašich. Souborů CPP, které odkazují na zdroje v. Soubor RC musí #include prostředku. Soubor H, obvykle v rámci hlavní hlavičkový soubor projektu. To vede k nežádoucím vedlejším účinkem z důvodu interní projekt management vývojové prostředí, která zdrojových souborech kontroluje závislost záhlaví. Pokaždé, když přidáte nový symbol v jazyce Visual C++, všechny. CPP souboru, který #include prostředků. H bude muset být překompilovány.

Visual C++ obchází závislost na prostředek. H zahrnutím následujícího komentáře jako první řádek zdroje. H souboru:

```
//{{NO_DEPENDENCIES}}
```

Vývojové prostředí interpretuje tento komentář ignorováním změn do prostředku. H tak závislé. Soubory CPP nebudou muset být překompilovány.

Vizuální C++ vždy přidá //{{NO_DEPENDENCIES}} komentář řádek, který. Soubor RC při uložení souboru. V některých případech obcházení závislosti sestavení na prostředku. H může vést k chybám za běhu v době spojení. Například pokud použijete prohlížeč symbolů ke změně číselné hodnoty přiřazené k symbolu pro prostředek, prostředek nebude správně nalezen a načten aplikace za běhu, jestliže. Soubor CPP vztahující se k prostředku není znovu zkompilován. V takovém případě by měly explicitně opětovné kompilaci žádné. Souborů CPP, o kterých víte jsou ovlivněny změnami v prostředku. H nebo vyberte **sestavit vše znovu**. Pokud potřebujete často měnit hodnoty symbolů pro určitou skupinu prostředků, pravděpodobně zjistíte ji pohodlnější a bezpečnější rozdělit tyto symboly do samostatného záhlaví jen pro čtení souboru, jak je popsáno výše v části [včetně Další souborů záhlaví](#_mfcnotes_tn035_including).

## <a name="_mfcnotes_tn035_set_includes"></a> Jak spravuje Visual C++ sada obsahuje informace o **

Jak je popsáno výše, sada obsahuje příkaz nabídky Soubor umožňuje určit tři typy informací:

- Hlavičkový soubor symbolů

- Směrnice souborů jen pro čtení

- Směrnice času kompilace

Následující text popisuje, jak Visual C++ udržuje tuto informaci v. Soubor RC. Není nutné tyto informace používat Visual C++, ale pochopíte to může vylepšit tak, aby větší jistotou používat funkci Set Includes.

Každý z výše uvedených tří typů informací Set Includes je uložen v. Soubor RC ve dvou formách: (1) jako #include nebo jiné směrnice interpretovatelné kompilátorem prostředku a (2) jako zvláštní prostředky TEXTINCLUDE interpretovatelné pouze pomocí Visual C++.

Účelem prostředku TEXTINCLUDE je bezpečně uložit informace sada ve formuláři, který je snadno prezentovatelný v jazyce Visual C++ **Set Includes** dialogové okno. TEXTINCLUDE je *typ prostředku* definovaný přes Visual C++. Visual C++ rozpoznává tři specifické prostředky TEXTINCLUDE, které mají identifikační čísla 1, 2 a 3 prostředků:

|ID prostředku TEXTINCLUDE|Typ informací Set Includes|
|-----------------------------|--------------------------------------|
|1|Hlavičkový soubor symbolů|
|2|Směrnice souborů jen pro čtení|
|3|Směrnice času kompilace|

Každý ze tří typů informací Set Includes je znázorněn ve výchozím nastavení MYAPP. RC a prostředků. H soubory vytvořeny pomoci AppWizard, jak je popsáno níže. Navíc \0 a "" tokeny mezi bloky BEGIN a END je potřeba syntaxí RC v uvedeném pořadí zadejte řetězců ukončených nulou a dvojitými uvozovkami.

## <a name="symbol-header-file"></a>Hlavičkový soubor symbolů

Forma informace souboru hlavičky symbolu interpretovány kompilátorem prostředku je jednoduše #include – příkaz:

```
#include "resource.h"
```

Odpovídající prostředek TEXTINCLUDE je:

```
1 TEXTINCLUDE DISCARDABLE
BEGIN
"resource.h\0"
END
```

## <a name="read-only-symbol-directives"></a>Směrnice souborů jen pro čtení

Direktivy symbolů jen pro čtení jsou zahrnuty v horní části MYAPP. RC ve tvaru interpretovatelném kompilátorem prostředku:

```
#include "afxres.h"
```

Odpovídající prostředek TEXTINCLUDE je:

```
2 TEXTINCLUDE DISCARDABLE
BEGIN
   "#include ""afxres.h""\r\n"
   "\0"
END
```

## <a name="compile-time-directives"></a>Směrnice času kompilace

Směrnice času kompilace jsou zahrnuty na konci MYAPP. RC ve tvaru interpretovatelném kompilátorem prostředku:

```
#ifndef APSTUDIO_INVOKED
///////////////////////
//
// From TEXTINCLUDE 3
//
#include "res\myapp.rc2"  // non-Visual C++ edited resources

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
#endif  // not APSTUDIO_INVOKED
```

Direktiva #ifndef APSTUDIO_INVOKED instruuje Visual C++ mají přeskočit kompilační direktivy.

Odpovídající prostředek TEXTINCLUDE je:

```
3 TEXTINCLUDE DISCARDABLE
BEGIN
"#include ""res\myapp.rc2""  // non-Visual C++ edited resources\r\n"
"\r\n"
"#include ""afxres.rc""  // Standard components\r\n"
"#include ""afxprint.rc""  // printing/print preview resources\r\n"
"\0"
END
```

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
