---
title: 'Postupy: Povolení technologie IntelliSense pro projekty souborů pravidel'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
ms.openlocfilehash: 80a4696856fea46c7749cfeb120535dcdab86282
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434668"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Postupy: Povolení technologie IntelliSense pro projekty souborů pravidel

Technologie IntelliSense nebude moci pracovat v integrovaném vývojovém prostředí pro projekty Visual C++ makefile při některých nastavení projektu a možnosti kompilátoru, jsou správně nastavená. Pomocí tohoto postupu konfigurace projektů Visual C++ makefile, tak, aby IntelliSense funguje, když jsou otevřené ve vývojovém prostředí sady Visual Studio projekty souborů pravidel.

### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Chcete povolit technologii IntelliSense pro projekty souborů pravidel v integrovaném vývojovém prostředí

1. Otevřít **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Vyberte **NMake** vlastnost stránce a potom změňte vlastnosti v rámci **IntelliSense** podle potřeby.

   - Nastavte **Definice preprocesoru** vlastnost pro definování preprocesoru symbolů ve vašem projektu souboru pravidel. Zobrazit [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md), další informace.

   - Nastavte **zahrnout cestu vyhledávání** vlastnosti a určit tak seznam adresářů, které kompilátor prohledá, chcete-li vyřešit odkazy na soubory, které jsou předány do direktivy preprocesoru ve vašem projektu souboru pravidel. Zobrazit [/I (další vložené adresáře)](../build/reference/i-additional-include-directories.md), další informace.

         For projects that are built using CL.EXE from a Command Window, set the **INCLUDE** environment variable to specify directories that the compiler will search to resolve file references that are passed to preprocessor directives in your makefile project.

   - Nastavte **vynucené zahrnuje** vlastnosti a určit, které hlavičkové soubory proces, při vytváření projektu souboru pravidel. Zobrazit [/FI (vynucené soubor zahrnutí názvu)](../build/reference/fi-name-forced-include-file.md), další informace.

   - Nastavte **cesta pro vyhledávání sestavení** vlastnosti a určit tak seznam adresářů, které kompilátor bude hledat odkazy na sestavení rozhraní .NET ve vašem projektu. Zobrazit [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md), další informace.

   - Nastavte **vynucené používání sestavení** vlastnosti a určit tak sestavení .NET pro zpracování při vytváření projektu souboru pravidel. Zobrazit [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md), další informace.

   - Nastavte **další možnosti** vlastnosti a určit další přepínače kompilátoru pro použití technologií IntelliSense při analýze souborů C++.

1. Klikněte na tlačítko **OK** stránku vlastností zavřete.

1. Použití **Uložit vše** příkazu k uložení nastavení projektu.

Při příštím otevření projektu makefile ve vývojovém prostředí sady Visual Studio, spusťte **Vyčistit řešení** příkaz a potom **sestavit řešení** v projektu makefile příkaz. Technologie IntelliSense by měly fungovat správně v integrovaném vývojovém prostředí.

## <a name="see-also"></a>Viz také

[Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE – referenční zdroje](../build/nmake-reference.md)<br>
[Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)