---
title: /GF (odstranění duplicitních řetězců)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320492"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (odstranění duplicitních řetězců)

Umožňuje kompilátoru vytvořit jednu kopii identických řetězců v bitové kopii programu a v paměti během provádění. Jedná se o optimalizaci s názvem *sdružování řetězců,* která může vytvářet menší programy.

## <a name="syntax"></a>Syntaxe

```
/GF
```

## <a name="remarks"></a>Poznámky

Pokud použijete **/GF**, operační systém nezamění řetězcovou část paměti a může číst řetězce zpět ze souboru bitové kopie.

**/GF** fondy řetězce jako jen pro čtení. Pokud se pokusíte upravit řetězce pod **/GF**, dojde k chybě aplikace.

Sdružování řetězců umožňuje, co byly určeny jako více ukazatelů na více vyrovnávacích pamětí, které mají být více ukazatelů na jednu vyrovnávací paměť. V následujícím kódu `s` `t` a jsou inicializovány stejným řetězcem. Sdružování řetězců způsobí, že odkazují na stejnou paměť:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> Možnost [/ZI,](z7-zi-zi-debug-information-format.md) která se používá pro úpravy a pokračovat, automaticky nastaví **/GF** možnost.

> [!NOTE]
> Možnost kompilátoru **/GF** vytvoří adresovatelný oddíl pro každý jedinečný řetězec. A ve výchozím nastavení může soubor objektu obsahovat až 65 536 adresovatelných oddílů. Pokud váš program obsahuje více než 65 536 řetězců, vytvořte další oddíly pomocí možnosti kompilátoru [/bigobj.](bigobj-increase-number-of-sections-in-dot-obj-file.md)

**/GF** je v platnosti při [použití /O1](o1-o2-minimize-size-maximize-speed.md) nebo [/O2.](o1-o2-minimize-size-maximize-speed.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klikněte na stránku **vlastností Generování kódu.**

1. Upravte vlastnost **Povolit sdružování řetězců.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
