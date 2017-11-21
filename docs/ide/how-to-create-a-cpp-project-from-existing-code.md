---
title: "Postupy: vytvoření projektu jazyka C++ z existujícího kódu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae75f8b831af1a2eb58529c09273a6e61cc58223
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Postupy: Vytvoření projektu jazyka C++ z existujícího kódu

V sadě Visual Studio, můžete existující soubory s kódem portu do projektu Visual C++ pomocí **vytvoření nového projektu z existujících souborů kódu** průvodce. Tohoto průvodce není k dispozici v starší edice Express sady Visual Studio. Tento průvodce vytvoří nové řešení a projekt, který používá systém MSBuild ke správě zdrojové soubory a konfigurace sestavení.  
  
Přenesení existujících souborů kódu do projektu Visual C++ umožňuje používat všechny funkce pro správu nativní projektu nástroje MSBuild integrovaný do prostředí IDE. Pokud byste radši chtěli použít existující systém sestavení, jako jsou soubory nmake pravidel, CMake nebo alternativy, můžete místo toho použít možnost otevřít složku. Další informace najdete v tématu [otevřít složku projektů v jazyce Visual C++](../ide/non-msbuild-projects.md). Obě možnosti umožňují používat funkce rozhraní IDE, jako [IntelliSense](/visualstudio/ide/using-intellisense) a [vlastnosti projektu](../ide/working-with-project-properties.md).  
  
### <a name="to-create-a-c-project-from-existing-code"></a>Vytvoření projektu jazyka C++ z existujícího kódu  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projekt z existujícího kódu**.  
  
1.  Na první stránce **vytvoření nového projektu z existujících souborů kódu** průvodci vyberte **Visual C++** v **jaký typ projektu byste chtěli vytvořit** seznamu. Zvolte **Další** pokračujte. 
  
1.  Zadejte umístění vašeho projektu a adresář pro zdrojové soubory. Podrobnosti na této stránce najdete v tématu [zadejte umístění projektu a zdrojových souborů, Průvodce vytvořením nové projekt z existujícího kódu soubory](../ide/specify-project-location-and-source-files.md). Zvolte **Další** pokračujte.  
  
1.  Specifikace nastavení projektu používat. Podrobnosti na této stránce najdete v tématu [zadejte nastavení projektu, Průvodce vytvořením nové projekt z existujícího kódu soubory](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Zvolte **Další** pokračujte.  

1.  Zadejte nastavení konfigurace ladění k použití. Podrobnosti na této stránce najdete v tématu [zadejte konfiguraci nastavení pro ladění, Průvodce vytvořením nové projekt z existujícího kódu soubory](../ide/specify-debug-configuration-settings.md). Zvolte **Další** pokračujte.  

1.  Zadejte nastavení konfigurace verze k použití. Podrobnosti na této stránce najdete v tématu [zadejte konfigurace nastavení pro vydání, Průvodce vytvořením nové projekt z existujícího kódu soubory](../ide/specify-release-configuration.md). Zvolte **Dokončit** ke generování nový projekt.  
  
## <a name="see-also"></a>Viz také  

[Zadejte projektu umístění a zdrojové soubory, vytvořením nového projektu z existujících souborů kódu pomocí Průvodce](../ide/specify-project-location-and-source-files.md)   
[Specifikace nastavení projektu, vytvoření nového projektu z existujících souborů kódu pomocí Průvodce](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[Zadejte nastavení pro konfiguraci ladění, vytvoření nového projektu z existujících souborů kódu pomocí Průvodce](../ide/specify-debug-configuration-settings.md)   
[Specifikace konfigurace nastavení pro vydání, vytvoření nového projektu z existujících souborů kódu pomocí Průvodce](../ide/specify-release-configuration.md)