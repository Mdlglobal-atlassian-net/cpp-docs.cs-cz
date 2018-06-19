---
title: Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku | Microsoft Docs
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- include
- Lib
- Path
dev_langs:
- C++
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b72f13fe25330b81a48d1447b707bdc4626ab3f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381132"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku

Nástroje pro sestavení příkazového řádku Visual C++ vyžadovat několik proměnné prostředí, které jsou přizpůsobené pro konfiguraci instalace a sestavení. Při instalaci zatížení C++ pomocí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalační program, vytvoří vlastní příkazové soubory nebo dávkové soubory, které nastavení proměnných prostředí vyžaduje. Instalační program použije tyto soubory příkaz k vytvoření zástupce pro nabídky Start otevřít okno příkazového řádku vývojáře. Tyto zástupce nastavení proměnných prostředí pro konkrétní konfigurace sestavení. Pokud chcete pomocí nástroje příkazového řádku, můžete spustit jeden z těchto zástupce, nebo můžete otevřít okno prostý příkazového řádku a poté spustíte jeden z vlastního příkazu soubory, které chcete nastavit konfigurační prostředí sestavení, sami. Další informace najdete v tématu [sestavení kódu C/C++ v příkazovém řádku](building-on-the-command-line.md).  
  
Nástroje příkazového řádku Visual C++ pomocí proměnné prostředí PATH, TMP, zahrnout, LIB a LIBPATH a také použít jiné proměnné prostředí specifické pro vaše nainstalovaného nástroje, platformy a sady SDK. I jednoduchou [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalace může nastavení než 20 nebo více proměnných prostředí. Protože hodnoty těchto proměnných prostředí jsou specifické pro vaši instalaci a zvoleného konfiguraci sestavení a může změnit produktu aktualizace nebo upgrady, důrazně doporučujeme použít zástupce příkazového řádku vývojáře nebo jeden z soubory příkazů vlastní nastavení, namísto nastavování si je v prostředí Windows sami. 

Pokud chcete zobrazit, které proměnné prostředí se nastavují pomocí zástupce příkazového řádku vývojáře, můžete příkaz SET. Otevřete okno příkazového řádku prostý a zachycení výstup příkazu SET pro směrný plán. Otevřete okno příkazového řádku vývojáře a zachycení výstup příkazu SET pro porovnání. Diff nástroje, jako je jedna integrovaná v prostředí Visual Studio IDE může být užitečné k porovnání proměnných prostředí a zjistit, co se nastavuje pomocí příkazového řádku vývojáře. Informace o proměnných prostředí používá kompilátoru a linkeru najdete v tématu [proměnné prostředí CL](../build/reference/cl-environment-variables.md) a [proměnné prostředí LINK](../build/reference/link-environment-variables.md).  
  
> [!NOTE]
>  Několik nástroje příkazového řádku nebo možnosti nástroje může vyžadovat oprávnění správce. Pokud máte problémy s oprávněním, když je budete používat, doporučujeme, otevřete okno příkazového řádku vývojáře pomocí **spustit jako správce** možnost. Ve Windows 10, klikněte pravým tlačítkem myši a místní nabídce pro okno příkazového řádku, a potom vyberte **Další**, **spustit jako správce**.  
  
## <a name="see-also"></a>Viz také  

[Vytvoření kódu C/C++ v příkazovém řádku](../build/building-on-the-command-line.md)   
[Propojování](../build/reference/linking.md)   
[Možnosti linkeru](../build/reference/linker-options.md)   
[Kompilace programu C/C++](../build/reference/compiling-a-c-cpp-program.md)   
[Možnosti kompilátoru](../build/reference/compiler-options.md)