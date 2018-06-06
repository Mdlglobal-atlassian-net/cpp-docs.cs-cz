---
title: Určení, které knihovny DLL je třeba redistribuovat | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3ca079fc69fe10f15a55812eaa55d4ba2d2ab04
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337597"
---
# <a name="determining-which-dlls-to-redistribute"></a>Zjištění, které knihovny DLL je třeba redistribuovat

Když vytvoříte aplikaci, která používá knihovna DLL poskytl Visual Studio, uživatelů vaší aplikace musí rovněž mít tyto knihovny DLL na svých počítačích pro spuštění aplikace. Protože většina uživatelů pravděpodobně nemají nainstalovanou sadu Visual Studio, je nutné zadat tyto knihovny DLL pro ně. Sada Visual Studio provádí tyto knihovny DLL k dispozici jako *redistribuovatelné soubory* , kterou můžete v instalačním programem vaší aplikace.

Aby bylo snazší zahrnout redistributable knihovny DLL s instalačním programem vaší, jsou k dispozici jako samostatné *Distribuovatelné balíčky*. Toto jsou specifické pro architekturu spustitelné soubory, které instalace distribuovatelné soubory v počítači uživatele pomocí Centrální nasazení. Například vcredist\_x86.exe nainstaluje 32bitová verze knihovny pro x86 počítače, vcredist\_x64.exe nainstaluje 32bitová verze a 64bitová verze knihovny pro x64 počítače a vcredist\_ARM.exe nainstaluje knihovny pro ARM počítače. Centrální nasazení doporučujeme, protože společnost Microsoft mohla použít službu Windows Update nezávisle aktualizovat tyto knihovny. Kromě kopií v instalaci sady Visual Studio, jsou k dispozici ke stažení na aktuální Distribuovatelné balíčky [VisualStudio.com/Downloads](https://www.visualstudio.com/downloads/) v části Další nástroje a rozhraní.

Hlavní číslo verze distribuovatelného balíčku, který nasazujete musí odpovídat verzi sady nástrojů Visual Studio použít k vytvoření aplikace. Visual Studio 2017 a Visual Studio 2015 mít číslo verze kompatibilní nástrojů, což znamená, že Visual Studio 2017 redistribuovatelné soubory, může být používán aplikace vytvořené pomocí sady nástrojů 2015. Když mohou být kompatibilní, nepodporujeme pomocí 2015 redistribuovatelné soubory v aplikace vytvořené pomocí sady nástrojů 2017. Pouze podporovat použití redistribuovatelného balíčku, která je stejná jako nebo novější než nástrojů verze. Odkazy na nejnovější podporovanou Distribuovatelné balíčky pro starší modulové, najdete v části [nejnovější podporované Visual C++ stahování](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads). Konkrétní dřívějších verzích Distribuovatelné balíčky najdete tak, že [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431) pro "Distribuovatelné balíčky Visual C++".

Dalším způsobem zahrnout redistributable knihovny DLL s instalačním programem vaší je použít *slučovací moduly*. Tyto moduly Microsoft Installer jsou součástí a nainstalovat s instalačním programem vaší aplikace. Slučovací moduly pro redistributable knihovny DLL se nacházejí v adresáři instalace sady Visual Studio v části \\VC\\Redist\MSVC\\*verze*\\MergeModules\\ . V dřívějších verzích sady Visual Studio, tyto soubory se nacházejí ve vaší \\Program Files nebo \\adresář Program Files (x86) v společné soubory\\podadresáři slučovacích modulů. Další informace o použití těchto souborů najdete v tématu [Redistribuce součástí s použitím modulů sloučení](../ide/redistributing-components-by-using-merge-modules.md).

Jednotlivé redistributable knihovny DLL jsou také uvedené v instalaci sady Visual Studio. Ve výchozím nastavení, jsou nainstalovány v instalačním adresáři v sadě Visual Studio \\VC\\Redist\\MSVC\\*verze* složky. *Verze* čísla může představovat jiné menší sestavení počty jeden společnou sadu redistribuovatelné soubory. Použijte nejnovější verzi soubor knihovny DLL, redistribuovatelný balíček či slučovací modul najít v těchto adresářů. Můžete použít tyto knihovny pro místní nasazení nainstalováním ve stejném adresáři jako aplikace. Místní nasazení nedoporučujeme, protože díky tomu je zodpovědná za doručování aktualizací vaše nasazené aplikace. Centrální nasazení pomocí Distribuovatelné balíčky je upřednostňovaný.

Chcete-li určit, které knihovny DLL, budete muset znovu distribuovat s vaší aplikací, seznam knihoven DLL, které závisí aplikace na shromažďování. Tyto podmínky jsou uvedeny normálně jako importovat knihovny vstupy linkeru. Některé knihovny, například vcruntime a univerzální C Runtime Library (UCRT), jsou zahrnuté ve výchozím nastavení. Pokud vaše aplikace nebo jeden z jeho závislosti používá LoadLibrary se dynamicky načíst knihovnu DLL, nemusí být uvedeny této knihovny DLL na vstupy pro linkeru. Je možné shromáždit seznam dynamicky načtené knihovny DLL ke spuštění Walkera závislosti (depends.exe) ve vaší aplikaci, jak je popsáno v [Principy závislostí aplikace Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Bohužel se tento nástroj je zastaralá a může hlásit, že nelze najít určité knihovny DLL.

Když máte seznam závislosti, porovnejte, je do seznamu propojené v souboru Redist.txt souboru v instalačním adresáři nástroje sady Microsoft Visual Studio, nebo seznam REDISTRIBUCE, na"redistributable knihoven DLL, který se odkazuje v části"Soubory distribuovatelného kódu" Microsoft licenčních podmínek pro Software pro vaší kopie Visual Studio. Visual Studio 2017, najdete v části [Distribuovatelný kód pro Microsoft Visual Studio 2017 (zahrnuje nástrojů, rozšíření a soubory buildovacího serveru)](http://go.microsoft.com/fwlink/p/?linkid=823098). Visual Studio 2015, najdete v části [Distribuovatelný kód pro Microsoft Visual Studio 2015 a Microsoft Visual Studio 2015 SDK (zahrnuje nástroje a soubory buildovacího serveru)](http://go.microsoft.com/fwlink/p/?linkid=799794). Pro Visual Studio 2013, v seznamu je k dispozici online v [distribuovatelného kódu pro Microsoft Visual Studio 2013 a Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603).

V sadě Visual Studio verze před Visual Studio 2015, byl zahrnut jako redistributable knihovny DLL, v msvc C Runtime Library (CRT)*verze*.dll. Spouštění v sadě Visual Studio 2015, byly funkce v CRT rozdělili do vcruntime a UCRT. UCRT je nyní součástí systému ve Windows 10 spravovaná službou Windows Update. Je k dispozici pro všechny operační systémy Windows 10. Chcete-li nasadit aplikaci na starší operační systémy, musíte znovu distribuovat UCRT také. Starší verzi aplikace UCRT je zahrnuté v sadě Visual Studio redistribuovatelné soubory, které je nainstalován pouze v operačních systémech starších než Windows 10, a to pouze pokud je již nainstalována žádná verze UCRT. Instalovat verzi UCRT pro systémy nižší úrovně jako balíček aktualizace produktu Microsoft System, naleznete v části [Windows 10 Universal C Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=48234) na webu Microsoft Download Center.

Nelze znovu distribuovat všechny soubory, které jsou zahrnuté v sadě Visual Studio; jsou povolena pouze chcete-li distribuovat soubory, které jsou určené v souboru Redist.txt nebo online seznam REDISTRIBUCE,." Ladicí verze aplikací a různé ladění jazyka Visual C++ – knihovny DLL nejsou redistributable. Další informace najdete v tématu [volba metody nasazení](../ide/choosing-a-deployment-method.md).

Následující tabulka popisuje některé z Visual C++ knihovny DLL, která vaše aplikace může záviset na.

|Knihovna jazyka Visual C++|Popis|Platí pro|
|--------------------------|-----------------|----------------|
|vcruntime*verze*.dll|Knihovna modulu runtime pro nativní kód.|Aplikace, které používají normální C a C++ jazyk spuštění a ukončení služby.|
|vccorlib*verze*.dll|Knihovna modulu runtime pro spravovaný kód.|Aplikace, které používají službu jazyka C++ pro spravovaný kód.|
|msvcp*verze*.dll a msvcp*verze*_*dotnumber*.dll|Standardní knihovna C++ pro nativní kód|Aplikace, které používají [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*verze*.dll|Knihovna Concurrency Runtime pro nativní kód.|Aplikace, které používají [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).|
|MFC*verze*.dll|Microsoft Foundation třídy (MFC) knihovny.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md).|
|MFC*verze* *jazyk*.dll|Microsoft Foundation třídy (MFC) prostředků knihovny.|Aplikace, které používají konkrétní jazyk prostředky pro MFC.|
|MFC*verze*u.dll|Knihovna MFC s podporou Unicode.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) a nepožadujete podporu kódování Unicode.|
|mfcmifc80.dll|MFC – knihovna spravovaná rozhraní.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) s [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*verze*.dll|Spravované knihovny MFC.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) s [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*verze*u.dll|Spravované knihovny MFC s podporou Unicode.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) s [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index) a nepožadujete podporu kódování Unicode.|
|vcamp*verze*.dll|Knihovna AMP pro nativní kód.|Aplikace, které používají [knihovny C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) kódu.|
|vcomp*verze*.dll|Knihovna OpenMP pro nativní kód.|Aplikace, které používají [knihovny C++ OpenMP](../parallel/openmp/openmp-in-visual-cpp.md) kódu.|

> [!NOTE]
> Už je nutné znovu distribuovat aktivní knihovna šablon jako samostatné knihovny DLL. Svých funkcí, aby byl přesunut do záhlaví a statické knihovny.

Další informace o tom, jak znovu distribuovat tyto knihovny DLL s vaší aplikací najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md). Příklady najdete v tématu [Příklady nasazení](../ide/deployment-examples.md).

Obvykle je nemusíte znovu distribuovat systémové knihovny DLL, protože jsou součástí operačního systému. Však může existovat výjimky, například pokud vaše aplikace bude spuštěna v několika verzích operačních systémů Microsoft. V takovém případě nezapomeňte si přečíst odpovídající licenční podmínky. Také pokusí se získat systémové knihovny DLL pomocí služby Windows Update, aktualizace service Pack nebo s použitím Distribuovatelné balíčky zpřístupněné společností Microsoft.

## <a name="see-also"></a>Viz také

[Volba metody nasazení](../ide/choosing-a-deployment-method.md)

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)
