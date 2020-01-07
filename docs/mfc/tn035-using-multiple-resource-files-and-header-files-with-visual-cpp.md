---
title: 'TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyku Visual C++'
ms.date: 11/04/2016
f1_keywords:
- vc.resources
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
ms.openlocfilehash: 23d4fdeb82ed7eea97a104e111cd022a87626df4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302169"
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyku Visual C++

> [!NOTE]
> Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

Tato poznámka popisuje, jak editor C++ vizuálních prostředků podporuje více souborů prostředků a hlavičkových souborů, které jsou sdíleny v jednom projektu nebo sdíleny v rámci více projektů, a způsob využití této podpory. Tato poznámka obsahuje odpovědi na tyto otázky:

- Kdy může být projekt rozdělen do více souborů prostředků nebo hlavičkových souborů a jak to uděláte

- Jak sdílíte společnou hlavičku. Soubor H mezi dvěma. Soubory RC

- Jak rozdělit prostředky projektu na násobek. Soubory RC

- Jak vy (a nástroje) spravujete závislosti mezi sestaveními. RC,. CPP a. Soubory H

Měli byste si uvědomit, že pokud přidáte další soubor prostředků do projektu, ClassWizard nebude rozpoznat prostředky v přidaném souboru.

Tato poznámka je strukturováná na zodpovězení výše uvedených otázek takto:

- **Přehled způsobu, jakým C++ vizuál spravuje soubory prostředků a hlavičkové soubory,** nabízí přehled o tom, jak sada prostředků obsahuje příkaz v vizuálu C++ umožňuje použít v jednom projektu více souborů prostředků a hlavičkových souborů.

- **Analýza AppWizard – vytvořena. RC a. Soubory H** vypadají v souboru s více prostředky a hlavičkou, které používá aplikace vytvořená v AppWizard. Tyto soubory slouží jako dobrý model pro další soubory prostředků a hlavičkové soubory, které byste mohli chtít přidat do projektu.

- **Včetně dalších hlavičkových souborů** popisuje, kde můžete chtít zahrnout více hlavičkových souborů, a poskytuje podrobné informace o tom, jak to provést.

- **Sdílení souboru hlaviček mezi dvěma. Soubory RC** ukazují, jak lze sdílet jeden hlavičkový soubor mezi několika. Soubory RC v různých projektech, případně ve stejném projektu.

- **Použití více souborů prostředků ve stejném projektu** popisuje, kde můžete chtít rozdělit projekt do více. Soubory RC a poskytuje podrobné informace o tom, jak to udělat.

- **Vynucování vizuálních C++ souborů bez úprav** popisuje, jak můžete zajistit, aby C++ vizuál neupravil ani neúmyslně přeformátoval vlastní prostředek.

- **Správa symbolů sdílených více vizuálními C++úpravami. Soubory RC** popisují, jak sdílet stejné symboly napříč více. Soubory RC a jak se vyhnout přiřazování duplicitních číselných hodnot ID.

- **Správa závislostí mezi. RC,. CPP a. Soubory H** popisují, jak C++ si vizuál vyloučí zbytečné opětovné kompilování. Soubory CPP, které jsou závislé na souborech symbolů prostředků.

- **Jak vizuál C++ spravuje sadu** , obsahuje informace o technických podrobnostech o C++ tom, jak vizuální sleduje více (vnořené). Soubory RC a více hlavičkových souborů, které jsou #include. Soubor RC

## <a name="overview-of-how-visual-c-manages-resource-files-and-header-files"></a>Přehled způsobu, jakým Visual C++ spravuje soubory prostředků a soubory hlaviček

Vizuál C++ spravuje jednu. Soubor prostředků RC a odpovídající. Soubor hlaviček H jako úzce spárované dvojice souborů Když upravujete a ukládáte prostředky v. RC soubor, nepřímo upravíte a uložíte symboly v odpovídajících. Soubor H. I když můžete otevřít a upravit více. Soubory RC (pomocí uživatelského rozhraní MDI jazyka C++Visual) pro všechny dané. Soubor RC nepřímo upravuje přesně jeden odpovídající hlavičkový soubor.

### <a name="symbol-header-file"></a>Soubor hlaviček symbolu

Ve výchozím nastavení má C++ Visual vždy název odpovídajícího prostředku hlavičkového souboru. H bez ohledu na název souboru prostředků (například MYAPP. RC). Pomocí příkazu **prostředek obsahuje** v nabídce **zobrazení** v vizuálu C++můžete změnit název tohoto souboru hlaviček aktualizací souboru hlaviček symbolu v dialogovém okně **sada obsahuje** .

### <a name="read-only-symbol-directives"></a>Direktivy symbolů jen pro čtení

I když C++ vizuální upraví jenom jeden hlavičkový soubor pro každé z nich. Soubor RC, vizuál C++ podporuje odkazy na symboly definované v dalších souborech hlaviček jen pro čtení. Pomocí příkazu **prostředek obsahuje** v nabídce **zobrazení** v vizuálu C++můžete zadat libovolný počet dalších souborů hlaviček jen pro čtení jako direktivy symbolů jen pro čtení. Omezení jen pro čtení znamená, že při přidání nového prostředku do nástroje. RC soubor můžete použít symbol definovaný v souboru hlaviček jen pro čtení; Pokud ale prostředek odstraníte, symbol pořád zůstane definovaný v souboru hlaviček jen pro čtení. Číselnou hodnotu přiřazenou k symbolu jen pro čtení nemůžete změnit.

### <a name="compile-time-directives"></a>Direktivy při kompilaci

Vizuál C++ také podporuje vnořování souborů prostředků, kde jeden. Soubor RC je #include v rámci jiného. Při úpravě daného. Soubor RC s použitím C++vizuálu, žádné prostředky v souborech #include 's nejsou viditelné. Ale při kompilaci. Soubor RC, jsou také zkompilovány soubory #include 's. Pomocí příkazu **prostředek obsahuje** v nabídce **zobrazení** v vizuálu C++můžete zadat libovolný počet #include. Soubory RC jako direktivy v době kompilace.

Všimněte si, co se stane, když C++ si přečtete Visual a. Soubor RC, který #include jiný. Soubor RC, který *není zadán jako* direktiva v době kompilace. Tato situace může nastat při převedení do vizuálu C++ . Soubor RC, který jste předtím zachovali ručně pomocí textového editoru. Když vizuální C++ přečte #include. RC soubor, sloučí #include zdrojů do nadřazené položky. Soubor RC Při uložení nadřazeného objektu. Soubor RC, platný příkaz #include, bude nahrazen prostředky #include 's. Pokud nechcete, aby k tomuto sloučení docházelo, odeberte příkaz #include z nadřazeného objektu. Soubor RC *před* jeho načtením do C++vizuálu; pak pomocí vizuálu C++přidejte zpátky stejný příkaz #include jako direktivu pro kompilaci.

Vizuální C++ uložení v. RC soubor obsahuje tři druhy výše uvedeného seznamu včetně informací (soubor hlaviček symbolu, direktivy symbolů jen pro čtení a direktivy pro čas kompilace) v direktivách #include *a* v prostředcích TEXTINCLUDE. Prostředky TEXTINCLUDE, podrobnosti implementace, které obvykle nemusíte řešit, jsou vysvětleny ve [způsobu, jakým vizuál C++ spravuje sadu obsahuje informace](#_mfcnotes_tn035_set_includes).

## <a name="analysis-of-appwizard-created-rc-and-h-files"></a>Analýza AppWizard – vytvořena. RC a. Soubory H

Zkoumání kódu aplikace vytvořeného pomocí AppWizard poskytuje přehled o tom, C++ jak vizuál spravuje více souborů prostředků a hlavičkových souborů. Výňatky kódu zkoumané níže jsou z aplikace MYAPP vytvořené pomocí AppWizard s použitím výchozích možností.

Aplikace vytvořená AppWizard používá více souborů prostředků a více hlavičkových souborů, které jsou shrnuté v následujícím diagramu:

```Diagram
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

Tyto vztahy mezi soubory můžete zobrazit pomocí příkazu Visual C++ File/set includes.

MyApp. RC
Soubor prostředků aplikace, který upravujete pomocí vizuálu C++.

Partner. H je soubor hlaviček specifický pro aplikaci. Vždy se nazývá prostředek. H od AppWizard je konzistentní s výchozím C++pojmenovávání souboru hlaviček ve vizuálu. #Include pro tento hlavičkový soubor je prvním příkazem v souboru prostředků (MYAPP. RC):

```rc
//Microsoft Visual C++ generated resource script
//
#include "resource.h"
```

RES\MYAPP. RC2
Obsahuje prostředky, které nebudou upravovány pomocí vizuálu C++ , ale budou zahrnuty do finální kompilace. Soubor EXE. AppWizard ve výchozím nastavení nevytváří žádné takové prostředky, C++ protože vizuál může upravovat všechny standardní prostředky včetně prostředku verze (nová funkce v této verzi). AppWizard vygeneruje prázdný soubor pro případ, že chcete do tohoto souboru přidat vlastní formátované prostředky.

Pokud používáte vlastní formátované prostředky, můžete je přidat do RES\MYAPP. RC2 a upravte je pomocí vizuálního C++ textového editoru.

Afxres. RC a AFXPRINT. RC obsahuje standardní prostředky vyžadované některými funkcemi rozhraní. Podobně jako RES\MYAPP. RC2 tyto dva soubory prostředků poskytované rozhraním jsou #include 'd na konci MYAPP. RC a jsou zadány v direktivách doby kompilace dialogového okna set includes. Proto při úpravách MYAPP nebudete tyto prostředky rozhraní přímo zobrazovat ani upravovat. RC ve vizuálu C++, ale jsou zkompilovány do binárního souboru aplikace. Soubor RES a finální. Soubor EXE. Další informace o standardních zdrojích rozhraní, včetně postupů pro jejich úpravu, najdete v části [technická Poznámka 23](../mfc/tn023-standard-mfc-resources.md).

Afxres. H definuje standardní symboly, například `ID_FILE_NEW`, používané rozhraním a konkrétně použitou v AFXRES. RC. Afxres. H taky #include WINRES. H, který obsahuje podmnožinu oken. H, které jsou vyžadovány C++ vizuálním vygenerováním. Soubory RC a také AFXRES. RC. Symboly definované v AFXRES. H je k dispozici při úpravách souboru prostředků aplikace (MYAPP. RC). Například `ID_FILE_NEW` se používá pro položku nabídky soubor nový v MYAPP. Prostředek nabídky RC Tyto symboly definované v rozhraní nemůžete změnit ani odstranit.

## <a name="_mfcnotes_tn035_including"></a>Včetně dalších hlavičkových souborů

Aplikace vytvořená v AppWizard zahrnuje pouze dva hlavičkové soubory: prostředek. H a AFXRES. Y. Pouze prostředek. H je specifická pro aplikaci. Je možné, že budete muset zahrnout další soubory hlaviček jen pro čtení v následujících případech:

Hlavičkový soubor je poskytován externím zdrojem nebo chcete soubor hlaviček sdílet mezi více projekty nebo více částmi stejného projektu.

Hlavičkový soubor má formátování a komentáře, které nechcete, aby C++ vizuál změnil nebo odfiltroval při uložení souboru. Například můžete chtít zachovat #define, který používá symbolické aritmetické operace jako:

```h
#define RED 0
#define BLUE 1
#define GREEN 2
#define ID_COLOR_BUTTON 1001
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)
```

Můžete zahrnout další soubory hlaviček jen pro čtení pomocí příkazu **prostředků include** k určení #include příkazu jako druhé direktivy se symboly jen pro čtení, jako v:

```rc
#include "afxres.h"
#include "second.h"
```

Nový diagram relací souborů teď vypadá takto:

```Diagram
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

## <a name="sharing-a-header-file-between-two-rc-files"></a>Sdílení souboru hlaviček mezi dvěma. Soubory RC

Můžete chtít sdílet hlavičkový soubor mezi dvěma. Soubory RC, které jsou v různých projektech, nebo pravděpodobně stejný projekt. Uděláte to tak, že jednoduše použijete techniku direktiv jen pro čtení popsanou výše na obě. Soubory RC. V případě dvou. Soubory RC jsou pro různé aplikace (různé projekty), výsledek je znázorněn v následujícím diagramu:

```Diagram
     RESOURCE.H   AFXRES.H   RESOURCE.H  
    (for MYAPP1)  SECOND.H   (for MYAPP2)
          \       /     \       /
           \     /       \     /
          MYAPP1.RC      MYAPP2.RC
           /    \        /     \
          /      \      /       \
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2
                AFXPRINT.RC
```

Případ, kdy je druhý soubor hlaviček sdílen dvěma. Soubory RC ve stejné aplikaci (projektu) jsou popsány níže.

## <a name="using-multiple-resource-files-in-the-same-project"></a>Použití více souborů prostředků ve stejném projektu

Vizuál C++ a kompilátor prostředků podporují víc. RC soubory ve stejném projektu prostřednictvím #include. Soubor RC v jiném. Je povoleno vícenásobné vnoření. Existují různé důvody pro rozdělení prostředků projektu do více. Soubory RC:

- Je snazší spravovat velký počet prostředků mezi více členy projektového týmu, pokud rozdělíte prostředky na více. Soubory RC. Použijete-li balíček správy zdrojového kódu pro rezervaci souborů a vrácení změn se změnami, rozdělení prostředků na více. Soubory RC vám poskytnou lepší kontrolu nad správou změn prostředků.

- Pokud chcete použít direktivy preprocesoru, například #ifdef, #endif a #define, pro části vašich prostředků je nutné je izolovat v prostředcích jen pro čtení, které budou kompilovány kompilátorem prostředků.

- Část. Soubory RC budou načteny a ukládány rychleji ve C++ vizuálu než v jednom složeném. Soubor RC

- Pokud chcete zachovat prostředek pomocí textového editoru v uživatelsky čitelné podobě, měli byste ho uchovávat v. Soubor RC oddělený od různých úprav C++ vizuálů.

- Pokud potřebujete zachovat uživatelem definovaný prostředek v binárním nebo textovém formuláři, který je interpretované jiným specializovaným editorem dat, měli byste ho uchovávat samostatně. Soubor RC, takže C++ vizuál nemění formát na hexadecimální data. Okně. Dobrým příkladem jsou zdroje souborů WAV (zvuk) v části MFC Advanced Konceptys Sample [SPEAKN](../overview/visual-cpp-samples.md) .

Můžete #include sekundu. RC v direktivách doby kompilace v dialogovém okně Sada obsahuje:

```h
#include "res\myapp.rc2"  // non-Visual C++ edited resources
#include "second.rc"  // THE SECOND .RC FILE

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
```

Výsledek je znázorněn v následujícím diagramu:

```Diagram
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

Pomocí direktiv při kompilaci můžete uspořádat vizuální C++a neupravitelné prostředky do více. RC soubory, kde "hlavní" Mojeapl. RC nedělá nic, ale #include druhé. Soubory RC. Pokud používáte projekt sady Visual Studio C++ . Klíč k vícenásobné aktivaci, pak byste měli zahrnout "hlavní". Soubor RC v projektu tak, aby všechny prostředky #includea byly kompilovány s vaší aplikací.

## <a name="enforcement-of-noneditable-visual-c-files"></a>Vynucování neupravitelných vizuálních C++ souborů

AppWizard vytvořené RES\MYAPP. Soubor RC2 je příkladem souboru, který obsahuje prostředky, které *nechcete* omylem přečíst do vizuálu C++ , a pak ho zapište zpět se ztrátou informací o formátování. Pokud to chcete chránit, umístěte na začátek RES\MYAPP. následující řádky. Soubor RC2:

```rc2
#ifdef APSTUDIO_INVOKED
    #error this file is not editable by Visual C++
#endif //APSTUDIO_INVOKED
```

Když vizuál C++ zkompiluje. Soubor RC, definuje `APSTUDIO_INVOKED` a také `RC_INVOKED`. Pokud je struktura souboru vytvořená AppWizard poškozená a Visual C++ přečte #error řádek výše, oznamuje závažnou chybu a přeruší čtení. Soubor RC

## <a name="managing-symbols-shared-by-multiple-visual-c-edited-rc-files"></a>Správa symbolů sdílených více vizuálními C++úpravami. Soubory RC

Při rozdělení prostředků do více se vyskytnou dva problémy. Soubory RC, které chcete upravit samostatně v jazyce Visual C++:

- Je možné, že budete chtít stejné symboly sdílet mezi několika. Soubory RC.

- Je potřeba, aby vizuál C++ nepřiřadil stejné číselné hodnoty ID k různým prostředkům (symbolům).

Následující diagram znázorňuje organizaci. RC a. H soubory, které se dodávají s prvním problémem:

```Diagram
              MYAPP.RC
             /         \
            /           \
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H
     \    /    /      \   \    \
      \  /    /        \   \    \
      MYSTRS.RC         MYMENUS.RC
```

V tomto příkladu jsou prostředky řetězců uchovávány v jednom souboru prostředků, MYSTRS. RC a nabídky jsou uloženy v jiném, MYMENUS. RC. Některé symboly, například příkazy pro, mohou být nutné sdílet mezi dvěma soubory. ID_TOOLS_SPELL může být například ID příkazu nabídky pro položku pravopisu v nabídce nástroje. a může to být také ID řetězce příkazového řádku zobrazeného v rámci rozhraní ve stavovém řádku hlavního okna aplikace.

Symbol ID_TOOLS_SPELL je uložen ve sdíleném hlavičkovém souboru MYSHARED. Y. Tento sdílený hlavičkový soubor se udržuje ručně pomocí textového editoru. Vizuál C++ ho přímo neupraví. Ve dvou souborech prostředků MYSTRS. RC a MYMENUS. RC zadáte #include MYSHARED. H ve směrnicích jen pro čtení pro MYAPP. RC pomocí příkazu **prostředek obsahuje** , jak je popsáno výše.

Je nejvhodnější pro předvídání symbolu, který budete sdílet předtím, než se pokusíte použít k identifikaci libovolného prostředku. Přidejte symbol do sdíleného hlavičkového souboru a pokud jste ještě ne#includei, je soubor s sdíleným hlavičkou ve směrnicích jen pro čtení pro. Soubor RC, udělejte to před použitím symbolu. Pokud jste nepředpokládali sdílení symbolu tímto způsobem, budete muset ručně (pomocí textového editoru) přesunout příkaz #define pro symbol z výrazu, řekněme, MYMENUS. H až MYSHARED. H před použitím v MYSTRS. RC.

Když spravujete symboly v násobcích. Soubory RC, je také nutné pomáhat vizuálním C++ vyhnout se tomu, aby se stejné číselné hodnoty ID přiřadily k odlišným prostředkům (symbolům). Pro všechny dané. Soubor RC, vizuální C++ přírůstkově přiřadí ID v každé ze čtyř domén ID. Mezi relacemi při úpravách vizuálu C++ sleduje poslední ID, které bylo přiřazeno v každé doméně v souboru hlaviček symbolu pro. Soubor RC Tady je APS_NEXT hodnoty pro prázdné (nové). Soubor RC:

```rc
#define _APS_NEXT_RESOURCE_VALUE  101
#define _APS_NEXT_COMMAND_VALUE   40001
#define _APS_NEXT_CONTROL_VALUE   1000
#define _APS_NEXT_SYMED_VALUE     101
```

`_APS_NEXT_RESOURCE_VALUE` je další hodnota symbolu, která bude použita pro prostředek dialogového okna, prostředek nabídky a tak dále. Platný rozsah pro hodnoty symbolu prostředku je 1 až 0x6FFF.

`_APS_NEXT_COMMAND_VALUE` je další hodnota symbolu, která bude použita pro identifikaci příkazu. Platný rozsah pro hodnoty symbolů příkazu je 0x8000 na 0xDFFF.

`_APS_NEXT_CONTROL_VALUE` je další hodnota symbolu, která bude použita pro ovládací prvek dialogového okna. Platný rozsah pro hodnoty symbolů ovládacího prvku dialogu je 8 až 0xDFFF.

`_APS_NEXT_SYMED_VALUE` je další hodnota symbolu, která bude vyvolána, když ručně přiřadíte hodnotu symbolu pomocí příkazu nový v prohlížeči symbolů.

Vizuál C++ začíná mírně vyššími hodnotami, které mají nejnižší právní hodnotu při vytváření nového. Soubor RC AppWizard také inicializuje tyto hodnoty na něco vhodnějšího pro aplikace MFC. Další informace o rozsahu hodnot ID najdete v části [technická Poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md).

Nyní při každém vytvoření nového souboru prostředků, a to i ve stejném projektu, definuje vizuál C++ stejné `_APS_NEXT_` hodnoty. To znamená, že pokud přidáte například více dialogů ve dvou různých dialogových oknech. Soubory RC, je velmi pravděpodobnější, že se k různým dialogům přiřadí stejná #define hodnota. Například IDD_MY_DLG1 v prvním. Souboru RC může být přiřazeno stejné číslo, 101, jako IDD_MY_DLG2 za sekundu. Soubor RC

Abyste tomu předešli, měli byste rezervovat samostatný číselný rozsah pro každou ze čtyř domén ID v příslušné. Soubory RC. Provedete to tak, že ručně aktualizujete `_APS_NEXT` hodnoty v každé z. Soubory RC **před** zahájením přidávání prostředků Například, pokud první. Soubor RC používá výchozí hodnoty `_APS_NEXT` a potom můžete chtít přiřadit následující hodnoty `_APS_NEXT` druhému. Soubor RC:

```rc
#define _APS_NEXT_RESOURCE_VALUE  2000
#define _APS_NEXT_COMMAND_VALUE   42000
#define _APS_NEXT_CONTROL_VALUE   2000
#define _APS_NEXT_SYMED_VALUE     2000
```

Samozřejmě je stále možné, že vizuál C++ přiřadí tolik ID v prvním. Soubor RC, který začíná překrývat hodnoty, které jsou vyhrazeny pro druhý. Soubor RC Měli byste vyhradit dostatečně velké rozsahy, aby k tomu nedocházelo.

## <a name="managing-dependencies-between-rc-cpp-and-h-files"></a>Správa závislostí mezi. RC,. CPP a. Soubory H

Když vizuální C++ uloží. Soubor RC, také ukládá změny symbolu do odpovídajícího prostředku. Soubor H. Jakékoli z vašich. Soubory CPP, které odkazují na prostředky v. Soubor RC musí #include prostředku. Soubor H, obvykle v rámci hlavičkového souboru hlavního projektu. To vede k nežádoucímu vedlejšímu účinku z důvodu interní správy projektů ve vývojovém prostředí, které prohledává zdrojové soubory pro závislosti hlaviček. Pokaždé, když přidáte nový symbol do vizuálu C++, vše. Soubory CPP, které #include prostředku H by musel být znovu zkompilován.

Vizuál C++, obejít závislost na prostředku. H zahrnutím následujícího komentáře jako prvního řádku prostředku. Soubor H:

```h
//{{NO_DEPENDENCIES}}
```

Vývojové prostředí tento komentář interpretuje tak, že se změny v prostředku ignorují. H tak, aby byl závislý. Soubory CPP nebude nutné znovu kompilovat.

Vizuál C++ vždy přidá řádek komentáře//{{NO_DEPENDENCIES}} do. Soubor RC při uložení souboru V některých případech obejití závislosti sestavení v prostředku. H může vést k nezjištěným chybám za běhu v době propojování. Například pokud použijete Prohlížeč symbolů ke změně číselné hodnoty přiřazené k symbolu prostředku, prostředek nebude správně nalezen a načten v době běhu aplikace, pokud. Soubor CPP odkazující na prostředek není znovu zkompilován. V takových případech byste měli všechny explicitně kompilovat. Soubory CPP, na které víte, jsou ovlivněny změnami symbolů v prostředku. H nebo vyberte **znovu sestavit vše**. Pokud budete potřebovat často měnit hodnoty symbolů pro určitou skupinu prostředků, pravděpodobně bude lepší a bezpečnější, aby tyto symboly byly rozděleny do samostatného souboru hlaviček jen pro čtení, jak je popsáno v předchozí části, [včetně dalších hlavičkových souborů](#_mfcnotes_tn035_including).

## <a name="_mfcnotes_tn035_set_includes"></a>Jak vizuální C++ sada spravuje sadu obsahuje informace

Jak je popsáno výše, příkaz, který obsahuje nabídku soubor, umožňuje zadat tři typy informací:

- Soubor hlaviček symbolu

- Direktivy symbolů jen pro čtení

- Direktivy při kompilaci

Následující článek popisuje, jak C++ vizuál udržuje tyto informace v. Soubor RC Tyto informace nepotřebujete, abyste mohli používat C++vizuál, ale můžou zlepšit porozumění, abyste mohli lépe používat funkci set includes.

Každý z výše uvedených tří typů sady obsahuje informace jsou uloženy v. Soubor RC ve dvou formách: (1) jako #include nebo jiné direktivy interpretované kompilátorem prostředků a (2) jako speciální prostředky TEXTINCLUDE, které lze interpretovat C++pouze pomocí vizuálu.

Účelem prostředku TEXTINCLUDE je bezpečné uložení sady, která obsahuje informace ve formuláři, který je možné snadno předběžně odeslat v dialogovém okně C++ **sada** vizuálů. TEXTINCLUDE je *typ prostředku* definovaný pomocí vizuálu C++. Vizuál C++ rozpoznává tři konkrétní TEXTINCLUDE prostředky s identifikačními čísly prostředků 1, 2 a 3:

|ID prostředku TEXTINCLUDE|Typ sady obsahuje informace|
|-----------------------------|--------------------------------------|
|1|Soubor hlaviček symbolu|
|2|Direktivy symbolů jen pro čtení|
|3|Direktivy při kompilaci|

Každý ze tří typů sady obsahuje informace, které jsou znázorněny ve výchozím formuláři MYAPP. RC a RESOURCE. Soubory H vytvořené nástrojem AppWizard, jak je popsáno níže. Syntaxe RC vyžaduje tokeny extra \ 0 a "" mezi ZAČÁTKem a KONCOVými bloky pro zadání nulových ukončených řetězců a znaku dvojité uvozovky.

### <a name="symbol-header-file"></a>Soubor hlaviček symbolu

Forma informací souboru hlaviček symbolu, která je interpretována kompilátorem prostředků, je jednoduše příkaz #include:

```rc
#include "resource.h"
```

Odpovídající prostředek TEXTINCLUDE je:

```rc
1 TEXTINCLUDE DISCARDABLE
BEGIN
    "resource.h\0"
END
```

### <a name="read-only-symbol-directives"></a>Direktivy symbolů jen pro čtení

Direktivy symbolů jen pro čtení jsou obsaženy v horní části MYAPP. RC v následujícím formuláři, který je interpretován kompilátorem prostředku:

```rc
#include "afxres.h"
```

Odpovídající prostředek TEXTINCLUDE je:

```rc
2 TEXTINCLUDE DISCARDABLE
BEGIN
   "#include ""afxres.h""\r\n"
   "\0"
END
```

### <a name="compile-time-directives"></a>Direktivy při kompilaci

Direktivy doby kompilace jsou zahrnuty na konci MYAPP. RC v následujícím formuláři, který je interpretován kompilátorem prostředku:

```rc
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

Direktiva #ifndef APSTUDIO_INVOKED instruuje vizuál C++ , aby se přeskočily na direktivy v době kompilace.

Odpovídající prostředek TEXTINCLUDE je:

```rc
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

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)\
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
