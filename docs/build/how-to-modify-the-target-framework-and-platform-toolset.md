---
title: 'Postupy: Změna cílové architektury a sady nástrojů | Dokumentace Microsoftu'
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.modifytargetframeworkandplatformtoolset
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c53960b7ef972d605902a260de9e7ef344a31274
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464626"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Postupy: Změna cílové architektury a sady nástrojů
Můžete změnit nastavení projektu Visual C++ pro cílení na různé verze rozhraní .NET Framework a jiné sady nástrojů platformy. Ve výchozím nastavení používá systém projektu verzi rozhraní .NET Framework a verzi sady nástrojů, které odpovídají verzi sady Visual Studio, který použijete k vytvoření projektu. Můžete změnit cílovou sadu nástrojů platformy úpravou vlastností projektu. Cílové rozhraní Framework lze změnit úpravou souboru projektu (.vcxproj). Nemusíte udržovat samostatnou kód základní pro každý cíl kompilace.  
  
> [!IMPORTANT]
>  Některé edice nemusí podporovat změny cílových rozhraní nebo sad nástrojů platformy. Informace o kompatibilitě naleznete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).  
  
 Pokud změníte cílový rámec, také změňte sadu nástrojů platformy na verzi, která podporuje tento rámec. Například chcete-li cílit na rozhraní .NET Framework 4.5, musíte použít sadu nástrojů kompatibilní platformy, jako je Visual Studio 2015 (v140), Visual Studio 2013 (v120) nebo Visual Studio 2012 (v110). Můžete použít **Windows7.1SDK** sada nástrojů platformy cílit na rozhraní .NET Framework 2.0, 3.0, 3.5 a 4 a x86, Itanium a x64 platformy.  
  
> [!NOTE]
>  Chcete-li změnit sadu nástrojů cílové platformy, musíte mít přidružené verze sady Visual Studio nebo Windows Platform SDK nainstalovány. Například pro zaměření na platformu Itanium se **Windows7.1SDK** sada nástrojů platformy, musíte mít [Microsoft Windows SDK pro Windows 7 a rozhraní .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279) nainstalované, ale můžete použít jinou kompatibilní verzi sady Visual Studio k provedení vývojové práce, za předpokladu, že se zaměříte správnou Framework verze a platformy sadu nástrojů.  
  
 Můžete rozšířit cílovou platformu další tak, že vytvoříte vlastní sady nástrojů platformy. Další informace najdete v tématu [cílení na více verzí v nativním C++](http://go.microsoft.com/fwlink/p/?linkid=196619) na blogu Visual C++.  
  
### <a name="to-change-the-target-framework"></a>Chcete-li změnit cílový rámec  
  
1.  V sadě Visual Studio v **Průzkumníka řešení**, vyberte svůj projekt. Na panelu nabídky otevřete **projektu** nabídku a zvolte **uvolnit projekt**. To uvolní soubor projektu (.vcxproj) pro váš projekt.  
  
    > [!NOTE]
    >  Projekt C++ nelze načíst, když probíhá úprava souboru projektu v sadě Visual Studio. Ale můžete použít jiný editor, například Poznámkový blok pro úpravu souboru projektu při načtení projektu v sadě Visual Studio. Visual Studio zjistí, že došlo ke změně souboru projektu a vyzve k opětovnému načtení projektu.  
  
2.  Na panelu nabídek vyberte **souboru**, **otevřít**, **souboru**. V **otevřít soubor** dialogové okno, přejděte do složky vašeho projektu a pak otevřete soubor projektu (.vcxproj).  
  
3.  V souboru projektu vyhledejte položku pro cílovou verzi rozhraní Framework. Například pokud váš projekt je navržen pro použití rozhraní .NET Framework 4.5, vyhledejte `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` v `<PropertyGroup Label="Globals">` elementu `<Project>` elementu. Pokud `<TargetFrameworkVersion>` element není přítomen, váš projekt nepoužívá rozhraní .NET Framework a není nutná žádná změna.  
  
4.  Změňte hodnotu na požadovanou verzi Frameworku, třeba v3.5 nebo v4.6.  
  
5.  Uložte změny a zavřete editor.  
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **znovu načíst projekt**.  
  
7.  Chcete-li ověřit změny, v **Průzkumníka řešení**, klikněte pravým tlačítkem a otevřete místní nabídku pro projekt (ne pro vaše řešení) a klikněte na tlačítko **vlastnosti** otevření projektu **vlastnost Stránky** dialogové okno. V levém podokně dialogového okna rozbalte **vlastnosti konfigurace** a pak vyberte **Obecné**. Ověřte, že **cílové verze rozhraní .NET** ukazuje novou verzi Frameworku.  
  
### <a name="to-change-the-project-toolset"></a>Chcete-li změnit sadu nástrojů projektu  
  
1.  V sadě Visual Studio v **Průzkumníka řešení**, otevřete místní nabídku pro projekt (ne pro vaše řešení) a klikněte na tlačítko **vlastnosti** otevření projektu **stránky vlastností**dialogové okno.  
  
2.  V **stránky vlastností** dialogovém okně Otevřít **konfigurace** rozevíracího seznamu a pak vyberte **všechny konfigurace**.  
  
3.  V levém podokně dialogového okna rozbalte **vlastnosti konfigurace** a pak vyberte **Obecné**.  
  
4.  V pravém podokně vyberte **sada nástrojů platformy** a pak vyberte požadovanou sadu nástrojů v rozevíracím seznamu. Například, pokud jste nainstalovali sadu nástrojů Visual Studio 2010, vyberte **Visual Studio 2010 (v100)** určený pro váš projekt.  
  
5.  Zvolte **OK** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)