---
title: /DEF (Zadat soubor definice modulu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: c08412fb50835485e7941b2bb1db088943387b71
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807439"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Zadat soubor definice modulu)

```
/DEF:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Název souboru definice modulu (.def) má být předán linkeru.

## <a name="remarks"></a>Poznámky

/ DEF předá linkeru soubor definice modulu (.def). K propojení lze zadat pouze jeden soubor def. Podrobnosti o .def souborech najdete v tématu [soubory definice modulu](module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup** stránku vlastností.

1. Upravit **soubor definice modulu** vlastnost.

Zadat soubor .def z vývojového prostředí, musí ho přidat do projektu společně s další soubory a pak zadejte soubor, který má parametr/def.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
