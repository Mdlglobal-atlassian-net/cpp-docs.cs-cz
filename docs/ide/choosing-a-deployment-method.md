---
title: "Volba metody nasazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e4336f200f736ea7656af11c7c7c43ca32f27f9
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="choosing-a-deployment-method"></a>Volba metody nasazení
Pokud vaše aplikace Visual C++ je samostatný a dá se nasadit pomocí kopie příkazu, doporučujeme použít instalační služby systému Windows pro nasazení. Instalační služba systému Windows podporuje instalace, opravy a odinstalace a také atomické aktualizace souborů aplikace, závislostí a položek registru.  
  
> [!NOTE]
>  I když [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) nasazení pro Visual C++ nativních aplikací je možné v sadě Visual Studio, vyžaduje dodatečné kroky. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Knihovny Visual C++ jsou sdílené knihovny DLL  
 Protože knihovny Visual C++ instaluje Instalační služba sady Visual Studio do adresáře %windir%\system32\, budou vyvíjené aplikace jazyka Visual C++, které na těchto knihovnách závisejí, fungovat podle očekávání. Chcete-li však aplikace nasazovat do počítačů, ve kterých není sada Visual Studio, doporučujeme zajistit, aby byly knihovny do těchto počítačů nainstalovány spolu s aplikací.  
  
## <a name="redistributing-visual-c-libraries"></a>Distribuce knihoven Visual C++  
 Ve svých nasazeních můžete distribuovat jakoukoli verzi knihovny Visual C++, která disponuje licencí pro distribuci. Můžete je nasadit třemi způsoby:  
  
-   Centrální nasazení pomocí Distribuovatelné balíčky, který se nainstaluje knihovny jazyka Visual C++ jako sdílené knihovny DLL v %windir%\system32\\. (Instalace do této složky vyžaduje oprávnění správce.) Můžete vytvořit skript nebo instalační program, který spustí distribuovatelný balíček před instalací aplikace do cílového počítače. Distribuovatelné balíčky jsou k dispozici pro platformy x86, x64 a ARM (VCRedist_x86.exe, VCRedist_x64.exe nebo VCRedist_arm.exe). Visual Studio obsahuje tyto balíčky v % ProgramFiles (x86) %\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. Také si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793). (Na webu Stažení softwaru, vyhledejte "distribuovatelného balíčku Visual C++ *verze sady Visual Studio a aktualizace*" odpovídající vaší aplikace. Pokud jste například k sestavení aplikace použili sadu Visual Studio 2012 s aktualizací 4, vyhledejte „Distribuovatelný balíček Visual C++ 2012 s aktualizací 4“.) Informace o použití redistribuovatelného balíčku najdete v tématu [návod: nasazení Visual C++ aplikace s použitím redistribuovatelného balíčku Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
-   Centrální nasazení s použitím slučovacích modulů, z nichž každý nainstaluje konkrétní knihovny Visual C++ jako sdílené knihovny DLL v %windir%\system32\\. (Instalace do této složky vyžaduje oprávnění správce.) Slučovací moduly se stanou součástí instalačního souboru .msi pro vaši aplikaci. Visual C++ redistributable slučovacích modulů jsou zahrnuté v sadě Visual Studio v \Program soubory (x86) \Common Files\Merge moduly\\. Další informace najdete v tématu [Redistribuce podle použití slučovacích modulů](../ide/redistributing-components-by-using-merge-modules.md).  
  
-   Místní nasazení, ve kterém můžete zkopírovat konkrétní knihovny DLL jazyka Visual C++ z instalace sady Visual Studio – obvykle ve \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and je nainstalujte na cílových počítačích ve stejné složce jako spustitelný soubor aplikace. Tuto metodu nasazení můžete využít k tomu, abyste povolili instalaci uživatelům, kteří nemají oprávnění správce, případně u aplikací, které lze spouštět ze sdíleného umístění v síti.  
  
 Pokud nasazení používá redistributable slučovacích modulů a instalace je spuštěna uživatelem, který nemá práva správce, nenainstalují se knihovny DLL jazyka Visual C++ a aplikace se nespustí. Instalační programy aplikací vytvořené pomocí slučovacích modulů, které umožňují instalaci pro jednotlivé uživatele, navíc nainstalují knihovny do sdíleného umístění, které ovlivňuje všechny uživatele systému. Místní nasazení můžete použít k instalaci požadované knihovny DLL jazyka Visual C++ v adresáři aplikace určitého uživatele bez ovlivnění jiných uživatelů nebo nutnosti práva správce. Protože tak můžou vzniknout problémy použitelnost, nedoporučujeme místní nasazení knihoven DLL Visual C++ redistributable.  
  
 Nesprávné nasazení knihoven Visual C++ může způsobit chyby prostředí Runtime během spuštění aplikace, která na knihovnách závisí. Až se operační systém načte aplikaci, použije pořadí vyhledávání popsané v [funkce LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>Dynamické propojení je lepší než statické  
 Doporučujeme vyhnout statické propojení, když provedete opětovnou distribuci knihovny jazyka Visual C++. Tento typ propojení téměř nikdy výrazně nezlepší výkon aplikace, a naopak prakticky pokaždé zvyšuje náklady na obsluhu. Představte si například aplikaci staticky propojenou s knihovnou, kterou je třeba aktualizovat pomocí vylepšení zabezpečení – aplikace nebude moci aktualizace využívat, pokud ji znovu nezkompilujete a nenasadíte. Namísto toho doporučujeme aplikace dynamicky propojit s knihovnami, na kterých jsou závislé, aby bylo možné knihovny aktualizovat bez ohledu na to, kde jsou nasazeny.  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Příklady nasazení](../ide/deployment-examples.md)