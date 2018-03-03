---
title: "Postupy: Změna cílové architektury a sady nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- msbuild.cpp.howto.modifytargetframeworkandplatformtoolset
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ed85e0f1e1ce94401c505281c0e693a4904f92d
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Postupy: Změna cílové architektury a sady nástrojů
Nastavení projektu Visual C++ jiné cílové verze rozhraní .NET Framework a používat modulové různé platformy, můžete změnit. Ve výchozím nastavení používá systém projektu verzi rozhraní .NET Framework a verzi sady nástrojů, které odpovídají verzi sady Visual Studio, který použijete k vytvoření projektu. Sada nástrojů platformy cíl, můžete změnit úpravou vlastností projektu. Cílový Framework můžete změnit úpravou souboru projektu (VCXPROJ). Nemáte udržovat samostatné kód základní pro každý cíl kompilace.  
  
> [!IMPORTANT]
>  Některé edice by nemusely podporovat upravené cílové rozhraní nebo modulové platformy. Informace o kompatibilitě, najdete v části [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).  
  
 Když změníte cílový Framework, také změníte sada nástrojů platformy na verzi, která podporuje dané platformy. Například pro rozhraní .NET Framework 4.5, musí používat kompatibilní sady nástrojů, jako je například Visual Studio 2015 (v140), Visual Studio 2013 (v120) nebo sady Visual Studio 2012 (v110). Můžete použít **Windows7.1SDK** sada nástrojů platformy pro rozhraní .NET Framework 2.0, 3.0, 3.5 a 4 a x86, Itanium a x64 platformy.  
  
> [!NOTE]
>  Chcete-li změnit sada nástrojů platformy cíl, musí mít přidružené verze sady Visual Studio nebo sadu SDK platformy Windows nainstalována. Například pro Cílová platforma Itanium s **Windows7.1SDK** sada nástrojů platformy, musíte mít [programu Microsoft Windows SDK pro systém Windows 7 a rozhraní .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279) nainstalovaný; však můžete použít jiné kompatibilní verze sady Visual Studio k práci vývoj, za předpokladu, že cíl správné Framework verze a platforma nástrojů.  
  
 Další cílové platformy můžete rozšířit tak, že vytvoříte vlastní sady nástrojů. Další informace najdete v tématu [cílení na více nativní C++](http://go.microsoft.com/fwlink/p/?linkid=196619) na blogu Visual C++.  
  
### <a name="to-change-the-target-framework"></a>Chcete-li změnit cílový Framework  
  
1.  V sadě Visual Studio v **Průzkumníku**, vyberte projektu. V řádku nabídek, otevřete **projektu** nabídky a zvolte **uvolnit projekt**. Zrušeno jeho zavedení souboru projektu (VCXPROJ) pro váš projekt.  
  
    > [!NOTE]
    >  Projektu jazyka C++ nelze načíst, když je upravována souboru projektu v sadě Visual Studio. Můžete však jiný editor, například Poznámkový blok k úpravě souboru projektu při načtení projektu v sadě Visual Studio. Visual Studio zjistí, že soubor projektu došlo ke změně a zobrazí výzvu k projekt znovu načíst.  
  
2.  Na panelu nabídek vyberte **soubor**, **otevřete**, **soubor**. V **otevřít soubor** dialogové okno, přejděte do složky projektu a pak otevřete soubor projektu (VCXPROJ).  
  
3.  V souboru projektu vyhledejte položku pro verzi rozhraní target Framework. Například když je váš projekt pomocí rozhraní .NET Framework 4.5, vyhledejte `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` v `<PropertyGroup Label="Globals">` element `<Project>` elementu. Pokud `<TargetFrameworkVersion>` element není přítomen, projekt nepoužívá rozhraní .NET Framework a není třeba žádná změna.  
  
4.  Změňte hodnotu na verzi, kterou chcete, jako je například v3.5 nebo 4.6.  
  
5.  Uložte změny a zavřete editor.  
  
6.  V **Průzkumníku řešení**, otevřete místní nabídky pro svůj projekt a zvolte **znovu načíst projekt**.  
  
7.  Chcete-li ověřit změny, v **Průzkumníku řešení**, klikněte pravým tlačítkem na otevření místní nabídky projektu (není pro vaše řešení) a potom zvolte **vlastnosti** otevřete projekt **vlastnost Stránky** dialogové okno. V levém podokně dialogového okna rozbalte **vlastnosti konfigurace** a pak vyberte **Obecné**. Ověřte, že **verze rozhraní .NET Framework cíl** ukazuje novou verzi.  
  
### <a name="to-change-the-project-toolset"></a>Chcete-li změnit projekt sady nástrojů  
  
1.  V sadě Visual Studio v **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt (není pro vaše řešení) a potom zvolte **vlastnosti** otevřete projekt **stránky vlastností**dialogové okno.  
  
2.  V **stránky vlastností** dialogové okno, otevřete **konfigurace** rozevíracího seznamu a potom vyberte **všechny konfigurace**.  
  
3.  V levém podokně dialogového okna rozbalte **vlastnosti konfigurace** a pak vyberte **Obecné**.  
  
4.  V pravém podokně vyberte **sada nástrojů platformy** a pak vyberte sady nástrojů, které chcete z rozevíracího seznamu. Například pokud jste nainstalovali [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)] sada nástrojů, vyberte **Visual Studio 2010 (v100)** používat pro svůj projekt.  
  
5.  Vyberte **OK** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)