---
title: Konfigurace vydání nového projektu z existujícího kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.releasesettings
dev_langs:
- C++
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4e7d5fb707c455aa7b7fb9f0e14dff95ee5633f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703353"
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Specifikace konfigurace nastavení pro vydání , Průvodce vytvoření nového projektu z existujících souborů kódu
Na této stránce Průvodce vytvoření nového projektu z existujících souborů kódu k určení konfigurace nastavení projektu pro vydání.  
  
## <a name="task-list"></a>Seznam úloh  
 [Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
- **Stejný jako konfigurace ladění**

   Určuje, že průvodce bude generovat verze konfigurace nastavení projektu identické a ladit nastavení projektu. Tato možnost je ve výchozím nastavení zaškrtnuto. Další možnosti na této stránce jsou neaktivní, dokud nezrušíte zaškrtnutí tohoto políčka.  
  
- **Sestavení příkazového řádku**

   Určuje příkazový řádek, který vytvoří nový projekt. Zadejte název pro kompilátor plus všechny přepínače nebo argumenty, které chcete použít k vytvoření nového projektu. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
- **Opětovné sestavení příkazového řádku**

   Určuje příkazový řádek, který znovu sestaví nový projekt. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
- **Příkazový řádek vyčištění**

   Určuje příkazový řádek odstranit soubory podpory, které jsou generovány pomocí nástrojů pro vytváření nového projektu. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
- **Výstup (ladění)**

   Určuje cestu k adresáři výstupních souborů pro konfiguraci ladění nového projektu. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
- **Definice preprocesoru (/ D)**

   Definuje symboly preprocesoru nového projektu. Další informace najdete v tématu [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md).  
  
- **Zahrnout cestu vyhledávání (/ I)**

   Určuje cesty k adresářům přidat do seznamu adresáře, které kompilátor prohledá, chcete-li vyřešit odkazy na soubory předané do direktivy preprocesoru v novém projektu. Další informace najdete v tématu [/I (další vložené adresáře)](../build/reference/i-additional-include-directories.md).  
  
- **Nuceně zahrnuté soubory (/FI)**

   Určuje hlavičkové soubory ke zpracování při vytváření nového projektu. Další informace najdete v tématu [/FI (vynucené soubor zahrnutí názvu)](../build/reference/fi-name-forced-include-file.md).  
  
- **Cesta pro vyhledávání sestavení .NET (/ AI)**

   Určuje adresář cesty, které kompilátor prohledá, chcete-li vyřešit odkazy na sestavení .NET předané do direktivy preprocesoru v novém projektu. Další informace najdete v tématu [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md).  
  
- **Vynuceně použitá sestavení .NET (/ FU)**

   Určuje sestavení .NET pro zpracování při vytváření nového projektu. Další informace najdete v tématu [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## <a name="see-also"></a>Viz také  
 [Specifikace nastavení projektu, Průvodce vytvořením nového projektu z existujících souborů kódu](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)