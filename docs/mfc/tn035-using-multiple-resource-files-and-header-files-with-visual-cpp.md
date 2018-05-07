---
title: 'TN035: Použití více zdrojových souborů a hlavičkových souborů pomocí aplikace Visual C++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.resources
dev_langs:
- C++
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c374e0d14375450533326be5fd406fe8147e475a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyku Visual C++
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje, jak editoru prostředků Visual C++ podporuje více prostředků souborů a hlavičkových souborů sdílených v jediném projektu nebo sdílet mezi více projektů a jak můžete využít výhod podporující. Tato poznámka odpoví na tyto otázky:  
  
-   Když může chcete rozdělit do více zdrojových souborů a hlavičkových souborů projektu a jak se  
  
-   Jak budete sdílet společné hlavičky. H soubor mezi dvěma. RC – soubory  
  
-   Jak můžete rozdělit projektu prostředky do více. RC – soubory  
  
-   Jak vám (a nástroje) spravovat sestavení závislosti mezi. RC. CPP, a. Soubory H  
  
 Je třeba si uvědomit, že pokud přidáte do projektu soubor dalších prostředků, ClassWizard nerozpozná prostředky v přidaný soubor.  
  
 Tato poznámka strukturovaná odpovězte na výše uvedené otázky následujícím způsobem:  
  
- **Přehled o tom, jak Visual C++ spravuje zdrojových souborů a hlavičkových souborů** poskytuje přehled o tom, jak nastavit prostředek zahrnuje příkaz v jazyce Visual C++ vám umožní používat více zdrojových souborů a hlavičkových souborů v rámci jednoho projektu.  
  
- **Analýza vytvořené objekty AppWizard. RC a. Soubory H** zjistí více prostředků a hlavičky souborů, které používají aplikace vytvořené objekty AppWizard. Tyto soubory sloužit jako model dobrý pro další zdrojových souborů a hlavičkových souborů, které chcete přidat do projektu.  
  
- **Včetně další soubory hlaviček** popisuje, kde můžete chtít zadat více hlavičky souborů a poskytuje podrobnosti o tom, jak to provést.  
  
- **Sdílení souboru záhlaví mezi dvěma. Soubory RC** ukazuje, jak můžete sdílet jeden soubor hlaviček mezi několika. RC – soubory v různých projektů nebo možná ve stejném projektu.  
  
- **Použití více souborů prostředků ve stejném projektu** popisuje, kde můžete chtít rozdělit do několika projektu. RC soubory a poskytuje podrobnosti o tom, jak to provést.  
  
- **Vynucení Non-upravovat soubory Visual C++** popisuje, jak můžete zkontrolovat, Visual C++ nepodporuje upravit a náhodně přeformátujte vlastní prostředek.  
  
- **Správa symboly, které jsou sdíleny více Visual C++ upravit. Soubory RC** popisuje, jak sdílet stejný symboly napříč více. RC – soubory a jak se vyhnout přiřazení duplicitní ID číselné hodnoty.  
  
- **Správa závislostí mezi. RC. CPP, a. Soubory H** popisuje, jak Visual C++ zabraňuje zbytečným rekompilace. CPP souborů, které jsou závislé na soubory symbolů prostředků.  
  
- **Jak Visual C++ spravuje zahrnuje informací o sadě** obsahuje technické informace o tom, jak Visual C++ uchovává informace o více (vnořená). RC – soubory a více hlavičkových souborů, které jsou #include'd pomocí. RC soubor.  
  
 **Přehled o tom, jak Visual C++ spravuje zdrojových souborů a soubory hlaviček**  
  
 Visual C++ spravuje jeden. Soubor RC zdrojů a odpovídající. Soubor hlaviček H jako dvojice úzce párované souborů. Když je upravovat a ukládat prostředky v. RC soubor nepřímo upravíte a uložit do odpovídajícího symboly. Soubor H. I když můžete otevřít a upravit více. RC – soubory v čase (pomocí uživatelského rozhraní MDI Visual C++) pro všechny zadané. RC soubor nepřímo upravit přesně jeden odpovídající soubor hlaviček.  
  
 **Soubor hlaviček symbolů**  
  
 Ve výchozím nastavení Visual C++ vždy názvy odpovídající soubor hlaviček prostředků. H, bez ohledu na název souboru prostředků (například Moje aplikace. RC). Pomocí **prostředek zahrnuje** příkaz z **zobrazení** nabídky v jazyce Visual C++, můžete změnit název tohoto souboru záhlaví při aktualizaci souboru Symbol hlavičkový soubor v **nastavit zahrnuje**dialogové okno.  
  
 **Směrnice pro symboly jen pro čtení**  
  
 I když Visual C++ pouze upraví jeden soubor hlavičky pro všechny zadané. RC soubor, Visual C++ podporuje odkazy na symboly definované v souborech další záhlaví jen pro čtení. Pomocí **prostředek zahrnuje** příkaz **zobrazení** nabídky v jazyce Visual C++, můžete zadat libovolný počet dalších jen pro čtení hlavičkových souborů jako směrnice pro symboly pouze pro čtení. Omezení "jen pro čtení" znamená, že při přidání nového prostředku v. RC soubor, můžete použít symbol definované v souboru jen pro čtení hlavičku. ale pokud odstraníte prostředek, symbol stále zůstává definované v souboru jen pro čtení hlavičku. Číselná hodnota přiřazená k symbol jen pro čtení nelze změnit.  
  
 **Direktivy kompilace**  
  
 Visual C++ také podporuje vnoření soubory prostředků, kde jeden. RC soubor #include'd v rámci jiného. Při úpravách danou. RC soubor pomocí Visual C++, všechny prostředky v #include'd soubory nejsou viditelné. Když zkompilujete, ale. RC soubor #include'd soubory také kompilaci. Pomocí **prostředek zahrnuje** příkaz **zobrazení** nabídky v jazyce Visual C++, můžete zadat libovolný počet #include'd. RC – soubory jako kompilaci direktivy.  
  
 Všimněte si, co se stane, pokud jste pro čtení do Visual C++. RC soubor, který #include elementu jiného. RC soubor, který je *není* zadaný jako direktivu kompilaci. Tato situace může dojít, když použijete pro aplikaci Visual C++. RC soubor, který jste měli byla dříve zachování ručně pomocí textového editoru. Když Visual C++ přečte #include'd. RC soubor sloučí #include'd prostředky do nadřazené. RC soubor. Při ukládání nadřazený. RC soubor #include efekt příkazu, budou nahrazeny #include'd prostředky. Pokud nechcete, aby tento sloučení provést, byste měli odebrat #include příkaz z nadřazeného objektu. RC soubor *předchozí* pro čtení do Visual C++; potom pomocí Visual C++, přidat zpět stejné #include příkaz jako direktivu kompilaci.  
  
 Visual C++ se uloží do. RC soubor tři druhy výše uvedených nastavení zahrnuje informace (Symbol soubor hlaviček, směrnice pro symboly pouze pro čtení a kompilaci direktivy) v # direktivy include *a* v TEXTINCLUDE prostředky. TEXTINCLUDE prostředky, implementaci podrobností, která obvykle nepotřebujete k řešení, jsou vysvětlené v [jak Visual C++ spravuje nastavit zahrnuje informace](#_mfcnotes_tn035_set_includes).  
  
 **Analýza vytvořené objekty AppWizard. RC a. Soubory H**  
  
 Zkoumání kódu aplikace vyprodukované objekty AppWizard poskytuje přehled o tom, jak Visual C++ spravuje více zdrojových souborů a hlavičkových souborů. Úryvky kód zkontrolován níže jsou z aplikace MYAPP vyprodukované objekty AppWizard použití výchozích možností.  
  
 Aplikace vytvořené objekty AppWizard používá více souborů prostředků a několik hlavičkových souborů, popsané v následujícím diagramu:  
  
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
  
 Můžete zobrazit tyto více vztahů souboru pomocí příkazu zahrnuje soubor Visual C++ nebo nastavení.  
  
 MOJE APLIKACE. RC  
 Soubor prostředků aplikace, který můžete upravit pomocí Visual C++.  
  
 PROSTŘEDEK. H je soubor hlaviček specifické pro aplikaci. Je vždy název prostředku. H podle objekty AppWizard konzistentní s Visual C++ výchozí názvy záhlaví souboru. #Include tento soubor záhlaví je první příkaz v souboru prostředků (Moje aplikace. RC):  
  
```  
//Microsoft Visual C++ generated resource script  
//  
#include "resource.h"  
```  
  
 RES\MYAPP. RC2  
 Obsahuje prostředky, které nebudou upraveny ve Visual C++, ale budou zahrnuty do konečné zkompilovat. Soubor EXE. Objekty AppWizard žádné tyto prostředky vytvoří ve výchozím nastavení, protože Visual C++ můžete upravit všechny standardní prostředky, včetně verze prostředků (nová funkce v této verzi). Prázdný soubor je generován objekty AppWizard v případě, že chcete přidat vlastní vlastní formátovaný prostředky do tohoto souboru.  
  
 Pokud používáte vlastní formátovaný prostředky, můžete je přidat k RES\MYAPP. RC2 a upravovat pomocí textového editoru Visual C++.  
  
 AFXRES. RC a AFXPRINT. RC obsahují standardní prostředky, které vyžadují určité funkce rozhraní. Jako RES\MYAPP. RC2, jsou tyto dva soubory zadaný framework prostředků #include'd na konci Moje aplikace. RC a jsou určené v kompilaci direktivy dialogového okna nastavení obsahuje. Proto není přímo umožňuje zobrazit nebo upravit tyto prostředky architektury během úprav Moje aplikace. RC v jazyce Visual C++, ale že se kompilují do binárního souboru aplikace. Soubor RES a konečná. Soubor EXE. Další informace o standardní framework prostředků, včetně postupy při úpravách, najdete v části [Technická poznámka 23](../mfc/tn023-standard-mfc-resources.md).  
  
 AFXRES. H definuje standardní symboly, například `ID_FILE_NEW`, používají rozhraní a konkrétně používat v AFXRES. RC. AFXRES. H také #include na WINRES. H, který obsahuje podmnožinu systému WINDOWS. H, která jsou potřeba Visual C++ vygenerovat. RC – soubory a také AFXRES. RC. Symboly definované v AFXRES. H jsou k dispozici při úpravách souboru prostředků aplikace (Moje aplikace. RC). Například `ID_FILE_NEW` se používá pro položku nabídky nový soubor Moje aplikace. Prostředek nabídky na RC. Nelze změnit ani odstranit tyto symboly definované framework.  
  
## <a name="_mfcnotes_tn035_including"></a> Včetně další hlavičkové soubory  
  
 Aplikace vytvořené objekty AppWizard obsahuje pouze dva soubory hlaviček: prostředků. H a AFXRES. H. Pouze prostředek. H je specifické pro aplikaci. Musíte zahrnout další jen pro čtení hlavičkových souborů v následujících případech:  
  
 Záhlaví souboru je poskytován externího zdroje, nebo chcete sdílet mezi více projektů nebo z několika součástí stejného projektu soubor hlaviček.  
  
 Soubor hlaviček má formátování a komentáře, které nechcete změnit nebo odfiltrovat, když se uloží soubor Visual C++. Například možná chcete zachovat #define společnosti využívající symbolický aritmetické operace, jako:  
  
```  
#define RED 0  
#define BLUE 1  
#define GREEN 2  
#define ID_COLOR_BUTTON 1001  
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)  
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)  
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)  
```  
  
 Můžete zahrnout další jen pro čtení hlavičkových souborů pomocí **prostředek zahrnuje** příkazu zadejte #include příkaz jako druhý direktiva Symbol jen pro čtení, jako:  
  
```  
#include "afxres.h"  
#include "second.h"  
```  
  
 Nový diagram vztah souboru nyní vypadat třeba takto:  
  
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
  
 **Sdílení souboru záhlaví mezi dvěma. RC – soubory**  
  
 Můžete sdílet hlavičkový soubor mezi dvěma. RC soubory, které se nacházejí v různých projektů nebo které by mohly mít stejné projektu. Uděláte to tak, jednoduše použijte jen pro čtení direktivy technika popsaná výše na obě. RC – soubory. V případě, kdy dva. RC – soubory jsou pro různé aplikace (různých projektů), výsledkem je znázorněno v následujícím diagramu:  
  
```  
    RESOURCE.H AFXRES.H   RESOURCE.H    
 (for MYAPP1) SECOND.H   (for MYAPP2)               
 \       /     \       /             
 \     /       \     /               
    MYAPP1.RC MYAPP2.RC */    \        /     \ */      \      /       \              
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2                
    AFXPRINT.RC 
```  
  
 Případ, kdy druhý soubor hlaviček sdílí dva. RC – soubory ve stejné aplikaci (projekt) jsou popsány níže.  
  
 **Použití více souborů prostředků ve stejném projektu**  
  
 Visual C++ a kompilátor prostředků podporovat více. RC – soubory ve stejném projektu prostřednictvím #include na jedné. RC soubor v rámci jiného. Je povoleno více vnoření. Existují různé příčiny rozdělit do několika zdroje projektu. RC – soubory:  
  
-   Je snazší spravovat velké množství prostředků mezi více členů týmu, pokud rozdělte prostředky do více. RC – soubory. Pokud používáte balíček správy zdroj ovládací prvek rezervování souborů a kontroly v změny, rozdělení prostředky do více. RC – soubory získáte lepší kontrolu nad Správa změny zdrojů.  
  
-   Pokud chcete použít preprocesor – direktivy, jako je například #ifdef, #endif, a #define, pro části prostředkům, musí izolovat je v jen pro čtení prostředky, které se zkompiluje kompilátorem prostředků.  
  
-   Komponenta. RC – soubory se načíst a uložit v jazyce Visual C++ rychleji než jeden složené. RC soubor.  
  
-   Pokud chcete zachovat prostředku v textovém editoru ve formuláři čitelný, byste měli mít na. RC soubor odděleně od jedné úpravy Visual C++.  
  
-   Pokud potřebujete zachovat prostředek uživatelem definované v binární nebo text formuláře, který je interpretable pomocí jiného editoru specializované dat, pak by měla být v samostatné. RC soubor tak Visual C++ nezmění data v šestnáctkovém formátu formátu. Na. WAV (zvuk) souborových prostředků v ukázce MFC rozšířené koncepty [SPEAKN](../visual-cpp-samples.md) jsou dobrým příkladem.  
  
 Můžete #include druhý. RC v kompilaci direktivy v dialogovém okně nastavení zahrnuje:  
  
```  
#include "res\myapp.rc2"  // non-Visual C++ edited resources  
#include "second.rc"  // THE SECOND .RC FILE  
  
#include "afxres.rc"  // Standard components  
#include "afxprint.rc"  // printing/print preview resources  
```  
  
 Výsledkem je znázorněno v následujícím diagramu:  
  
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
  
 Pomocí direktiv kompilaci, můžete uspořádat Visual C++ upravovat a upravovat prostředky do více. RC – soubory, kde "hlavní" Moje aplikace. RC neprovede žádnou akci, ale #include Další. RC – soubory. Pokud používáte projektu Visual C++. Soubor klíče k vícenásobné aktivaci a potom by měly obsahovat "hlavní". RC v projektu soubor, který všechny #include'd zdroje kompilovány s vaší aplikací.  
  
 **Vynucení souborů neumožňující úpravy Visual C++**  
  
 Vytvořit objekty AppWizard RES\MYAPP. RC2 soubor je příkladem soubor, který obsahuje prostředky, které uděláte *není* chcete omylem načtení do Visual C++ a zapište si ji zpět ztráty formátování informace. Tomu Pokud chcete předejít, umístěte následující řádky na začátek RES\MYAPP. Soubor RC2:  
  
```  
#ifdef APSTUDIO_INVOKED  
 #error this file is not editable by Visual C++  
#endif //APSTUDIO_INVOKED  
```  
  
 Při kompilaci Visual C++. RC soubor definuje **APSTUDIO_INVOKED** a také **RC_INVOKED**. Pokud strukturu vytvořené objekty AppWizard soubor je poškozený a přečte výše #error řádku Visual C++, sestavy na závažnou chybu a přerušit čtení. RC soubor.  
  
 **Správa symboly, které jsou sdíleny více Visual C++ upravit. RC – soubory**  
  
 Při rozdělování si vaše prostředky do více mohou vzniknout dva problémy. RC soubory, které chcete upravit samostatně v jazyce Visual C++:  
  
-   Můžete chtít sdílet stejnou symboly napříč více. RC – soubory.  
  
-   Potřebujete zajistit Visual C++ nepřiřazujte stejné ID číselné hodnoty odlišné prostředky (symbolů).  
  
 Následující diagram znázorňuje organizaci systému. RC a. H soubory, které se zabývá první problém:  
  
```  
    MYAPP.RC */         \ */           \  
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H  
 \    /    /      \   \    \  
 \  /    /        \   \    \  
    MYSTRS.RC MYMENUS.RC  
```  
  
 V tomto příkladu řetězcové prostředky se ukládají do jednoho zdrojového souboru, MYSTRS. RC a nabídky jsou uchovávány v jiné, MYMENUS. RC. Některé symboly, například konkrétní příkazy, může třeba sdílet mezi těmito dvěma soubory. ID_TOOLS_SPELL může být například ID příkazu nabídky pro kontrolu pravopisu položku v nabídce Nástroje pro; a řetězec ID příkazovém řádku zobrazí rámcem ve stavovém řádku hlavního okna aplikace může být také.  
  
 ID_TOOLS_SPELL symbol je uložen v souboru sdílené záhlaví MYSHARED. H. Ručně udržovat tento sdílený hlavičkový soubor v textovém editoru; Visual C++ není upravovat přímo. V rámci dvou prostředku soubory MYSTRS. RC a MYMENUS. Zadáte RC, #include MYSHARED. H v direktivy jen pro čtení pro Moje aplikace. RC, pomocí **prostředek zahrnuje** příkaz, jak je popsáno výše.  
  
 Je nejvhodnější pro předvídání symbol budou sdílet, než se pokusíte použít pro identifikaci všech prostředků. Má být symbol přidán do sdílené záhlaví souboru a, pokud již máte #include'd sdílené hlavičkový soubor v direktivy jen pro čtení pro. RC souboru, proveďte to před použitím symbolu. Pokud jste neodhadl, sdílení symbol tímto způsobem, pak budete muset ručně (pomocí textového editoru) přesunout #define příkazu pro symbol z Řekněme, MYMENUS. H k MYSHARED. H před použitím v MYSTRS. RC.  
  
 Při správě symboly v několika. RC – soubory, můžete také musí pomoci Visual C++ nepřiřazujte stejné ID číselné hodnoty odlišné prostředky (symbolů). Pro všechny zadané. RC soubor Visual C++ přírůstkově přiřadí ID v každé z domén čtyři ID. Mezi úpravy relací, Visual C++ uchovává informace o ID poslední jí přiřadit v každé z domén v záhlaví souboru symbol pro. RC soubor. Zde je APS_NEXT hodnoty jsou pro prázdnou (Nový). RC soubor:  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  101  
#define _APS_NEXT_COMMAND_VALUE   40001  
#define _APS_NEXT_CONTROL_VALUE   1000  
#define _APS_NEXT_SYMED_VALUE     101  
```  
  
 **_APS_NEXT_RESOURCE_VALUE** je hodnotě další symbol, který se použije pro dialogové okno prostředků, prostředků nabídky a tak dále. Platný rozsah hodnot symbol prostředků je 1 – 0x6FFF.  
  
 **_APS_NEXT_COMMAND_VALUE** je hodnotě další symbol, který se použije pro identifikaci příkaz. Platný rozsah pro příkaz symbol hodnoty je 0x8000 k 0xDFFF.  
  
 **_APS_NEXT_CONTROL_VALUE** je hodnotě další symbol, který se použije pro ovládací prvek dialogového okna. Platný rozsah pro dialogové okno ovládacího prvku symbol hodnoty je 8 k 0xDFFF.  
  
 **_APS_NEXT_SYMED_VALUE** je další symbol hodnotu, která způsobí vystavení, když ho ručně nepřiřadíte hodnotu symbol použít nový příkaz, v prohlížeči Symbol.  
  
 Visual C++ začíná mírně vyšší hodnoty, právních nejnižší hodnotu v případě vytvoření nové. RC soubor. Objekty AppWizard také inicializuje tyto hodnoty na něco pro aplikace MFC vhodnější. Další informace o rozsahy hodnota ID najdete v tématu [Technická poznámka 20](../mfc/tn020-id-naming-and-numbering-conventions.md).  
  
 Teď pokaždé, když vytvoříte nový soubor prostředků, i v rámci jednoho projektu, Visual C++ definuje stejné **_APS_NEXT\_**  hodnoty. To znamená, že pokud přidáte, můžete, více v dialogových oknech v dva různé. RC – soubory, je velmi pravděpodobné, který stejné #define hodnota se přiřadí různé dialogová okna. Například IDD_MY_DLG1 v prvním. RC soubor může být přiřazen stejný počet, 101, jako IDD_MY_DLG2 za sekundu. RC soubor.  
  
 Abyste tomu předešli, by měl vyhradit samostatné číselný rozsah pro každé z domén, čtyři ID v příslušné. RC – soubory. To provedete ruční aktualizace **_APS_NEXT** hodnoty v jednotlivých. RC – soubory `before` začnete přidávat prostředky. Například pokud první. RC soubor používá výchozí **_APS_NEXT** hodnoty, pak můžete přiřadit následující **_APS_NEXT** hodnoty na druhý. RC soubor:  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  2000  
#define _APS_NEXT_COMMAND_VALUE   42000  
#define _APS_NEXT_CONTROL_VALUE   2000  
#define _APS_NEXT_SYMED_VALUE     2000  
```  
  
 Samozřejmě je stále možné, že Visual C++ se přiřazení mnoho ID v prvním. RC soubor, který číselné hodnoty začít těch, které pro druhý překrývat. RC soubor. Dostatečně velké oblasti by měl rezervovat tak, aby se tato situace.  
  
 **Správa závislostí mezi. RC. CPP, a. Soubory H**  
  
 Když Visual C++ uloží. RC soubor se taky uloží symbol změny odpovídající prostředek. Soubor H. Některé z vaší. CPP souborů, které odkazují na prostředky v. RC soubor musí #include prostředku. Soubor H, obvykle v rámci vašeho projektu hlavní hlavičkový soubor. To vede k vedlejší účinek z důvodu interní projektu Správa vývojové prostředí, která kontroluje zdrojové soubory pro záhlaví závislosti. Pokaždé, když přidáte nový symbol v jazyce Visual C++, všechny. CPP souboru, který #include prostředků. H by bylo potřeba zopakovat.  
  
 Visual C++, by se obešla závislost na prostředku. H včetně komentář následující jako první řádek prostředku. Soubor H:  
  
```  
//{{NO_DEPENDENCIES}}  
```  
  
 Vývojové prostředí interpretuje tohoto komentáře ignorováním změny prostředků. H proto to závislé. Soubory CPP nebudete muset zopakovat.  
  
 Visual C++ vždy přidá //{{NO_DEPENDENCIES}} komentář řádku. RC soubor, když se uloží soubor. V některých případech obcházení sestavení závislosti na prostředku. H může vést ke běhové chyby nebyla rozpoznána v době spojení. Například pokud používáte prohlížeč Symbol změnit číselnou hodnotu přiřazenou symbol pro prostředek, prostředek nebude správně najít a načíst v případě spuštění aplikace. Není překompilovat souboru CPP odkazující na prostředek. V takových případech můžete musí explicitně znovu zkompiluje žádné. Symbol změny v prostředku se týká CPP souborů, které znáte. H nebo vyberte **znovu vytvořit všechny**. Pokud je potřeba často mění symbol hodnoty pro určité skupiny prostředků, pravděpodobně naleznete ji pohodlnější a bezpečnější pro přerušení těchto symbolů do samostatné jen pro čtení hlavičky souboru, jak je popsáno v části výše [včetně Soubory hlaviček Další](#_mfcnotes_tn035_including).  
  
## <a name="_mfcnotes_tn035_set_includes"></a> Jak Visual C++ spravuje sada obsahuje informace o **  
  
 Jak je popsáno výše, v nabídce Soubor nastavit obsahuje příkaz umožňuje určit tři typy informací:  
  
-   Soubor hlaviček symbolů  
  
-   Směrnice pro symboly jen pro čtení  
  
-   Direktivy kompilace  
  
 Následující text popisuje, jak Visual C++ zajišťuje tyto informace. RC soubor. Není nutné tyto informace používat Visual C++, ale tak, aby mohli bez obav více můžete nastavit zahrnuje funkce, může ho cestou prohloubit vaše pochopení.  
  
 Každou z výše uvedených tří typů nastavit zahrnuje informace jsou uloženy v. RC soubor ve dvou formách: (1) jako #include nebo jiné direktivy interpretable kompilátor prostředků a (2) jako speciální prostředky TEXTINCLUDE interpretable pouze ve Visual C++.  
  
 Účelem TEXTINCLUDE prostředku je bezpečně uložit nastavení zahrnují informace ve formuláři, který je snadno přístupné v jazyce Visual C++ **nastavit zahrnuje** dialogové okno. Je TEXTINCLUDE *typ prostředku* definované ve Visual C++. Visual C++ rozpozná tři konkrétní TEXTINCLUDE prostředky, které mají prostředků identifikační čísla 1, 2 a 3:  
  
|ID prostředku TEXTINCLUDE|Typ nastavení zahrnuje informací|  
|-----------------------------|--------------------------------------|  
|1|Soubor hlaviček symbolů|  
|2|Směrnice pro symboly jen pro čtení|  
|3|Direktivy kompilace|  
  
 Všechny tři typy nastavení zahrnuje informace je zobrazená ve výchozím nastavení Moje aplikace. RC a prostředků. H soubory vytvořené objekty AppWizard, jak je popsáno níže. Navíc \0 a "" tokeny mezi bloky ZAČÁTKU a KONCE potřebuje RC syntaxe pro specifikují nulové ukončenou řetězce a znak dvojitých uvozovek.  
  
## <a name="symbol-header-file"></a>Soubor hlaviček symbolů  
 Formu interpretovat kompilátor prostředků informací o symbolu záhlaví souboru je jednoduše #include příkaz:  
  
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
  
## <a name="read-only-symbol-directives"></a>Směrnice pro symboly jen pro čtení  
 Směrnice pro symboly jen pro čtení jsou zahrnuty v horní části Moje aplikace. RC v následující podobě interpretable kompilátorem prostředků:  
  
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
  
## <a name="compile-time-directives"></a>Direktivy kompilace  
 Direktivy kompilaci jsou zahrnuty na konci Moje aplikace. RC v následující podobě interpretable kompilátorem prostředků:  
  
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
  
 #Ifndef – direktiva APSTUDIO_INVOKED dá pokyn k přeskočit direktivy kompilaci Visual C++.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

