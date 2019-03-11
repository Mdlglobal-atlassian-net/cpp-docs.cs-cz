---
title: Zjištění, které knihovny DLL je třeba redistribuovat
ms.date: 06/08/2018
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: ee81fb1560133b2777a33e80d32c0e2e55c01bf4
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749084"
---
# <a name="determining-which-dlls-to-redistribute"></a>Zjištění, které knihovny DLL je třeba redistribuovat

Při sestavování aplikace, která používá knihoven DLL, získáte ho od sady Visual Studio se třeba uživatelům vaší aplikace těmito knihovnami DLL na svých počítačích pro spuštění aplikace. Protože většina uživatelů pravděpodobně nemají nainstalovanou sadu Visual Studio, je nutné zadat tyto knihovny DLL pro ně. Visual Studio zpřístupní tyto knihovny DLL jako *distribuovatelné soubory* , kterou můžete v instalačním programem vaší aplikace.

Aby bylo snazší zahrnout distribuovatelné knihovny DLL s instalačním programem vaší, jsou k dispozici jako samostatné *Distribuovatelné balíčky*. Toto jsou specifické pro architekturu spustitelné soubory, které pomocí centrálního nasazení nainstalujte distribuovatelné soubory v počítači uživatele. Například vcredist\_x86.exe nainstaluje 32bitové knihovny pro x86 počítače, vcredist\_x64.exe nainstaluje 32bitové a 64bitové knihovny pro x64 počítače a vcredist\_ARM.exe nainstaluje knihovny pro ARM počítače. Doporučujeme centrálního nasazení, protože Microsoft můžete použít službu Windows Update se nezávisle aktualizovat tyto knihovny. Kromě kopií v instalaci sady Visual Studio aktuální Distribuovatelné balíčky jsou k dispozici ke stažení. Odkazy na nejnovější podporované redistribuovatelné balíčky pro aktuální a starší sady nástrojů, naleznete v části [nejnovější podporované soubory ke stažení Visual C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads). Konkrétní starší verze distribuovatelné balíčky mohou jde najít vyhledáváním [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431) pro "Distribuovatelné balíčky Visual C++".

Hlavní číslo verze balíčku opětovné distribuce nasadíte musí odpovídat verzi sady nástrojů Visual Studio používá k vytvoření aplikace a podverze musí být stejná nebo vyšší. Visual Studio 2017 a Visual Studio 2015 mají sadu nástrojů kompatibilní čísla verzí, což znamená, že Visual Studio 2017 distribuovatelné soubory může používat aplikace vytvořené s použitím nástrojů 2015. Když mohou být kompatibilní, nepodporujeme pomocí distribuovatelné soubory 2015 v aplikace vytvořené s použitím nástrojů 2017. Podporujeme jenom pomocí distribuovatelných balíčků, který je stejný jako nebo novější než vaše verze sady nástrojů.

Dalším způsobem, jak zahrnout distribuovatelné knihovny DLL s instalačním programem vaší je použití *slučovací moduly*. Tyto moduly Microsoft Installer jsou součástí a nainstalovat s instalačním programem vaší aplikace. Slučovací moduly pro distribuovatelné knihovny DLL se nacházejí v adresáři instalace sady Visual Studio v části \\VC\\Redist\MSVC\\*verze*\\MergeModules\\ . V dřívějších verzích sady Visual Studio, tyto soubory se nacházejí ve vaší \\Program Files nebo \\adresář Program Files (x86) v běžné soubory\\podadresář slučovací moduly. Další informace o použití těchto souborů naleznete v tématu [Redistribuce součástí s použitím modulů sloučení](../ide/redistributing-components-by-using-merge-modules.md).

Jednotlivé distribuovatelné knihovny DLL jsou také součástí instalace sady Visual Studio. Ve výchozím nastavení, budou nainstalovány do instalačního adresáře sady Visual Studio v \\VC\\Redist\\MSVC\\*verze* složky. *Verze* čísel může představovat různá menší čísla sestavení z jednoho společnou sadu redistribuovatelné soubory. Použijte nejnovější verzi souboru knihovny DLL, Distribuovatelný balíček či slučovací modul najít v těchto adresářích. Tyto knihovny pro místní nasazení můžete samozřejmě využít instalací ve stejném adresáři jako vaši aplikaci. Místní nasazení nedoporučujeme, protože to ztěžuje je zodpovědná za poskytování aktualizací pro vaše nasazené aplikace. Centrální nasazení pomocí distribuovatelných balíčků je upřednostňována.

Chcete-li zjistit, které knihovny DLL, je nutné znovu distribuovat s vaší aplikací, shromážděte seznam knihoven DLL, které vaše aplikace závisí. Obvykle jsou uvedeny importu knihovny vstupy do propojovacího programu. Některé knihovny, jako je například vcruntime a Universal C Runtime Library (UCRT), jsou zahrnuté ve výchozím nastavení. Pokud vaše aplikace nebo jedna z jeho závislostí používá LoadLibrary dynamicky načíst knihovnu DLL, tuto knihovnu DLL nemusí být uvedená ve vstupech do propojovacího programu. Jedním ze způsobů, jak shromáždit seznam dynamicky načtené knihovny DLL je spustit prohlížeče závislostí (depends.exe) ve vaší aplikaci, jak je popsáno v [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Bohužel tento nástroj je zastaralý a může hlásit, že nelze najít určité knihovny DLL.

Když máte seznam závislostí, porovnejte do seznamu v souboru Redist.txt v adresáři instalace sady Microsoft Visual Studio, nebo "seznam REDIST" Distribuovatelný knihoven DLL, který se odkazuje v oddíle "Soubory s Distribuovatelným kódem" z licenční podmínky pro Software Microsoftu pro vaše kopie sady Visual Studio. Visual Studio 2017, najdete v části [Distribuovatelný kód pro Microsoft Visual Studio 2017 (zahrnuje nástroje, rozšíření a soubory buildovacího serveru)](http://go.microsoft.com/fwlink/p/?linkid=823098). Visual Studio 2015, najdete v části [Distribuovatelný kód pro Microsoft Visual Studio 2015 a Microsoft Visual Studio 2015 SDK (zahrnuje soubory Buildovacího serveru a)](http://go.microsoft.com/fwlink/p/?linkid=799794). Pro sadu Visual Studio 2013, v seznamu je k dispozici online v [Distribuovatelný kód pro Microsoft Visual Studio 2013 a Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603).

Ve verzích sady Visual Studio před Visual Studio 2015, byla zahrnuta jako distribuovatelné knihovny DLL v msvc knihovny Runtime jazyka C (CRT)*verze*.dll. Spouští se v sadě Visual Studio 2015, byly funkce CRT vyčleněný do vcruntime a UCRT. UCRT je teď součástí systému ve Windows 10 spravovaných pomocí Windows Update. Je dostupná ve všech operačních systémech Windows 10. Chcete-li nasadit aplikaci do starší operační systémy, budete muset znovu distribuovat a UCRT. Starší verzi aplikace UCRT je součástí sady Visual Studio redistribuovatelné soubory, které se instaluje v operačních systémech starších než Windows 10, a pouze pokud je již nainstalována žádná verze UCRT. Instalovatelnou verzi UCRT pro starší verze systémů jako balíček aktualizace systému Microsoft, naleznete v tématu [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234) webu Microsoft Download Center.

Nelze distribuovat soubory, které jsou zahrnuty v sadě Visual Studio; jsou povolené jenom znovu distribuovat soubory, které jsou uvedeny v souboru Redist.txt nebo online seznamu "REDIST list." Ladicí verze aplikace a různé ladění jazyka Visual C++ nejsou opakovaně distribuovatelné knihovny DLL. Další informace najdete v tématu [volba metody nasazení](../ide/choosing-a-deployment-method.md).

Následující tabulka popisuje některé z Visual C++ knihovny DLL, které může vaše aplikace závisí na.

|Knihovny jazyka Visual C++|Popis|Platí pro|
|--------------------------|-----------------|----------------|
|vcruntime*version*.dll|Knihovna prostředí runtime pro nativní kód.|Aplikace, které používají normální C a C++ language spuštění a ukončení služby.|
|vccorlib*version*.dll|Knihovna prostředí runtime pro spravovaný kód.|Aplikace, které používají služby jazyka C++ pro spravovaný kód.|
|msvcp*verze*.dll a msvcp*verze*_*dotnumber*.dll|Standardní knihovny C++ pro nativní kód.|Aplikace, které používají [standardní knihovny C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*verze*.dll|Knihovna Runtime souběžnosti pro nativní kód.|Aplikace, které používají [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).|
|mfc*version*.dll|Microsoft Foundation Classes (MFC) knihovny.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md).|
|mfc*version* *language*.dll|Microsoft Foundation Classes (MFC) prostředků knihovny.|Aplikace, které používají prostředky pro konkrétní jazyk pro knihovny MFC.|
|mfc*version*u.dll|Knihovna MFC s podporou kódování Unicode.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) a vyžadující podporu kódování Unicode.|
|mfcmifc80.dll|Řízená rozhraní knihovny MFC.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) s [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*verze*.dll|Řízená knihovna MFC.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) s [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*u.dll|Řízená knihovna MFC s podporou kódování Unicode.|Aplikace, které používají [knihovny MFC](../mfc/mfc-desktop-applications.md) s [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index) a vyžadující podporu kódování Unicode.|
|vcamp*version*.dll|Knihovny AMP pro nativní kód.|Aplikace, které používají [knihovny C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) kódu.|
|vcomp*version*.dll|OpenMP – knihovny pro nativní kód.|Aplikace, které používají [C++ OpenMP – knihovny](../parallel/openmp/openmp-in-visual-cpp.md) kódu.|

> [!NOTE]
> Už nemusíte znovu distribuovat knihovnu Active Template Library jako samostatné knihovny DLL. Jeho funkcí se přesunulo na záhlaví a statická knihovna.

Další informace o postupu distribuce těchto knihoven DLL s vaší aplikací najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md). Příklady najdete v tématu [Deployment Examples](../ide/deployment-examples.md).

Obvykle není nutné distribuovat systémové knihovny DLL, protože jsou součástí operačního systému. Nicméně mohou existovat výjimky, například když vaše aplikace bude spuštěna na několika verzích operačních systémů Microsoft. V takovém případě nezapomeňte přečíst odpovídající podmínky licenční smlouvy. Také pokusí se získat systémové knihovny DLL prostřednictvím služby Windows Update, aktualizace service Pack nebo s použitím distribuovatelných balíčků poskytovaných společností Microsoft.

## <a name="see-also"></a>Viz také:

[Volba metody nasazení](../ide/choosing-a-deployment-method.md)

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)
