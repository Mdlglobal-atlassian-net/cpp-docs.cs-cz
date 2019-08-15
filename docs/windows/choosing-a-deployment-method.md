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
ms.openlocfilehash: e2281effaa94c32454e88100c8b7020961f748d9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514839"
---
# <a name="choosing-a-deployment-method"></a>Volba metody nasazení

Pokud vaše vizuální C++ aplikace není samostatná a dá se nasadit pomocí příkazu pro kopírování, doporučujeme pro nasazení použít instalační služba systému Windows. Instalační služba systému Windows podporuje instalace, opravy a odinstalace a také atomické aktualizace souborů aplikace, závislostí a položek registru.

> [!NOTE]
>  I když nasazení [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) pro C++ Visual Native aplikace je možné v aplikaci Visual Studio, vyžaduje další kroky. Další informace naleznete v tématu [nasazení ClickOnce pro vizuální C++ aplikace](clickonce-deployment-for-visual-cpp-applications.md).

## <a name="visual-c-libraries-are-shared-dlls"></a>Knihovny Visual C++ jsou sdílené knihovny DLL

Protože knihovny Visual C++ instaluje Instalační služba sady Visual Studio do adresáře %windir%\system32\, budou vyvíjené aplikace jazyka Visual C++, které na těchto knihovnách závisejí, fungovat podle očekávání. Chcete-li však aplikace nasazovat do počítačů, ve kterých není sada Visual Studio, doporučujeme zajistit, aby byly knihovny do těchto počítačů nainstalovány spolu s aplikací.

## <a name="redistributing-visual-c-libraries"></a>Distribuce knihoven Visual C++

Ve svých nasazeních můžete distribuovat jakoukoli verzi knihovny Visual C++, která disponuje licencí pro distribuci. Můžete je nasadit třemi způsoby:

- Centrální nasazení pomocí redistribuovatelných balíčků, které instalují knihovny vizuálů C++ jako sdílené knihovny DLL v%windir%\system32\\. (Instalace do této složky vyžaduje oprávnění správce.) Můžete vytvořit skript nebo instalační program, který spustí distribuovatelný balíček před instalací aplikace do cílového počítače. Distribuovatelné balíčky jsou k dispozici pro platformy x86, x64 a ARM (VCRedist_x86.exe, VCRedist_x64.exe nebo VCRedist_arm.exe). Visual Studio zahrnuje tyto balíčky v% ProgramFiles (x86)% \ Microsoft Visual Studio `version`\VC\Redist\\`locale ID`.\\ Můžete je také stáhnout z webu [Microsoft Download Center](https://www.microsoft.com/download). (Pomocí vyhledávacího pole na webu služby Stažení softwaru vyhledejte "Visual C++ Redistributable Package *a verzi sady Visual Studio*, které odpovídají vaší aplikaci. Pokud jste například použili sadu Visual Studio 2015 Update 3 k sestavení aplikace, vyhledejte "Visual C++ redistributable package 2015 Update 3".) Informace o tom, jak použít Distribuovatelný balíček, najdete v tématu [Názorný postup: Nasazení vizuální C++ aplikace pomocí balíčku Visual C++ Redistributable Package.](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)

- Centrální nasazení pomocí slučovacích modulů, z nichž každý nainstaluje konkrétní vizuální C++ knihovnu jako SDÍLENOU knihovnu DLL v%windir%\system32\\. (Instalace do této složky vyžaduje oprávnění správce.) Slučovací moduly se stanou součástí instalačního souboru .msi pro vaši aplikaci. Moduly C++ Visual Redistributable Merge jsou součástí sady Visual Studio v modulech\\\Program Files (x86) \Common Files\Merge. Další informace naleznete v tématu [Redistribuce pomocí slučovacích modulů](redistributing-components-by-using-merge-modules.md).

- Místní nasazení, ve kterém kopírujete konkrétní vizuální C++ knihovny DLL z instalace sady Visual Studio – obvykle ve složce \Program Files (x86) \Microsoft `version`Visual\\Studio \VC\Redist`platform`\\\`library` – a nainstalujte je do cílových počítačů ve stejné složce jako spustitelný soubor aplikace. Tuto metodu nasazení můžete využít k tomu, abyste povolili instalaci uživatelům, kteří nemají oprávnění správce, případně u aplikací, které lze spouštět ze sdíleného umístění v síti.

Pokud nasazení používá redistribuovatelné slučovací moduly a instalace je spuštěna uživatelem, který nemá oprávnění správce, nejsou nainstalovány vizuální C++ knihovny DLL a aplikace nebude spuštěna. Instalační programy aplikací vytvořené pomocí slučovacích modulů, které umožňují instalaci pro jednotlivé uživatele, navíc nainstalují knihovny do sdíleného umístění, které ovlivňuje všechny uživatele systému. Místní nasazení můžete použít k instalaci požadovaných vizuálních C++ knihoven DLL do adresáře aplikace konkrétního uživatele, aniž by to ovlivnilo jiné uživatele nebo vyžadovalo oprávnění správce. Vzhledem k tomu, že to může vytvořit problémy se službou, nedoporučujeme místní C++ nasazení Visual Redistributable dll.

Nesprávné nasazení knihoven Visual C++ může způsobit chyby prostředí Runtime během spuštění aplikace, která na knihovnách závisí. Když operační systém načte aplikaci, použije pořadí hledání popsané v [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="dynamic-linking-is-better-than-static-linking"></a>Dynamické propojení je lepší než statické

Doporučujeme, abyste se vyhnuli statickému propojení při redistribuci vizuálních C++ knihoven. Tento typ propojení téměř nikdy výrazně nezlepší výkon aplikace, a naopak prakticky pokaždé zvyšuje náklady na obsluhu. Představte si například aplikaci staticky propojenou s knihovnou, kterou je třeba aktualizovat pomocí vylepšení zabezpečení – aplikace nebude moci aktualizace využívat, pokud ji znovu nezkompilujete a nenasadíte. Namísto toho doporučujeme aplikace dynamicky propojit s knihovnami, na kterých jsou závislé, aby bylo možné knihovny aktualizovat bez ohledu na to, kde jsou nasazeny.

## <a name="see-also"></a>Viz také:

[Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Příklady nasazení](deployment-examples.md)
