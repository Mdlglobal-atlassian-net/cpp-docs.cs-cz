---
title: Nový projekt z existujícího kódu ladění nastavení (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.debugsettings
dev_langs:
- C++
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40bafe817ebf1dd25cc40115635b895502e0df8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33335039"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Specifikace konfigurace nastavení pro ladění, Průvodce vytvořením nového projektu z existujících souborů kódu
Tato stránka Průvodce vytvoření nového projektu z existujících souborů kódu slouží k nastavení konfigurace ladění projektu.  
  
## <a name="task-list"></a>Seznam úloh  
 [Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Sestavení příkazového řádku**  
 Určuje příkazový řádek, který vytvoří nový projekt. Zadejte například název kompilátor (plus všech přepínačů a argumenty) nebo skripty sestavení, které chcete použít k vytvoření nového projektu. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak hodnota není k dispozici.  
  
 **Opětovné sestavení příkazového řádku**  
 Určuje příkazový řádek, který znovu sestaví nový projekt. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak hodnota není k dispozici.  
  
 **Vyčištění příkazového řádku**  
 Určuje příkazový řádek odstranit podpůrné soubory generované nástroje sestavení pro nový projekt. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak hodnota není k dispozici.  
  
 **Výstup (pro ladění)**  
 Určuje cestu k adresáři výstupní soubory pro konfiguraci ladění nový projekt. Tato možnost je povolená při **použití externí sestavení systému** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak hodnota není k dispozici.  
  
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
