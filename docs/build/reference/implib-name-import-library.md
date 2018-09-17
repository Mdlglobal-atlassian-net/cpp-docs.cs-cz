---
title: -IMPLIB (pojmenování knihovny importu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25d997bf7df96d3f6ee518a8b7ca0568a44efa93
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707639"
---
# <a name="implib-name-import-library"></a>/IMPLIB (knihovna importu názvů)

> / IMPLIB:*název souboru*

## <a name="parameters"></a>Parametry

*Název souboru*<br/>
Uživatelem zadaný název knihovny importu. Nahradí výchozí název.

## <a name="remarks"></a>Poznámky

Tato možnost /IMPLIB přepíše výchozí název knihovny importu, který propojení vytvoří, když se vytvoří program, který obsahuje exporty. Výchozí název je vytvořen ze základní název hlavního výstupního souboru a příponou. lib. Program obsahuje exporty, pokud nejsou zadány jeden nebo více z následujících akcí:

- [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) – klíčové slovo ve zdrojovém kódu

- [EXPORTY](../../build/reference/exports.md) – příkaz souboru .def

- [/EXPORT](../../build/reference/export-exports-a-function.md) specifikace v příkazu LINK

ODKAZ ignoruje /IMPLIB při knihovnu importu se vytváří. Pokud nejsou zadány žádné exporty, nevytvoří odkaz knihovnu importu. Pokud soubor exportu se používá v sestavení, odkaz předpokládá, že knihovnu importu již existuje a nelze vytvořit. Informace o importovanými knihovnami a exportovanými soubory, naleznete v tématu [LIB Reference](../../build/reference/lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **knihovnu importu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)