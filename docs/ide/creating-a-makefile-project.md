---
title: Vytvoření projektu souboru pravidel | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
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
ms.openlocfilehash: dc854f96f1c41baf28a5af4ca1f253e47d9a8914
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33336775"
---
# <a name="creating-a-makefile-project"></a>Vytvoření projektu souboru pravidel

Pokud máte stávající projekt zdrojového kódu, který jste vytvořili z příkazového řádku pomocí souboru pravidel, vývojovém prostředí sady Visual Studio obsahuje několik způsobů zapnutí do projektu, který mohou využít výhod funkcí Visual Studio IDE. Tento článek popisuje postup vytvoření projektu souboru pravidel v sadě Visual Studio, který používá vaše stávající soubor pravidel k vytvoření kódu v prostředí IDE. Alternativně můžete použít **vytvoření nového projektu z existujících souborů kódu** Průvodce pro vytvoření k nativnímu projektu nástroje MSBuild z vašeho zdrojového kódu. Další informace najdete v tématu [postupy: vytvoření projektu jazyka C++ z existujícího kódu](how-to-create-a-cpp-project-from-existing-code.md). Od verze Visual Studio 2017, můžete použít také **otevřít složku** funkci, která můžete použít několik existujících sestavení systémů, jako kdyby byly nativní projektů sady Visual Studio. Další informace najdete v tématu [otevřít složku projektů v jazyce Visual C++](non-msbuild-projects.md).

Pomocí sady Visual Studio k otevření a sestavení vašeho zdrojového kódu pomocí vaší existující soubor pravidel, nejprve vytvořit nový projekt výběrem šablony projektu souboru pravidel. Průvodce vám pomůže zadat příkazy a prostředí, které používá vaše souboru pravidel. Pak můžete tento projekt k vytváření kódu ve vývojovém prostředí sady Visual Studio.

Ve výchozím nastavení zobrazí projektem souboru pravidel žádné soubory v Průzkumníku řešení. Projektem souboru pravidel určuje nastavení sestavení, která se projeví na stránce vlastností projektu.

Výstupní soubor zadaný v projektu nemá žádný vliv na název, který generuje skript sestavení; deklaruje pouze záměr. Vaše makefile stále řídí procesu sestavení a určuje cíle sestavení.

## <a name="to-create-a-makefile-project"></a>Vytvoření projektu Makefile

1. Postupujte podle pokynů v tématu nápovědy [vytvoření projektu pomocí Průvodce aplikací Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).

1. V **nový projekt** dialogové okno, rozbalte seznam **Visual C++** > **Obecné** a pak vyberte **projektem souboru pravidel** v Šablony podokně otevřete Průvodce projektem.

1. V [nastavení aplikace](../ide/application-settings-makefile-project-wizard.md) zadejte vyčistit výstupu příkazu a informace o opětovném sestavení pro ladění a prodejní sestavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nově vytvořený projekt v **Průzkumníku řešení**.

Na stránce vlastností projektu můžete zobrazit a upravit jeho vlastnosti. V tématu [nastavení vlastností projektu Visual C++](../ide/working-with-project-properties.md) informace o zobrazení stránky vlastností.

## <a name="see-also"></a>Viz také

[Průvodce projektem souboru pravidel](../ide/makefile-project-wizard.md)<br/>
[Speciální znaky v souboru pravidel](../build/special-characters-in-a-makefile.md)<br/>
[Obsah souboru pravidel](../build/contents-of-a-makefile.md)<br/>
