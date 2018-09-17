---
title: -LIBPATH (další proměnná Libpath) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 784281df23b0a8d43625766297b6cbbd20179c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717194"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (další proměnná Libpath)

```
/LIBPATH:dir
```

## <a name="parameters"></a>Parametry

*adresář*<br/>
Určuje cestu, že propojovací program bude hledat před prohledává cestě zadané v možnosti prostředí LIB.

## <a name="remarks"></a>Poznámky

Pomocí možnosti/Libpath přepsat cestu ke knihovně prostředí. Linker se nejprve vyhledat v cestě určené tuto možnost a pak vyhledejte v cestě zadané v proměnné prostředí LIB. Můžete určit pouze jeden adresář pro každý/Libpath – možnost, které zadáte. Pokud chcete zadat více než jeden adresář, musíte zadat více možností/Libpath. Propojovací program poté vyhledá zadaných adresářích v pořadí.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **další adresáře knihoven** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)