---
title: 'Postupy: vytvoření projektu jazyka C++ z existujícího kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b190dbc2670ab94f7952adc188dd43d91fb520
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397283"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Postupy: Vytvoření projektu jazyka C++ z existujícího kódu

V sadě Visual Studio, můžete portů existujících souborů kódu do projektu jazyka Visual C++ s použitím **vytvoření nového projektu z existujících souborů kódu** průvodce. Tento průvodce není k dispozici ve starších edicích Express sady Visual Studio. Tento průvodce vytvoří nová řešení a projekt, který používá systém MSBuild ke správě zdrojových souborů a konfiguraci sestavení.

Přenesení stávajících souborů s kódem do projektu jazyka Visual C++ umožňuje používat všechny funkce pro správu nativní projekt MSBuild integrovanou do rozhraní IDE. Pokud byste radši chtěli použít existující systém sestavení, jako jsou soubory pravidel nmake, CMake nebo alternativy, můžete místo toho použít možnost otevřít složku. Další informace najdete v tématu [projekty otevřít složku v jazyce Visual C++](../ide/non-msbuild-projects.md). Obě možnosti umožňují používat funkce rozhraní IDE, jako [IntelliSense](/visualstudio/ide/using-intellisense) a [vlastnosti projektu](../ide/working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Vytvoření projektu jazyka C++ z existujícího kódu

1. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projekt z existujícího kódu**.

1. První stránka **vytvořit nový projekt z existujících souborů kódu** průvodce, vyberte **Visual C++** v **jaký typ projektu chcete vytvořit** seznamu. Zvolte **Další** pokračujte.

1. Zadejte umístění vašeho projektu a adresář pro zdrojové soubory. Podrobnosti na této stránce najdete v tématu [zadejte umístění projektu a zdrojových souborů, Průvodce vytvořením nové projektu z existujícího kódu soubory](../ide/specify-project-location-and-source-files.md). Zvolte **Další** pokračujte.

1. Specifikace nastavení projektu použít. Podrobnosti na této stránce najdete v tématu [zadejte nastavení projektu, Průvodce vytvořením nové projektu z existujícího kódu soubory](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Zvolte **Další** pokračujte.

1. Zadejte nastavení konfigurace ladění k použití. Podrobnosti na této stránce najdete v tématu [zadat konfigurační nastavení ladění, Průvodce vytvořením nové projektu z existujícího kódu soubory](../ide/specify-debug-configuration-settings.md). Zvolte **Další** pokračujte.

1. Zadejte konfigurační nastavení vydání chcete použít. Podrobnosti na této stránce najdete v tématu [zadejte konfigurační nastavení vydání, Průvodce vytvořením nové projektu z existujícího kódu soubory](../ide/specify-release-configuration.md). Zvolte **Dokončit** k vygenerování nového projektu.

## <a name="see-also"></a>Viz také

[Zadání umístění projektu a zdrojových souborů, Průvodce vytvořením nového projektu z existujících souborů kódu](../ide/specify-project-location-and-source-files.md)<br>
[Specifikace nastavení projektu, Průvodce vytvořením nového projektu z existujících souborů kódu](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)<br>
[Specifikace konfigurace nastavení pro ladění, Průvodce vytvořením nového projektu z existujících souborů kódu](../ide/specify-debug-configuration-settings.md)<br>
[Specifikace konfigurace nastavení pro vydání, Průvodce vytvoření nového projektu z existujících souborů kódu](../ide/specify-release-configuration.md)