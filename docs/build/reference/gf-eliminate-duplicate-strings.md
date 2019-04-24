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
ms.openlocfilehash: 2f2bec446fcec522857b4c05a34311e6c26c9b75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270885"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (odstranění duplicitních řetězců)

Umožňuje kompilátoru vytvořit jednu kopii identických řetězců v bitové kopii programu a v paměti během provádění. Toto je optimalizace se označuje jako *sdružování řetězců* , který můžete vytvořit programy menší.

## <a name="syntax"></a>Syntaxe

```
/GF
```

## <a name="remarks"></a>Poznámky

Pokud používáte **/GF**, operační systém není možné Prohodit řetězec část paměti a může číst zpět řetězce ze souboru bitové kopie.

**/GF** fondů řetězců jen pro čtení. Pokud se pokusíte upravit řetězců v rámci **/GF**, dojde k chybě aplikace.

Sdružování řetězců umožňuje, co se má sloužit jako více ukazatelů na více vyrovnávacích pamětí většího počtu ukazatelů na jednu vyrovnávací paměť. V následujícím kódu `s` a `t` jsou inicializovány pomocí stejné řetězce. Sdružování řetězců způsobí, že se jim tak, aby odkazoval na stejnou paměť:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  [/Zi](z7-zi-zi-debug-information-format.md) možnost použít pro funkce upravit a pokračovat, automaticky nastaví **/GF** možnost.

> [!NOTE]
>  **/GF** – možnost kompilátoru vytvoří adresovatelný sekci pro každý jedinečný řetězec. A ve výchozím objektový soubor může obsahovat až 65 536 adresovatelných sekcí. Pokud váš program obsahuje více než 65 536 řetězce, použijte [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) – možnost kompilátoru vytvořit víc oddílů.

**/GF** je v účinku po [/O1](o1-o2-minimize-size-maximize-speed.md) nebo **/O2** se používá.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **generování kódu** stránku vlastností.

1. Upravit **povolit sdružování řetězců** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
