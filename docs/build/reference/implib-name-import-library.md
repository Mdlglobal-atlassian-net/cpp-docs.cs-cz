---
title: /IMPLIB (knihovna importu názvů)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: dc9a9220d55f7831a00f70ec155cc5b57a695818
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821310"
---
# <a name="implib-name-import-library"></a>/IMPLIB (knihovna importu názvů)

> / IMPLIB:*název souboru*

## <a name="parameters"></a>Parametry

*Název souboru*<br/>
Uživatelem zadaný název knihovny importu. Nahradí výchozí název.

## <a name="remarks"></a>Poznámky

Tato možnost /IMPLIB přepíše výchozí název knihovny importu, který propojení vytvoří, když se vytvoří program, který obsahuje exporty. Výchozí název je vytvořen ze základní název hlavního výstupního souboru a příponou. lib. Program obsahuje exporty, pokud nejsou zadány jeden nebo více z následujících akcí:

- [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) – klíčové slovo ve zdrojovém kódu

- [EXPORTY](exports.md) – příkaz souboru .def

- [/EXPORT](export-exports-a-function.md) specifikace v příkazu LINK

ODKAZ ignoruje /IMPLIB při knihovnu importu se vytváří. Pokud nejsou zadány žádné exporty, nevytvoří odkaz knihovnu importu. Pokud soubor exportu se používá v sestavení, odkaz předpokládá, že knihovnu importu již existuje a nelze vytvořit. Informace o importovanými knihovnami a exportovanými soubory, naleznete v tématu [LIB Reference](lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **knihovnu importu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
