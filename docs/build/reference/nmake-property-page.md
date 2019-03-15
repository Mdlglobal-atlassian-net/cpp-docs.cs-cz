---
title: NMake – stránka vlastností (Windows C++) | Dokumentace Microsoftu
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: c0dbe537635fe6698f814f3d8456f0caa9c8c796
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823071"
---
# <a name="nmake-property-page"></a>NMake – stránka vlastností

**NMake** stránku vlastností umožňuje určit nastavení sestavení pro projekty NMake. (NMAKE je implementace společnosti Microsoft [zkontrolujte](https://wikipedia.org/wiki/Make_(software)).)

Další informace o projektech NMake najdete v tématu [vytváření projektu souboru pravidel](creating-a-makefile-project.md). Projekty Windows MakeFile, naleznete v tématu [vlastnosti projektu souboru pravidel (Linux C++)](../../linux/prop-pages/makefile-linux.md), [obecné vlastnosti projektů (Android C++ Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page) nebo [vlastnosti NMake (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page).

**NMake** stránka vlastností obsahuje následující vlastnosti.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Sestavení příkazového řádku**

   Určuje příkaz, který se spustí, když **sestavení** je kliknuli **sestavení** nabídky.

- **Opětovné sestavení všech příkazového řádku**

   Určuje příkaz, který se spustí, když **sestavit vše znovu** je kliknuli **sestavení** nabídky.

- **Příkazový řádek příkazu vyčistit**

   Určuje příkaz, který se spustí, když **Vyčistit** je kliknuli **sestavení** nabídky.

- **Output**

   Určuje název souboru, který bude obsahovat výstup do příkazového řádku. Ve výchozím nastavení tento název souboru je podle názvu projektu.

- **Definice preprocesoru**

   Určuje všechny definice preprocesoru používají zdrojové soubory. Výchozí hodnota je vzhledem k aktuální platformy a konfigurace.

- **Zahrnout cestu vyhledávání**

   Určuje adresáře, kde kompilátor hledá vkládané soubory.

- **Vynucené zahrnuje**

   Určuje soubory, které preprocesor zpracuje automaticky i v případě, že nejsou zahrnuté v souborech projektu.

- **Cesta pro vyhledávání sestavení**

   Určuje adresáře, kde rozhraní .NET Framework vyhledává to zkusí vyřešit sestavení .NET.

- **Vynuceně použitá sestavení**

   Určuje sestavení, která automaticky zpracovává rozhraní .NET Framework.

- **Další možnosti**

   Určuje další přepínačů technologie IntelliSense při analýze souborů C++.

Informace o tom, jak získat přístup **NMake** stránky vlastností naleznete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

Informace o tom, jak prostřednictvím kódu programu získat přístup ke členům tohoto objektu najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.

## <a name="see-also"></a>Viz také:

[Odkaz na stránku vlastností projektu jazyka C++](property-pages-visual-cpp.md)<br>
