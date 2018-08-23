---
title: Sestavování programů jazyka C/C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs:
- C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fa07308d04d14395b0ca9773e2a0c81ed0c2bc2
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464821"
---
# <a name="building-cc-programs"></a>Sestavování programů v jazyku C/C++

Můžete vytvářet projekty Visual C++ v sadě Visual Studio nebo na příkazovém řádku. Integrované vývojové prostředí sady Visual Studio používá [MSBuild](../build/msbuild-visual-cpp.md) k sestavení projektů a řešení. Na příkazovém řádku můžete použít k sestavení projektů jednoduchý kompilátor C/C++ (cl.exe) a linker (link.exe). K sestavení projektů složitější na příkazovém řádku, můžete pomocí nástroje MSBuild nebo [NMAKE](../build/nmake-reference.md). Přehled o tom, jak pomocí sady Visual Studio k vytváření projektů a řešení, naleznete v tématu [kompilování a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
## <a name="in-this-section"></a>V tomto oddílu  

[Sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)  
Popisuje, jak použít rozhraní IDE sady Visual Studio k vytvoření projektu jazyka C/C++.  
  
[Sestavení kódu C/C++ na příkazovém řádku](../build/building-on-the-command-line.md)  
Popisuje, jak pomocí příkazového řádku kompilátoru jazyka C/C++ a vytváření buildů, které jsou zahrnuty v sadě Visual Studio.  
  
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
Popisuje model nasazení pro aplikace Windows Desktop, založené na představu o izolovaných aplikací a sestavení vedle sebe.  
  
[Referenční zdroje k sestavení programu v jazyce C/C++](../build/reference/c-cpp-building-reference.md)  
Poskytuje odkazy na články, referenční informace o programu sestavení v jazyce C++, možnosti kompilátoru a propojovacího programu a různé nástroje pro vytváření.  
  
[Konfigurace Visual C++ pro 64bitové cíle x64](../build/configuring-programs-for-64-bit-visual-cpp.md)  
Popisuje postup konfigurace sady Visual Studio a příkazový řádek použijte 64bitovou sadu nástrojů a cílit na 64bitové architektury a pokud kód je přesunut do 64bitové architektury, tento článek popisuje běžné problémy s migrací.  
  
[Konfigurace Visual C++ pro procesory ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
Popisuje konvence používají procesory ARM a popisuje běžné problémy s migrací při kódu se přesune na architektury ARM.  
  
[Konfigurace programů pro Windows XP](../build/configuring-programs-for-windows-xp.md)  
Popisuje, jak nastavit sadu nástrojů platformy pro vývoj pro Windows XP cíl.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kompilace a sestavení](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Popisuje nástroje a systém sestavení Visual Studio.