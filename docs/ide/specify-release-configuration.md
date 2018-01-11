---
title: "Nový projekt z existujícího kódu verzi konfigurace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.releasesettings
dev_langs: C++
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff208af8bb89dbcb7df00b37ce542a5adae5fa23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Specifikace konfigurace nastavení pro vydání , Průvodce vytvoření nového projektu z existujících souborů kódu
Na této stránce Průvodce vytvoření nového projektu z existujících souborů kódu můžete nastavení konfigurace verze projektu.  
  
## <a name="task-list"></a>Seznam úloh  
 [Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Stejné jako konfiguraci ladění**  
 Určuje, že průvodce bude generovat verze projektu nastavení konfigurace stejná ladit nastavení projektu konfigurace. Tato možnost je ve výchozím nastavení zaškrtnuté. Všechny možnosti na této stránce jsou neaktivní, dokud nezrušíte zaškrtnutí tohoto políčka.  
  
 **Sestavení příkazového řádku**  
 Určuje příkazový řádek, který vytvoří nový projekt. Zadejte název pro kompilátor a všechny přepínače nebo argumenty, které chcete použít k vytvoření nového projektu. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
 **Opětovné sestavení příkazového řádku**  
 Určuje příkazový řádek, který znovu sestaví nový projekt. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
 **Vyčištění příkazového řádku**  
 Určuje příkazový řádek odstranit podpůrné soubory generované nástroje sestavení pro nový projekt. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
 **Výstup (pro ladění)**  
 Určuje cestu k adresáři výstupní soubory pro konfiguraci ladění nový projekt. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky.  
  
 **Definice preprocesoru (/ D)**  
 Definuje preprocesoru symboly pro nový projekt. Další informace najdete v tématu [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md).  
  
 **Zahrnout cesty pro hledání (/ I)**  
 Určuje adresář pro přidání do seznamu adresáře, které bude kompilátor hledat řešení odkazů na soubor předaný direktivy preprocesoru v novém projektu. Další informace najdete v tématu [/I (Další adresáře Include)](../build/reference/i-additional-include-directories.md).  
  
 **Vynucené zahrnuté soubory (/FI)**  
 Určuje hlavičku soubory ke zpracování při vytváření nového projektu. Další informace najdete v tématu [/FI (vynutit soubor začlenění název)](../build/reference/fi-name-forced-include-file.md).  
  
 **Vyhledávací cesta sestavení .NET (/ AI)**  
 Určuje adresář cesty, které bude vyhledávat kompilátor odkazy na sestavení rozhraní .NET předaný direktivy preprocesoru v novém projektu. Další informace najdete v tématu [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md).  
  
 **Vynucené použití sestavení .NET (/ FU)**  
 Určuje sestavení .NET zpracovat při vytváření nového projektu. Další informace najdete v tématu [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## <a name="see-also"></a>Viz také  
 [Specifikace nastavení projektu, Průvodce vytvořením nového projektu z existujících souborů kódu](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)