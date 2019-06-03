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
ms.openlocfilehash: b64fac7086dcc22199ca359a163074b967c56f95
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450616"
---
# <a name="redistributing-visual-c-files"></a>Redistribuce souborů Visual C++

> [!NOTE]
> Jste tady, protože jste hledali stahování jednoho ze souborů modulu Runtime Visual C++? Přejděte [webu společnosti Microsoft](https://www.microsoft.com/) a zadejte **distribuovatelné součásti Visual C++** do vyhledávacího pole. Stáhněte si a nainstalujte redistribuovatelný balíček pro architekturu vašeho počítače (například x64 Pokud používáte systém Windows 64-bit) a verze aplikace Visual C++ (například 2015), které potřebujete.

Při nasazení aplikace je nutné nasadit také soubory, které jsou vyžadovány pro její podporu. Pokud je některý z těchto souborů poskytován společností Microsoft, zkontrolujte, zda je povoleno jej dále distribuovat. Chcete-li zkontrolovat licenční podmínky pro Visual Studio, na odkaz licenční podmínky v dialogovém okně o aplikaci Microsoft Visual Studio v integrovaném vývojovém prostředí nebo stáhnout [licenční podmínky pro Software společnosti Microsoft](https://visualstudio.microsoft.com/license-terms/mlt687465/) souboru. K zobrazení seznamu "REDIST list", který se odkazuje v oddíle "Distribuovatelný kód" licenčních podmínek pro Software společnosti Microsoft pro některé edice sady Visual Studio, naleznete v tématu [Distribuovatelný kód pro Microsoft Visual Studio 2017 a Microsoft Visual Studio 2017 Sada SDK (zahrnuje soubory Buildovacího serveru a)](/visualstudio/productinfo/2017-redistribution-vs), nebo Visual Studio 2015, najdete v části [Distribuovatelný kód pro Microsoft Visual Studio 2015 a Microsoft Visual Studio 2015 SDK](/visualstudio/productinfo/2015-redistribution-vs). Další informace o znovu distribuovatelných souborech naleznete v tématu [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md) a [Deployment Examples](deployment-examples.md).

K nasazení souborů distribuovatelné součásti Visual C++, můžete použít Distribuovatelné balíčky Visual C++ (VCRedist\_x86.exe VCRedist\_x64.exe nebo VCRedist\_arm.exe), které jsou zahrnuty v sadě Visual Studio. V sadě Visual Studio 2017 tyto soubory lze nalézt ve složce Program Files [(x86)]\\sady Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\ MSVC\\_lib verze_ složky, kde _edition_ je edici sady Visual Studio nainstalovali, a _lib verze_ je verze knihovny, které chcete znovu distribuovat. V sadě Visual Studio 2015, tyto soubory najdete v části adresáře instalace sady Visual Studio v programových souborů [(x 86)] \Microsoft Visual Studio *verze*\VC\redist\\*národní prostředí* \\. Další možností je využít distribuovatelné slučovací moduly (soubory .msm), které v sadě Visual Studio 2017 najdete v souborech programu [(x 86)]\\sady Microsoft Visual Studio\\2017\\_edition_ \\ VC\\Redist\\MSVC\\_lib verze_\\MergeModules\\ složky. V sadě Visual Studio 2015 ty lze najít v programových souborů [(x 86)] \Common moduly\\. Je také možné nainstalovat přímo distribuovatelné součásti Visual C++ DLL v *místní složky aplikace*, což je složka, která obsahuje vaše spustitelný soubor aplikace. Z důvodů údržby, nedoporučujeme používat toto umístění instalace.

Distribuovatelné balíčky Visual C++ nainstalují a zaregistrují všechny knihovny Visual C++. Používáte-li je, je nutné nastavit jejich spuštění v cílovém systému, což je nezbytná podmínka pro instalaci aplikace. Doporučujeme používat pro nasazení právě tyto balíčky, protože umožňují automatické aktualizace knihovny Visual C++. Příklad použití těchto balíčků, najdete v části [názorný postup: Nasazení aplikace v jazyce Visual C++ s použitím redistribuovatelného balíčku Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Každý balíček Visual C++ Redistributable zkontroluje existenci novější verze na počítači. Pokud je novější verze, že balíček není nainstalovaný. V sadě Visual Studio 2015, Distribuovatelné balíčky zobrazit chybová zpráva s oznámením při nastavení, nepovedlo se spustit. Pokud balíček je spuštěn s použitím **/quiet** příznak, žádná chybová zpráva se zobrazí. V obou případech se zaznamená chyba pomocí instalačního programu Microsoft a chybného výsledku je vrátit zpět volajícímu. Od balíčků sady Visual Studio 2015 se můžete vyhnout této chybě kontrolou registru a zjistěte, zda je nainstalována novější verze. Aktuálně nainstalovanou verzi je uložen v \Microsoft\VisualStudio HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node]\\_verze vs_\VC\Runtimes\\{x86 | x64 | Klíč ARM}, kde _verze vs_ je číslo verze pro Visual Studio (14.0 pro Visual Studio 2015 i Visual Studio 2017, protože aktualizace 2017 redistributable je binární kompatibilní s verzí 2015), a pokud je klíč ARM, x 86 nebo x64 v závislosti na nainstalovaných vcredist verze pro platformu. (Není nutné ke kontrole podklíči Wow6432Node, pokud chcete zobrazit verzi nainstalovaného x86 nepoužíváte RegEdit balíček x x64 platformy.) Číslo verze je uloženo v řetězcové hodnotě REG_SZ **verze** a také v sadě **hlavní**, **menší**, **Bld**a **Rbld** hodnoty REG_DWORD. Aby se zabránilo chybě při instalaci, je musíte instalace balíčku opětovné distribuce vynechat, pokud aktuálně nainstalovaná verze je novější.

Používáte-li slučovací modul, který obsahuje DLL Knihovny jazyka Visual C++, je třeba jej zahrnout do balíček Instalační služby systému Windows (nebo podobného instalačního balíčku), který používáte k nasazení aplikace. Další informace najdete v tématu [Redistribuce podle pomocí slučovacích modulů](redistributing-components-by-using-merge-modules.md). Příklad najdete v tématu [názorný postup: Nasazení Visual C++ Application By Using a Setup Project](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), které zároveň ukazuje vytvoření instalačního balíčku pomocí programu InstallShield Limited Edition.

## <a name="potential-run-time-errors"></a>Potenciální běhové chyby

Pokud Windows nelze najít jeden z redistribuovatelné knihovny DLL, které jsou požadované pro vaší aplikaci, může zobrazí zpráva podobná této: "Tuto aplikaci se nepodařilo spustit, protože *knihovny*DLL nebyla nalezena. Opětovnou instalací aplikace může tento problém vyřešit."

Chcete-li vyřešit tento druh chyby, ujistěte se, že instalačním programem vaší aplikace správně sestavena a že distribuovatelné knihovny jsou správně nasazeny v cílovém systému. Další informace najdete v tématu [Principy závislostí v aplikacích Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Redistribuce s použitím modulů sloučení](redistributing-components-by-using-merge-modules.md)|Popisuje, jak používat Visual C++ distribuovatelné slučovací moduly pro instalaci vizuál C++ knihoven modulu runtime jako sdílené knihovny DLL do složky %windir%\system32\.|
|[Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++](redistributing-visual-cpp-activex-controls.md)|Popisuje, jak distribuovat aplikaci používající ovládací prvky technologie ActiveX.|
|[Redistribuce knihovny MFC](redistributing-the-mfc-library.md)|Popisuje, jak distribuovat aplikaci používající knihovnu MFC.|
|[Redistribuce aplikace ATL](redistributing-an-atl-application.md)|Popisuje, jak distribuovat aplikaci, která používá knihovnu ATL. Od verze Visual Studio 2012, je požadována žádná redistributable knihovna pro knihovnu ATL.|
|[Příklady nasazení](deployment-examples.md)|Odkazuje na příklady demonstrující, jak nasadit aplikace jazyka Visual C++.|
|[Nasazení aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)|Představuje koncepty a technologie nasazení Visual C++.|