---
title: Redistribuce souborů Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 46192fe7ff5b29c22a5001cc460c74f5ddf6d1bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167924"
---
# <a name="redistributing-visual-c-files"></a>Redistribuce souborů Visual C++

> [!NOTE]
> Jste tady, protože hledáte stažení jednoho ze souborů Visual C++ runtime? Přejděte na [Web společnosti Microsoft](https://www.microsoft.com/) a do vyhledávacího pole zadejte  **C++ Visual Redistributable** . Stáhněte a nainstalujte Distribuovatelný balíček pro architekturu vašeho počítače (například x64, pokud používáte 64-bit Windows) a verzi vizuálu C++ (například 2015), kterou potřebujete.

Při nasazení aplikace je nutné nasadit také soubory, které jsou vyžadovány pro její podporu. Pokud je některý z těchto souborů poskytován společností Microsoft, zkontrolujte, zda je povoleno jej dále distribuovat. Pokud si chcete přečíst licenční smlouvu sady Visual Studio, přečtěte si odkaz licenční smlouva v dialogovém okně o Microsoft Visual Studio v integrovaném vývojovém prostředí (IDE), nebo si stáhněte soubor [licenčních podmínek pro software společnosti Microsoft](https://visualstudio.microsoft.com/license-terms/mlt687465/) . Chcete-li zobrazit seznam Redist, na který je odkazováno v oddíle "Distribuovatelný kód" licenčních podmínek pro software společnosti Microsoft pro některé edice sady Visual Studio, viz [Distribuovatelný kód pro Microsoft Visual Studio 2017 a Microsoft Visual Studio 2017 SDK (zahrnuje nástroje a soubory buildovacího serveru)](/visualstudio/productinfo/2017-redistribution-vs), nebo pro sadu visual Studio 2015 naleznete v tématu [distribuovatelný kód pro Microsoft Visual Studio 2015 a Microsoft Visual Studio 2015 SDK](/visualstudio/productinfo/2015-redistribution-vs). Další informace o redistribuovatelných souborech naleznete v tématu [určení, které knihovny DLL mají být znovu distribuovány](determining-which-dlls-to-redistribute.md) a [Příklady nasazení](deployment-examples.md).

Pro nasazení distribuovatelných vizuálních C++ souborů můžete použít Visual C++ redistributable balíčky (VCRedist\_x86. exe, VCRedist\_x64. exe nebo VCRedist\_ARM. exe), které jsou součástí sady Visual Studio. V aplikaci Visual Studio 2017 se tyto soubory dají najít ve složce Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\redist\\MSVC\\_lib-Version_ , kde _Edition_ je nainstalovaná edice sady Visual Studio a _lib-Version_ je verze knihoven, které se mají znovu distribuovat. V aplikaci Visual Studio 2015 se tyto soubory nacházejí v instalačním adresáři sady Visual Studio v souborech programu [(x86)] \Microsoft Visual Studio *Version*\VC\redist\\*locale*\\. Další možností je použití redistribuovatelných slučovacích modulů (soubory. msm), které se v aplikaci Visual Studio 2017 dají najít ve složce Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edice_\\VC\\redist\\MSVC\\_lib-version_\\MergeModules\\. V aplikaci Visual Studio 2015 se tyto soubory nacházejí v programových souborech [(x86)] \Commonch Files\Merge modulech, které jsou\\. Je také možné přímo nainstalovat redistribuovatelné vizuální C++ knihovny DLL do *místní složky aplikace*, což je složka, která obsahuje soubor spustitelných aplikací. Pro účely údržby nedoporučujeme používat toto umístění instalace.

Distribuovatelné balíčky Visual C++ nainstalují a zaregistrují všechny knihovny Visual C++. Používáte-li je, je nutné nastavit jejich spuštění v cílovém systému, což je nezbytná podmínka pro instalaci aplikace. Doporučujeme používat pro nasazení právě tyto balíčky, protože umožňují automatické aktualizace knihovny Visual C++. Příklad použití těchto balíčků naleznete v tématu [Návod: nasazení vizuální C++ aplikace pomocí balíčku Visual C++ Redistributable Package](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Každý balíček C++ Visual Redistributable Package kontroluje existenci novější verze v počítači. Pokud je nalezena novější verze, balíček není nainstalován. Počínaje verzí sady Visual Studio 2015 se v distribuovatelných balíčcích zobrazí chybová zpráva oznamující, že instalace se nezdařila. Pokud se balíček spustí pomocí příznaku **/quiet** , nezobrazí se žádná chybová zpráva. V obou případech je chyba protokolována instalačním programem společnosti Microsoft a výsledkem je vrácení chyby volajícímu. Počínaje balíčky sady Visual Studio 2015 se můžete této chybě vyhnout tak, že zkontrolujete registr a zjistíte, jestli je nainstalovaná novější verze. Aktuálně nainstalovaná verze je uložená ve službě HKEY_LOCAL_MACHINE \SOFTWARE [\Wow6432Node] \Microsoft\VisualStudio\\_vs-Version_\VC\Runtimes\\{x86 | x64 | ARM} klíč, kde _vs-Version_ , je číslo verze pro Visual studio (14,0 pro visual Studio 2015 a visual Studio 2017, protože aktualizovaná verze programu 2017 Redistributable je binární, kompatibilní s verzí 2015) a kde Key je ARM, x86 nebo x64 v závislosti na nainstalovaných verzích VCRedist pro danou platformu. (Pokud nepoužíváte nástroj Regedit k zobrazení verze nainstalovaného balíčku x86 na platformě x64, nemusíte se kontrolovat pod podklíčem Wow6432Node.) Číslo verze je uloženo v REG_SZ **verzi** hodnoty řetězce a také v sadě hodnot REG_DWORD **hlavní_verze**, **podverze**, **bld**a **Rbld** . Chcete-li se vyhnout chybě při instalaci, je nutné přeskočit instalaci redistribuovatelného balíčku, pokud je aktuálně nainstalovaná verze novější.

Používáte-li slučovací modul, který obsahuje vizuální C++ knihovnu DLL, je nutné jej zahrnout do balíčku Instalační služba systému Windows (nebo podobného instalačního balíčku), který používáte k nasazení aplikace. Další informace naleznete v tématu [Redistribuce pomocí slučovacích modulů](redistributing-components-by-using-merge-modules.md). Příklad naleznete v tématu [Návod: nasazení vizuální C++ aplikace pomocí projektu instalace](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), který také ukazuje, jak pomocí nástroje InstallShield omezené Edition vytvořit instalační balíček.

## <a name="potential-run-time-errors"></a>Potenciální běhové chyby

Pokud systém Windows nemůže najít jeden z redistribuovatelných knihoven DLL potřebných pro vaši aplikaci, může se zobrazit zpráva podobná této: "tuto aplikaci se nepodařilo spustit, protože nebyla nalezena *Knihovna*dll. Tento problém může vyřešit Opakovaná instalace aplikace. "

Chcete-li tento druh chyby vyřešit, ujistěte se, že instalační program aplikace správně sestaví a zda jsou distribuovatelné knihovny správně nasazeny v cílovém systému. Další informace najdete v tématu [Principy závislostí vizuální C++ aplikace](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Redistribuce pomocí slučovacích modulů](redistributing-components-by-using-merge-modules.md)|Popisuje, jak použít Visual C++ Redistributable Merge modules k instalaci knihoven Visual C++ runtime jako sdílených knihoven DLL ve složce%Windir%\system32\.|
|[Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++](redistributing-visual-cpp-activex-controls.md)|Popisuje, jak distribuovat aplikaci používající ovládací prvky technologie ActiveX.|
|[Redistribuce knihovny MFC](redistributing-the-mfc-library.md)|Popisuje, jak distribuovat aplikaci používající knihovnu MFC.|
|[Redistribuce aplikace ATL](redistributing-an-atl-application.md)|Popisuje, jak znovu distribuovat aplikaci, která používá knihovnu ATL. Počínaje verzí Visual Studio 2012 není nutná žádná Redistribuovatelná knihovna pro ATL.|
|[Příklady nasazení](deployment-examples.md)|Odkazuje na příklady demonstrující, jak nasadit aplikace jazyka Visual C++.|
|[Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)|Představuje koncepty a technologie nasazení Visual C++.|
