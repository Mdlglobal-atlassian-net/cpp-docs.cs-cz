---
title: "Sestavení C/C++ – programy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs: C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc4b8c70c7be83e108104cf91d4629072a9324f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-programs"></a>Sestavování programů v jazyku C/C++

Můžete vytvořit projekty Visual C++ v sadě Visual Studio nebo na příkazovém řádku. Visual Studio IDE používá [MSBuild](../build/msbuild-visual-cpp.md) vytvářet projekty a řešení. Na příkazovém řádku můžete kompilátor C/C++ (cl.exe) a linkeru (link.exe) k vytvoření jednoduché projektů. K vytvoření složitějších projektů, na příkazovém řádku, můžete použít nástroje MSBuild nebo [NMAKE](../build/nmake-reference.md). Přehled o tom, jak používat [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] vytvářet projekty a řešení, najdete v části [kompilaci a sestavování](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
## <a name="in-this-section"></a>V tomto oddílu  

[Sestavení projektů C++ v sadě Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)  
Popisuje, jak pomocí prostředí Visual Studio IDE sestavení projektu C/C++.  
  
[Sestavení kódu C/C++ na příkazovém řádku](../build/building-on-the-command-line.md)  
Popisuje, jak používat C/C++ kompilátoru příkazového řádku a nástroje, které jsou zahrnuté v sadě Visual Studio pro vytváření.  
  
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
Popisuje model nasazení pro aplikace Windows Desktop, založené na nápad izolovaných aplikací a souběžně sdílená sestavení.  
  
[Referenční zdroje k sestavení programu v jazyce C/C++](../build/reference/c-cpp-building-reference.md)  
Obsahuje odkazy na články odkaz o programu sestavování v jazycích C++, možnosti kompilátoru a linkeru a různé nástroje pro sestavení.  
  
[Konfigurace Visual C++ pro 64bitové cíle x64](../build/configuring-programs-for-64-bit-visual-cpp.md)  
Popisuje postup konfigurace sady Visual Studio a příkazového řádku použijte 64bitovou sadu nástrojů a cílové architektury 64-bit a popisuje běžné problémy s migrací, pokud kód je přesunuta do 64bitové architektury.  
  
[Konfigurace Visual C++ pro procesory ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
Popisuje konvence používané procesory ARM a popisuje běžné problémy s migrací, pokud kód je přesunuta do architektury ARM.  
  
[Konfigurace programů pro Windows XP](../build/configuring-programs-for-windows-xp.md)  
Popisuje, jak nastavit sada nástrojů platformy na vývoj pro Windows XP cíl.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kompilace a sestavení](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Popisuje nástroje a systém sestavení sady Visual Studio.