---
title: 'Postupy: povolení technologie IntelliSense pro projekty Makefile | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b9b11f04f1fe8d201d6d07ca5ed83f9ca7d991b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705459"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Postupy: Povolení technologie IntelliSense pro projekty souborů pravidel
IntelliSense přestane fungovat v integrovaném vývojovém prostředí pro projekty makefile Visual C++ při určitých nastavení projektu a možnosti kompilátoru jsou nastaveny nesprávně. Pomocí tohoto postupu ke konfiguraci projekty makefile Visual C++, tak, aby IntelliSense funguje, když jsou projekty makefile otevřené ve vývojovém prostředí sady Visual Studio.  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>K povolení technologie IntelliSense pro projekty makefile v prostředí IDE  
  
1.  Otevřete **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Vyberte **NMake** vlastností stránky a potom změňte vlastnosti v rámci **IntelliSense** podle potřeby.  
  
    -   Nastavte **Definice preprocesoru** vlastnost pro definování symbolů preprocesoru v projektu souboru pravidel. V tématu [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md), další informace.  
  
    -   Nastavte **zahrnují cesty pro hledání** vlastnosti a určit tak seznam adresářů, které kompilátor hledat, které jsou předávány direktivy preprocesoru ve vašem projektu souboru pravidel. V tématu [/I (Další adresáře Include)](../build/reference/i-additional-include-directories.md), další informace.  
  
         Pro projekty, které jsou vytvořené pomocí CL. Nastavit spuštění z příkazového okna, **zahrnout** proměnné prostředí adresáře, které kompilátor hledat, které jsou předávány direktivy preprocesoru ve vašem projektu souboru pravidel.  
  
    -   Nastavte **obsahuje vynucené** vlastnosti a určit, které hlavičkové soubory zpracovat při sestavování projektu souboru pravidel. V tématu [/FI (vynutit soubor začlenění název)](../build/reference/fi-name-forced-include-file.md), další informace.  
  
    -   Nastavte **cesty pro hledání sestavení** vlastnosti a určit tak seznam adresářů, které kompilátor hledat odkazy na sestavení rozhraní .NET v projektu. V tématu [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md), další informace.  
  
    -   Nastavte **vynucené použití sestavení** vlastnost sestavení .NET určených ke zpracování při sestavování projektu souboru pravidel. V tématu [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md), další informace.  
  
    -   Nastavte **další možnosti** vlastnosti k určení dalších přepínačů, který se má použít technologii IntelliSense, při analýze souborů C++.  
  
4.  Klikněte na tlačítko **OK** zavřete stránky vlastností.  
  
5.  Použití **Uložit vše** příkaz pro uložení změněných nastavení projektu.  
  
 Při příštím otevření projektu makefile ve vývojovém prostředí sady Visual Studio, spusťte **Vyčistit řešení** příkaz a potom **sestavit řešení** v projektu souboru pravidel. IntelliSense by měly fungovat správně v prostředí IDE.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)   
 [NMAKE – odkaz](../build/nmake-reference.md)   
 [Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)