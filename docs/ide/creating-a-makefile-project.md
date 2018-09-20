---
title: Vytvoření projektu souboru pravidel C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3360d2ed86d220bc59d6f09f582c71b48f7d78c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399480"
---
# <a name="creating-a-c-makefile-project"></a>Vytvoření projektu souboru pravidel C++

A *makefile* je textový soubor, který obsahuje pokyny, jak kompilovat a propojení (nebo *sestavení*) sadu souborů zdrojového kódu jazyka C++. A *zkontrolujte* program přečte soubor pravidel a vyvolá kompilátoru, linkeru a pravděpodobně další programy, aby spustitelný soubor. Implementace společnosti Microsoft *zkontrolujte* program se nazývá **NMAKE**. (Visual Studio ve výchozím nastavení používá systém MSBuild na základě souborů .vcsproj; to je, co se vytvořila **soubor | Nové | Projekt**.)

Pokud máte existujícího projektu souboru pravidel, pokud chcete kód a/nebo ladění v rozhraní IDE sady Visual Studio mají tyto možnosti:

- Vytvoření projektu souboru pravidel v sadě Visual Studio, který používá vaše existující soubor pravidel pro sestavení svého kódu v rozhraní IDE. (Není nutné všechny funkce integrovaného vývojového prostředí, které jste získali s nativní projektu nástroje MSBuild.) Zobrazit [vytvoření projektu souboru pravidel](#create_a_makefile_project) níže.
- Použití **vytvořit nový projekt z existujících souborů kódu** průvodce vytvořit nativní projekt MSBuild ze zdrojového kódu. Další informace najdete v tématu [postupy: vytvoření projektu jazyka C++ z existujícího kódu](how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 a novější**: použijte **otevřít složku** funkci pro otevření souboru pravidel. Další informace najdete v tématu [projekty otevřít složku v jazyce Visual C++](non-msbuild-projects.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Vytvoření projektu souboru pravidel se šablonou projektu souboru pravidel

V sadě Visual Studio 2017 nebo novější je k dispozici šablonu projektu Makefile, když je nainstalovaná úloha vývoj v jazyce C++ Desktop.

Postupujte podle pokynů průvodce a zadat příkazy a prostředí, které používá váš soubor pravidel. Potom můžete tento projekt k sestavení vašeho kódu ve vývojovém prostředí sady Visual Studio.

Ve výchozím projektu makefile nezobrazí žádné soubory v Průzkumníku řešení. Projekt makefile určuje nastavení sestavení, která se projeví na stránce vlastností projektu.

Výstupní soubor zadaný v projektu nemá žádný vliv na název, který generuje skript sestavení; deklaruje pouze záměr. Váš soubor pravidel stále řídí proces sestavení a určuje cílů pro sestavení.

1. Na úvodní stránce sady Visual Studio, zadejte "makefile" **nový projekt** vyhledávacího pole. Nebo v **nový projekt** dialogového okna rozbalte **Visual C++** > **Obecné** (Visual Studio 2015) nebo **jiných** (Visual Studio 2017) a pak vyberte **projektu Makefile** v podokně šablon a spusťte Průvodce projektu.

1. V [nastavení aplikace](../ide/application-settings-makefile-project-wizard.md) zadejte výstupu příkazu vyčistit a informace o opětovné sestavení pro ladění a prodejní sestavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nově vytvořený projekt v **Průzkumníka řešení**.

Na stránce vlastností projektu můžete zobrazit a upravit jeho vlastnosti. Zobrazit [nastavení vlastností projektu Visual C++](../ide/working-with-project-properties.md) informace o zobrazení stránky vlastností.

## <a name="see-also"></a>Viz také

[Průvodce projektem souboru pravidel](../ide/makefile-project-wizard.md)<br/>
[Speciální znaky v souboru pravidel](../build/special-characters-in-a-makefile.md)<br/>
[Obsah souboru pravidel](../build/contents-of-a-makefile.md)<br/>
