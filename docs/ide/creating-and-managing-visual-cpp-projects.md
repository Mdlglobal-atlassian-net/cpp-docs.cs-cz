---
title: Vytváření a spravování projektů Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vcprojects
- creatingmanagingVC
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f56ee748738cd67199348c93272a9cd2ed564e2c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685696"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Vytváření a spravování projektů Visual C++ založené na MSBuild
Nástroj MSBuild je systém nativní sestavení jazyka Visual C++ a je obvykle že nejlepší vytvořit systém pro aplikace UWP, jakož i desktopových aplikací, které používají knihovny MFC nebo ATL. Nástroj MSBuild je úzce integrovaná s Visual Studio IDE a systém projektu, ale můžete ho použít také z příkazového řádku. Spouští se v sadě Visual Studio 2017, Visual C++ podporuje [CMake a jiných systémů než MSBuild prostřednictvím funkce Otevřít složku](non-msbuild-projects.md).

Založené na MSBuild projekt obsahuje soubor projektu ve formátu XML (.vcxproj), který určuje všechny soubory a prostředky potřebné pro kompilaci programu, jakož i další nastavení konfigurace, například cílové platformy (x 86, x64 nebo ARM) a určuje, zda vytváříte verzi nebo verzi ladicí program. Jsou součástí projektu (nebo mnoha projektů) *řešení*, třeba řešení může obsahovat několik projektů knihovny DLL systému Win32 a jeden Konzolová aplikace Win32, který používá tyto knihovny DLL. Při sestavování projektu stroji MSBuild engine využívá soubor projektu a vytváří spustitelný soubor a/nebo jakékoli vlastní výstup, který jste zadali.

Můžete vytvářet projekty Visual C++ výběrem **souboru &#124; nový &#124; projektu**, zajištění, že je vybraná Visual C++ v levém podokně a následným výběrem ze seznamu šablon projektu v prostředním podokně. Po kliknutí na šablonu v mnoha případech průvodce se zobrazí, které vám umožní nastavit různé vlastnosti projektu před vytvořením projektu. Můžete zobrazit a upravit tyto vlastnosti později pomocí stránky vlastností projektu (**projektu &#124; vlastnosti**).  
  
 Můžete také vytvořit nové projekty podle:  
  
-   Výběr **souboru &#124; nový &#124; projekt z existujícího kódu** a budou postupovat podle pokynů pro přidání existujících souborů se zdrojovým kódem. Tato možnost funguje nejlépe relativně malé a jednoduchých projektech, případně 25 zdrojové kódy soubory nebo méně s málo nebo žádná složitými závislostmi.  
  
-   spouští se souborem pravidel a vyberte šablonu projektu Makefile na kartě Obecné.  
  
-   vytvořit prázdný projekt (v části **Obecné** kartu) a ručnímu přidávání souborů zdrojového kódu tak, že kliknete pravým tlačítkem na uzel projektu v Průzkumníku řešení a zvolíte **přidat &#124; existující položku**.  
  
-   použití [Průvodce aplikací Win32](../windows/win32-application-wizard.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)  
 Popisuje typy založené na MSBuild projektů, které jsou k dispozici v jazyce Visual C++.  
  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)  
 Popisuje typy souborů, které se používají s různými typy projektu MSBuild.  
  
 [Tvorba desktopových projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 Jak vytvářet projekty v jazyce Visual C++ pomocí průvodců.  
  
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)  
 Popisuje, jak pomocí stránky vlastností a seznamech vlastností, můžete určit nastavení projektu.  
  
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)  
 Popisuje, jak přidat do projektu přidat funkce třídy, metody, proměnných a další prvky.  
  
 [Postupy: Uspořádání výstupních souborů projektu pro sestavení](../ide/how-to-organize-project-output-files-for-builds.md)  
 Popisuje způsob uspořádání výstupních souborů projektu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)  
 Obsahuje odkazy na témata popisující vytváření vaší aplikace z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Visual Studio SDK](https://msdn.microsoft.com/vstudio/extend)
