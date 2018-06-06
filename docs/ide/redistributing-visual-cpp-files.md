---
title: Redistribuce souborů Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e67ad87f1dce47f3d02dcbe907285cf0513a8ce9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337545"
---
# <a name="redistributing-visual-c-files"></a>Redistribuce souborů Visual C++

> [!NOTE]
> Jste tady vzhledem k tomu, že hledáte stahování jednoho ze souborů modulu Runtime Visual C++? Přejděte na [Microsoft](http://www.microsoft.com/) web a zadejte **Visual C++ Redistributable** do vyhledávacího pole. Stáhněte a nainstalujte redistribuovatelného balíčku pro architekturu počítače (například x64 Pokud používáte systém Windows 64-bit) a verze aplikace Visual C++ (například 2015), které potřebujete.

Při nasazení aplikace je nutné nasadit také soubory, které jsou vyžadovány pro její podporu. Pokud je některý z těchto souborů poskytován společností Microsoft, zkontrolujte, zda je povoleno jej dále distribuovat. Chcete-li zkontrolovat licenční podmínky pro Visual Studio, klikněte na odkaz licenční podmínky v dialogovém okně o aplikaci Microsoft Visual Studio v prostředí IDE nebo stáhnout [licenční podmínky softwaru společnosti Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=831114) souboru. "Seznam REDISTRIBUCE, na který se odkazuje v části"Distribuovatelný kód"licenční podmínky pro Software společnosti Microsoft pro některé edice sady Visual Studio najdete v tématu [distribuovatelného kódu pro Microsoft Visual Studio 2017 a Microsoft Visual Studio 2017 Sada SDK (zahrnuje nástroje a soubory buildovacího serveru)](http://go.microsoft.com/fwlink/p/?LinkId=823098), nebo pro Visual Studio 2015, najdete v části [Distribuovatelný kód pro Microsoft Visual Studio 2015 a Microsoft Visual Studio 2015 SDK](http://go.microsoft.com/fwlink/p/?LinkId=523763). Další informace o redistribuovatelné soubory, najdete v části [určení, které knihovny DLL znovu distribuovat](../ide/determining-which-dlls-to-redistribute.md) a [Příklady nasazení](../ide/deployment-examples.md).

Chcete-li nasadit redistribuovatelné soubory Visual C++, můžete použít Distribuovatelné balíčky Visual C++ (VCRedist\_x86.exe VCRedist\_x64.exe nebo součást VCRedist\_arm.exe) které jsou zahrnuté v sadě Visual Studio. Ve Visual Studio 2017, tyto soubory najdete ve složce Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\ MSVC\\_lib-version_ složku, kde _edition_ je edicí sady Visual Studio nainstalována, a _lib-version_ je verze knihovny znovu distribuovat. V sadě Visual Studio 2015, tyto soubory naleznete v části adresáře instalace sady Visual Studio v Program Files [(x 86)] \Microsoft Visual Studio *verze*\VC\redist\\*národního prostředí* \\. Další možností je použít redistributable slučovací moduly (soubory .msm), které v Visual Studio 2017 najdete v souborech programu [(x 86)]\\Microsoft Visual Studio\\2017\\_edition_ \\ VC\\Redist\\MSVC\\_lib-version_\\MergeModules\\ složky. V sadě Visual Studio 2015 ty lze najít v programových souborů [(x 86)] \Common Files\Merge moduly\\. Je také možné přímo nainstalovat redistributable Visual C++ – knihovny DLL v *místní složky aplikace*, což je složka, která obsahuje váš soubor spustitelná aplikace. Pro obsluhu z důvodů, nedoporučujeme používat toto umístění instalace.

Distribuovatelné balíčky Visual C++ nainstalují a zaregistrují všechny knihovny Visual C++. Používáte-li je, je nutné nastavit jejich spuštění v cílovém systému, což je nezbytná podmínka pro instalaci aplikace. Doporučujeme používat pro nasazení právě tyto balíčky, protože umožňují automatické aktualizace knihovny Visual C++. Příklad o tom, jak používat tyto balíčky, naleznete v části [návod: nasazení Visual C++ aplikace s použitím redistribuovatelného balíčku Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Každý balíček Visual C++ Redistributable zkontroluje existenci novější verze na počítači. Pokud je nalezena novější verze, balíček není nainstalovaný. Spuštění ve Visual Studiu 2015, zobrazení Distribuovatelné balíčky se nepodařilo chybovou zprávu s oznámením, že instalační program. Pokud je balíček spustit pomocí **/quiet** příznak žádná chybová zpráva se zobrazí. V obou případech zaznamenána chyba instalačního programu společnosti Microsoft a výsledek chyba je vrácena volajícímu. Od verze sady Visual Studio 2015 balíčky, se můžete vyhnout této chybě kontrolou registru a zjistěte, zda je nainstalována novější verze. Aktuálně nainstalovanou verzi je uložen v \Microsoft\VisualStudio HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node]\\_vs-version_\VC\Runtimes\\{x86 | x64 | Klíč ARM}, kde _vs-version_ je číslo verze pro sadu Visual Studio (14.0 pro Visual Studio 2015 a Visual Studio 2017, protože aktualizované 2017 redistributable je binární kompatibilní s verzí 2015), a kde je klíč ARM x 86 nebo x64 v závislosti na nainstalovaná součást vcredist verze pro platformu. (Nemusíte zkontrolujte v podklíči Wow6432Node, pokud chcete zobrazit verzi nainstalovaného x86 používáte RegEdit balíček na x64 platformy.) Číslo verze je uložené v hodnotě REG_SZ řetězce **verze** a také v sadě **hlavní**, **menší**, **Bld**a **Rbld** hodnoty REG_DWORD. Aby nedošlo k chybě během instalace, musíte přejít instalace distribuovatelného balíčku, pokud aktuálně nainstalovaná verze je novější.

Pokud používáte modul sloučení, který obsahuje knihovny DLL Visual C++, je třeba jej zahrnout v balíčku Instalační služby systému Windows (nebo podobné instalační balíček), který používáte k nasazení aplikace. Další informace najdete v tématu [Redistribuce podle použití slučovacích modulů](../ide/redistributing-components-by-using-merge-modules.md). Příklad, naleznete v části [návod: nasazení Visual C++ aplikace pomocí projektu instalace](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), který také ukazuje, jak používat InstallShield Limited Edition k vytvoření instalačního balíčku.

## <a name="potential-run-time-errors"></a>Potenciální běhové chyby

Pokud systém Windows nemůže najít jednu redistributable knihovny DLL, které jsou potřebné pro vaši aplikaci, může se zobrazit zpráva podobná této: "tuto aplikaci se nepodařilo spustit, protože *knihovny*.dll nebyl nalezen. Opětovné instalaci aplikace může problém vyřešit tento problém."

Chcete-li vyřešit tento druh chyby, ujistěte se, správně vytvoří instalační program aplikace a aby byly redistributable knihovny správně nasazené v cílovém systému. Další informace najdete v tématu [Principy závislostí aplikace Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Redistribuce s použitím slučovacích modulů](../ide/redistributing-components-by-using-merge-modules.md)|Popisuje, jak použít k instalaci modulu runtime knihoven Visual C++ jako sdílené knihovny DLL ve složce %windir%\system32\ Visual C++ redistributable slučovacích modulů.|
|[Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++](../ide/redistributing-visual-cpp-activex-controls.md)|Popisuje, jak distribuovat aplikaci používající ovládací prvky technologie ActiveX.|
|[Redistribuce podpůrných souborů databáze](../ide/redistributing-database-support-files.md)|Popisuje, jak distribuovat podporované soubory pro rozhraní DAO a databázové technologie v sadě Microsoft Data Access SDK.|
|[Redistribuce knihovny MFC](../ide/redistributing-the-mfc-library.md)|Popisuje, jak distribuovat aplikaci používající knihovnu MFC.|
|[Redistribuce aplikace ATL](../ide/redistributing-an-atl-application.md)|Popisuje, jak znovu distribuovat aplikace, která používá ATL. Spouštění v sadě Visual Studio 2012, žádné redistributable pro ATL vyžaduje se knihovna.|
|[Příklady nasazení](../ide/deployment-examples.md)|Odkazuje na příklady demonstrující, jak nasadit aplikace jazyka Visual C++.|
|[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)|Představuje koncepty a technologie nasazení Visual C++.|