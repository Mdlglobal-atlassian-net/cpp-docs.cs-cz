---
title: Vytváření a správa projektů Visual C++ | Microsoft Docs
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
ms.openlocfilehash: b3afbd2019965d859895462cfdad57292bc2e0b3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33332420"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Vytváření a správa projekty využívající MSBuild Visual C++
MSBuild je systém nativní sestavení pro Visual C++ a je obecně že nejvhodnější vytvořit systému pro aplikace UWP a také aplikací klasické pracovní plochy, které používají knihovny MFC nebo ATL. MSBuild je úzce integrovaná s Visual Studio IDE a systému projektu, ale můžete ji použít i z příkazového řádku. Počínaje Visual Studio 2017, Visual C++ podporuje [CMake a dalšími systémy bez MSBuild prostřednictvím funkce Otevřít složku](non-msbuild-projects.md).

Projektu na základě MSBuild má projekt soubor ve formátu XML (VCXPROJ), která určuje, všechny soubory a prostředky potřebné ke kompilaci programu, jakož i další nastavení konfigurace, například cílové platformy (x 86, x64 nebo ARM) a jestli vytváříte uvolnění verzi nebo verzi ladicí program. Projekt (nebo mnoha projektů) jsou součástí *řešení*, například řešení může obsahovat několik projektů knihovny DLL Win32 a jednu Win32 konzolovou aplikaci, která používá tyto knihovny DLL. Při sestavování projektu nástroje MSBuild modul využívá souboru projektu a vytvoří spustitelný soubor nebo jakýkoli jiný vlastní výstup, který jste zadali.

Projekty Visual C++ můžete vytvořit tak, že zvolíte **soubor &#124; nový &#124; projektu**, zajistíte, že je vybraná Visual C++ v levém podokně a pak vyberete ze seznamu šablon projektu v prostředním podokně. Když kliknete na šablonu, v mnoha případech průvodce se zobrazí, můžete nastavit různé vlastnosti projektu před vytvořením projektu. Můžete zobrazit a upravit tyto vlastnosti později pomocí stránky vlastností projektu (**projektu &#124; vlastnosti**).  
  
 Můžete také vytvořit nové projekty podle:  
  
-   Výběr **soubor &#124; nový &#124; projekt z existujícího kódu** a následujících pokynů přidejte existující soubory zdrojového kódu. Tato možnost funguje nejlépe ve relativně malý a jednoduchý projekty, případně 25 zdrojové kódy soubory nebo menší s několika nebo žádné složitým závislostem.  
  
-   od verze souboru pravidel a zvolte šablonu projektem souboru pravidel na kartě Obecné.  
  
-   vytváření prázdného projektu (v části **Obecné** kartu) a ručně přidejte soubory zdrojového kódu tak, že kliknete na uzel projektu v Průzkumníku řešení pravým tlačítkem a vyberete **přidat &#124; existující položka**.  
  
-   pomocí [Win32 – Průvodce aplikací](../windows/win32-application-wizard.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)  
 Popisuje typy projektů využívající MSBuild, které jsou k dispozici v jazyce Visual C++.  
  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)  
 Popisuje typy souborů, které se používají s různými typy projektu nástroje MSBuild.  
  
 [Tvorba desktopových projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 Postup vytváření projektů s Visual C++ pomocí průvodců.  
  
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)  
 Popisuje, jak používat stránky vlastností a vlastností k určení nastavení projektu.  
  
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)  
 Popisuje postup přidání tříd, metod, proměnné a další elementy do projektu přidat další funkce.  
  
 [Postupy: Uspořádání výstupních souborů projektu pro sestavení](../ide/how-to-organize-project-output-files-for-builds.md)  
 Popisuje, jak uspořádání výstupních souborů projektu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)  
 Obsahuje odkazy na témata popisující sestavení programu z příkazového řádku nebo z integrovaného vývojového prostředí sady Visual Studio.  
  
 [Referenční dokumentace jazyka Visual C++](http://msdn.microsoft.com/en-us/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 Obsahuje odkazy na témata popisující jazyk C a C++, knihovny poskytované aplikaci Visual C++, rozšířený objektový model Visual C++ a MASM (Microsoft Macro Assembler).  
  
## <a name="see-also"></a>Viz také  
 [Visual Studio SDK](http://msdn.microsoft.com/vstudio/extend)
