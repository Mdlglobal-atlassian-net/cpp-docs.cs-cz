---
title: /LIBPATH (další proměnná Libpath)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: ab586c788825a854e7d3cb3760da6e4e5558de3a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819880"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (další proměnná Libpath)

```
/LIBPATH:dir
```

## <a name="parameters"></a>Parametry

*dir*<br/>
Určuje cestu, že propojovací program bude hledat před prohledává cestě zadané v možnosti prostředí LIB.

## <a name="remarks"></a>Poznámky

Pomocí možnosti/Libpath přepsat cestu ke knihovně prostředí. Linker se nejprve vyhledat v cestě určené tuto možnost a pak vyhledejte v cestě zadané v proměnné prostředí LIB. Můžete určit pouze jeden adresář pro každý/Libpath – možnost, které zadáte. Pokud chcete zadat více než jeden adresář, musíte zadat více možností/Libpath. Propojovací program poté vyhledá zadaných adresářích v pořadí.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **další adresáře knihoven** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
