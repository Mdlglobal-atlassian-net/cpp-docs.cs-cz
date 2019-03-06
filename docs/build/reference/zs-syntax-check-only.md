---
title: /Zs (pouze kontrola syntaxe)
ms.date: 11/04/2016
f1_keywords:
- /zs
helpviewer_keywords:
- -Zs compiler option [C++]
- Syntax Check Only compiler option
- Zs compiler option
- /Zs compiler option [C++]
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
ms.openlocfilehash: c7c8993ba9589b2a5fbc59d67e8603c141511695
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413313"
---
# <a name="zs-syntax-check-only"></a>/Zs (pouze kontrola syntaxe)

Instruuje kompilátor, aby Zkontrolujte syntaxi zdrojových souborů na příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```
/Zs
```

## <a name="remarks"></a>Poznámky

Při použití této možnosti žádný výstupní soubory jsou vytvořeny a chybové zprávy jsou zapsány do standardního výstupu.

**/Zs** možnost poskytuje rychlý způsob, jak najít a opravit chyby syntaxe před kompilujete a propojujete zdrojový soubor.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
