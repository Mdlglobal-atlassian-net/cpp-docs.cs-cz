---
title: Volba metody nasazení
ms.date: 11/04/2016
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
ms.openlocfilehash: e755ad44d088dca77f012569cd3783079cd23f86
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739709"
---
# <a name="choosing-a-deployment-method"></a>Volba metody nasazení

Pokud vaše aplikace Visual C++ je samostatný a je možné nasadit pomocí příkazu Kopírovat, doporučujeme použít instalační služby systému Windows pro nasazení. Instalační služba systému Windows podporuje instalace, opravy a odinstalace a také atomické aktualizace souborů aplikace, závislostí a položek registru.

> [!NOTE]
>  I když [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) nasazení pro nativní aplikace Visual C++ je možné v sadě Visual Studio, vyžaduje však další kroky. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Knihovny Visual C++ jsou sdílené knihovny DLL

Protože knihovny Visual C++ instaluje Instalační služba sady Visual Studio do adresáře %windir%\system32\, budou vyvíjené aplikace jazyka Visual C++, které na těchto knihovnách závisejí, fungovat podle očekávání. Chcete-li však aplikace nasazovat do počítačů, ve kterých není sada Visual Studio, doporučujeme zajistit, aby byly knihovny do těchto počítačů nainstalovány spolu s aplikací.

## <a name="redistributing-visual-c-libraries"></a>Distribuce knihoven Visual C++

Ve svých nasazeních můžete distribuovat jakoukoli verzi knihovny Visual C++, která disponuje licencí pro distribuci. Můžete je nasadit třemi způsoby:

- Centrální nasazení pomocí distribuovatelných balíčků, které nainstalují knihovny Visual C++ jako sdílených DLL v %windir%\system32\\. (Instalace do této složky vyžaduje oprávnění správce.) Můžete vytvořit skript nebo instalační program, který spustí distribuovatelný balíček před instalací aplikace do cílového počítače. Distribuovatelné balíčky jsou k dispozici pro platformy x86, x64 a ARM (VCRedist_x86.exe, VCRedist_x64.exe nebo VCRedist_arm.exe). Visual Studio obsahuje tyto balíčky v % ProgramFiles (x86) %\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Můžete také stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793). (Použijte vyhledávací pole pro hledání v Centru pro stahování "Distribuovatelný balíček Visual C++ *verze sady Visual Studio a aktualizace*", který odpovídá vaší aplikace. For example, pokud jste k sestavení aplikace použili Visual Studio 2015 update 3, vyhledejte "Visual C++ Redistributable Package 2015 update 3".) Informace o tom, jak pomocí distribuovatelných balíčků naleznete v tématu [názorný postup: Nasazení aplikace v jazyce Visual C++ s použitím redistribuovatelného balíčku Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Centrální nasazení pomocí slučovacích modulů, z nichž každý nainstaluje konkrétní knihovnu Visual C++ jako sdílenou knihovnu DLL do %windir%\system32\\. (Instalace do této složky vyžaduje oprávnění správce.) Slučovací moduly se stanou součástí instalačního souboru .msi pro vaši aplikaci. Visual C++ distribuovatelné slučovací moduly jsou zahrnuty v sadě Visual Studio v \Program soubory (x86) \Common moduly\\. Další informace najdete v tématu [Redistribuce podle pomocí slučovacích modulů](../ide/redistributing-components-by-using-merge-modules.md).

- Místní nasazení, ve kterém zkopírujete konkrétní knihovny DLL jazyka Visual C++ v instalaci sady Visual Studio – obvykle v \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and nainstalují do cílových počítačů do stejné složky jako spustitelný soubor aplikace. Tuto metodu nasazení můžete využít k tomu, abyste povolili instalaci uživatelům, kteří nemají oprávnění správce, případně u aplikací, které lze spouštět ze sdíleného umístění v síti.

Pokud nasazení využívá distribuovatelné slučovací moduly a instalace je spuštěna uživatelem, který nemá oprávnění správce, nenainstalují se knihovny DLL jazyka Visual C++ a aplikace se nespustí. Instalační programy aplikací vytvořené pomocí slučovacích modulů, které umožňují instalaci pro jednotlivé uživatele, navíc nainstalují knihovny do sdíleného umístění, které ovlivňuje všechny uživatele systému. Místní nasazení můžete použít k instalaci požadovaných knihoven DLL Visual C++ v adresáři aplikace konkrétního uživatele, aniž by tím ovlivnili ostatní uživatele nebo byla nutná oprávnění správce. Protože to může způsobit potíže s obsluhou, místní nasazení knihoven DLL jazyka Visual C++ redistributable nedoporučujeme.

Nesprávné nasazení knihoven Visual C++ může způsobit chyby prostředí Runtime během spuštění aplikace, která na knihovnách závisí. Když operační systém načítá aplikaci, používá pořadí vyhledávání, které jsou popsané v [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)

## <a name="dynamic-linking-is-better-than-static-linking"></a>Dynamické propojení je lepší než statické

Doporučujeme, abyste je velmi riskantní statické propojování při redistribuci knihoven Visual C++. Tento typ propojení téměř nikdy výrazně nezlepší výkon aplikace, a naopak prakticky pokaždé zvyšuje náklady na obsluhu. Představte si například aplikaci staticky propojenou s knihovnou, kterou je třeba aktualizovat pomocí vylepšení zabezpečení – aplikace nebude moci aktualizace využívat, pokud ji znovu nezkompilujete a nenasadíte. Namísto toho doporučujeme aplikace dynamicky propojit s knihovnami, na kterých jsou závislé, aby bylo možné knihovny aktualizovat bez ohledu na to, kde jsou nasazeny.

## <a name="see-also"></a>Viz také:

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Příklady nasazení](../ide/deployment-examples.md)
