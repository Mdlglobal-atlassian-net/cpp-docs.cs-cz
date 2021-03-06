---
title: /Gw (Optimalizovat globální data)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 8afdb21defbbc8309b27749ab18a40f9555139e5
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450133"
---
# <a name="gw-optimize-global-data"></a>/Gw (Optimalizovat globální data)

Globální data balíčku v oddílů COMDAT optimalizace.

## <a name="syntax"></a>Syntaxe

```
/Gw[-]
```

## <a name="remarks"></a>Poznámky

**/Gw** možnost způsobí, že kompilátor globální data balíčku v jednotlivých oddílů COMDAT. Ve výchozím nastavení **/Gw** je vypnuté a musí být explicitně povolené. Chcete-li explicitně zakázat, použijte **/Gw-** . Pokud obě **/Gw** a [/GL](gl-whole-program-optimization.md) jsou povolené, propojovací program používá k porovnání oddílů COMDAT napříč více souborů objektů, aby bylo možné vyloučit neodkazovaná globální data nebo sloučit optimalizace celého programu stejná jen pro čtení globální data. To může výrazně snížit velikost výsledné binárního spustitelného souboru.

Když kompilujete a propojujete samostatně, můžete [OPT](opt-optimizations.md) – možnost linkeru vyloučit ze spustitelného souboru zkompilovaná neodkazovaná globálních dat v souborech objektů **/Gw** možnost.

Můžete také použít [/OPT:ICF](opt-optimizations.md) a [parametru/LTCG](ltcg-link-time-code-generation.md) možnosti propojovacího programu dohromady a sloučit ve spustitelném souboru zkompilovaná všechny shodné jen pro čtení globálních dat napříč více souborů objektů **/Gw** možnost.

Další informace najdete v tématu [Představujeme /Gw přepínač kompilátoru](https://devblogs.microsoft.com/cppblog/introducing-gw-compiler-switch/) na C++ Blog týmu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Gw** a klikněte na tlačítko **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
