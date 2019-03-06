---
title: /Od (Zakázat (ladění))
ms.date: 11/04/2016
f1_keywords:
- /od
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
ms.openlocfilehash: 386113c7926085aa7e82e23768556372014a8cc8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426248"
---
# <a name="od-disable-debug"></a>/Od (Zakázat (ladění))

Vypne všechny optimalizace v programu a urychluje sestavování.

## <a name="syntax"></a>Syntaxe

```
/Od
```

## <a name="remarks"></a>Poznámky

Tato možnost je výchozí hodnota. Protože **/Od** pohyb kódu, potlačí zjednodušuje ladění procesu. Další informace o – možnosti kompilátoru pro ladění, naleznete v tématu [/Z7, / zi, /ZI (formát informací o ladění)](../../build/reference/z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](../../build/reference/o-options-optimize-code.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/Z7, /Zi, /ZI (formát informací o ladění)](../../build/reference/z7-zi-zi-debug-information-format.md)
