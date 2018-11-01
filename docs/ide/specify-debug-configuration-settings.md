---
title: Nový projekt z existujícího kódu, ladění, nastavení (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.debugsettings
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
ms.openlocfilehash: 9c43e86bedd08667c67427e69e12b21c59492fba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565058"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Specifikace konfigurace nastavení pro ladění, Průvodce vytvořením nového projektu z existujících souborů kódu

Na této stránce Průvodce vytvoření nového projektu z existujících souborů kódu k nastavení konfigurace ladění projektu.

## <a name="task-list"></a>Seznam úloh

[Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Sestavení příkazového řádku**

   Určuje příkazový řádek, který vytvoří nový projekt. Zadejte například název kompilátor (plus všechny přepínače a argumenty) nebo skripty sestavení, kterou chcete použít k vytvoření nového projektu. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak je k dispozici.

- **Opětovné sestavení příkazového řádku**

   Určuje příkazový řádek, který znovu sestaví nový projekt. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak je k dispozici.

- **Příkazový řádek vyčištění**

   Určuje příkazový řádek odstranit soubory podpory, které jsou generovány pomocí nástrojů pro vytváření nového projektu. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak je k dispozici.

- **Výstup (ladění)**

   Určuje cestu k adresáři výstupních souborů pro konfiguraci ladění nového projektu. Tato možnost bude nabídnuta při **použijte externí sestavovací systém** je vybraná možnost v **zadejte nastavení projektu** stránky; jinak je k dispozici.

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
