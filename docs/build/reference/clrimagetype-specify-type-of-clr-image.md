---
title: /CLRIMAGETYPE (Zadat typ obrázku CLR)
ms.date: 05/16/2019
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: ee2e2ce359a4b877551adf9af71e0187b42cfd42
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837484"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Zadat typ obrázku CLR)

Nastavte typ bitové kopie CLR v propojený obrázek.

## <a name="syntax"></a>Syntaxe

> **/ CLRIMAGETYPE:**{**IJW**|**PRÁZDNÁ**|**BEZPEČNÉ**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Poznámky

Linker přijímá nativní objekty a také objekty jazyka MSIL, které jsou kompilovány pomocí [/CLR](clr-common-language-runtime-compilation.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru byla vyřazena jako zastaralá v sadě Visual Studio 2015 a nepodporované v sadě Visual Studio 2017 nebo novější. Při předávání smíšených objektů ve stejném sestavení je ověřitelnost výsledného výstupního souboru je ve výchozím nastavení rovna nejnižší úrovni ověřitelnosti výstupních modulů. Například pokud předáte nativní obraz a obraz smíšeného režimu (kompilované pomocí **/CLR**), bude výsledný obraz smíšeného režimu.

Můžete použít **/CLRIMAGETYPE** k určení nižší úroveň ověřitelnosti, pokud je to, co potřebujete.

Informace o tom, jak určit typ bitové kopie CLR souboru najdete v tématu [/CLRHEADER](clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Upravit **typ bitové kopie CLR** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Viz také:

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
