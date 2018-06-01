---
title: / CLRIMAGETYPE (zadat typ obrázku CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5efb2e73e854591be7134753cec21a708fff3e5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705007"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Zadat typ obrázku CLR)

Nastavte typ obrázku CLR v propojený obrázek.

## <a name="syntax"></a>Syntaxe

> **/ CLRIMAGETYPE:**{**IJW**|**PRÁZDNÁ**|**BEZPEČNÉ**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Poznámky

Linkeru přijme nativních objektů a také MSIL objekty, které jsou kompilovaná pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru byly zastaralé v sadě Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017. Při předávání smíšený objektů ve stejném sestavení, je, ověřitelnosti výsledné výstupního souboru, ve výchozím nastavení rovna nejnižší úroveň ověřitelnosti vstupní modulů. Například pokud předáte nativní image a image ve smíšeném režimu (zkompilovat pomocí **/CLR**), bude výsledný obraz bitové kopie ve smíšeném režimu.

Můžete použít **/CLRIMAGETYPE** k určení s nižší úrovní ověřitelnosti, pokud je to, co potřebujete.

Informace o tom, jak určit typ obrázku CLR souboru najdete v tématu [/CLRHEADER](../../build/reference/clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Změnit **typ obrázku CLR** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
