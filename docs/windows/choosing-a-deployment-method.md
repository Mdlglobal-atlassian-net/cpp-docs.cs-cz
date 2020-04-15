---
title: Volba metody nasazení
ms.date: 03/14/2019
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
ms.openlocfilehash: 633b76458fdc24ef9ba551d8209c5c99720df37e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377395"
---
# <a name="choosing-a-deployment-method"></a>Volba metody nasazení

Pokud vaše aplikace Visual C++ není samostatná a dá se nasadit pomocí příkazu copy, doporučujeme použít pro nasazení Instalační službu systému Windows. Instalační služba systému Windows podporuje instalace, opravy a odinstalace a také atomické aktualizace souborů aplikace, závislostí a položek registru.

> [!NOTE]
> Přestože [clickonce](/visualstudio/deployment/clickonce-security-and-deployment) nasazení pro nativní aplikace Visual C++ je možné v sadě Visual Studio, vyžaduje další kroky. Další informace naleznete v [tématu ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Knihovny Visual C++ jsou sdílené knihovny DLL

Protože knihovny Visual C++ instaluje Instalační služba sady Visual Studio do adresáře %windir%\system32\, budou vyvíjené aplikace jazyka Visual C++, které na těchto knihovnách závisejí, fungovat podle očekávání. Chcete-li však aplikace nasazovat do počítačů, ve kterých není sada Visual Studio, doporučujeme zajistit, aby byly knihovny do těchto počítačů nainstalovány spolu s aplikací.

## <a name="redistributing-visual-c-libraries"></a>Distribuce knihoven Visual C++

Ve svých nasazeních můžete distribuovat jakoukoli verzi knihovny Visual C++, která disponuje licencí pro distribuci. Můžete je nasadit třemi způsoby:

- Centrální nasazení pomocí redistribuovatelných balíčků, které instalují knihovny Visual C++ jako sdílené\\knihovny DLL v %windir%\system32 . (Instalace v této složce vyžaduje práva správce.) Před instalací aplikace do cílového počítače můžete vytvořit skript nebo instalační program, ve které bude spuštěn redistribuovatelný balíček. Distribuovatelné balíčky jsou k dispozici pro platformy x86, x64 a ARM (VCRedist_x86.exe, VCRedist_x64.exe nebo VCRedist_arm.exe). Visual Studio obsahuje tyto balíčky v %ProgramFiles(x86)%\Microsoft `version`Visual\\`locale ID`\\Studio \VC\Redist . Můžete si je také stáhnout ze služby [Stažení softwaru](https://www.microsoft.com/download). (Pomocí vyhledávacího pole v centru pro stahování vyhledejte *verzi a aktualizaci*sady Visual C++ Redistributable Package Visual Studio, která odpovídá vaší aplikaci. Pokud jste například k vytvoření aplikace použili aktualizaci 3 visual studia 2015, vyhledejte "Visual C++ Redistributable Package 2015 update 3".) Informace o použití redistribuovatelného balíčku naleznete v [návodu: Nasazení aplikace Visual C++ pomocí balíčku Visual C++ Redistributable Package](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

- Centrální nasazení pomocí slučovacích modulů, z nichž každý nainstaluje určitou knihovnu Visual C++ jako sdílenou knihovnu DLL v %windir%\system32\\. (Instalace do této složky vyžaduje práva správce.) Slučovací moduly se stanou součástí instalačního souboru MSI pro vaši aplikaci. Redistribuovatelné slučovací moduly Visual C++ jsou součástí sady Visual Studio v \Program\\Files (x86)\Common Files\Merge Modules . Další informace naleznete [v tématu Redistributing Using Merge Modules](redistributing-components-by-using-merge-modules.md).

- Místní nasazení, ve kterém zkopírujete konkrétní knihovny DLL jazyka Visual C++ z instalace sady Visual `version`Studio – obvykle\\`platform`\\`library`v \Program Files (x86)\Microsoft Visual Studio \VC\Redist \— a nainstalujete je do cílových počítačů ve stejné složce jako spustitelný soubor aplikace. Tuto metodu nasazení můžete využít k tomu, abyste povolili instalaci uživatelům, kteří nemají oprávnění správce, případně u aplikací, které lze spouštět ze sdíleného umístění v síti.

Pokud nasazení používá redistribuovatelné slučovací moduly a instalaci spustí uživatel, který nemá práva správce, nejsou nainstalovány knihovny DLL jazyka Visual C++ a aplikace nebude spuštěna. Instalační programy aplikací vytvořené pomocí slučovacích modulů, které umožňují instalaci pro jednotlivé uživatele, navíc nainstalují knihovny do sdíleného umístění, které ovlivňuje všechny uživatele systému. Místní nasazení můžete použít k instalaci požadovaných knihoven DLL jazyka Visual C++ do adresáře aplikace konkrétního uživatele, aniž byste ovlivnili ostatní uživatele nebo vyžadovali práva správce. Vzhledem k tomu, že to může způsobit problémy s provozuschopností, nedoporučujeme místní nasazení knihoven DLL redistribuovatelných aplikací Visual C++.

Nesprávné nasazení knihoven Visual C++ může způsobit chyby prostředí Runtime během spuštění aplikace, která na knihovnách závisí. Když operační systém načte aplikaci, použije pořadí hledání popsané v [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="dynamic-linking-is-better-than-static-linking"></a>Dynamické propojení je lepší než statické

Doporučujeme vyhnout se statické propojení při redistribuci visual c++ knihovny. Tento typ propojení téměř nikdy výrazně nezlepší výkon aplikace, a naopak prakticky pokaždé zvyšuje náklady na obsluhu. Představte si například aplikaci staticky propojenou s knihovnou, kterou je třeba aktualizovat pomocí vylepšení zabezpečení – aplikace nebude moci aktualizace využívat, pokud ji znovu nezkompilujete a nenasadíte. Namísto toho doporučujeme aplikace dynamicky propojit s knihovnami, na kterých jsou závislé, aby bylo možné knihovny aktualizovat bez ohledu na to, kde jsou nasazeny.

## <a name="see-also"></a>Viz také

[Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce Zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Příklady nasazení](deployment-examples.md)
