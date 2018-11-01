---
title: /Gw (Optimalizovat globální data)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 406b1577b77f056e18753db10bae5675febe879e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506688"
---
# <a name="gw-optimize-global-data"></a>/Gw (Optimalizovat globální data)

Globální data balíčku v oddílů COMDAT optimalizace.

## <a name="syntax"></a>Syntaxe

```
/Gw[-]
```

## <a name="remarks"></a>Poznámky

**/Gw** možnost způsobí, že kompilátor globální data balíčku v jednotlivých oddílů COMDAT. Ve výchozím nastavení **/Gw** je vypnuté a musí být explicitně povolené. Chcete-li explicitně zakázat, použijte **/Gw-**. Pokud obě **/Gw** a [/GL](../../build/reference/gl-whole-program-optimization.md) jsou povolené, propojovací program používá k porovnání oddílů COMDAT napříč více souborů objektů, aby bylo možné vyloučit neodkazovaná globální data nebo sloučit optimalizace celého programu stejná jen pro čtení globální data. To může výrazně snížit velikost výsledné binárního spustitelného souboru.

Když kompilujete a propojujete samostatně, můžete [OPT](../../build/reference/opt-optimizations.md) – možnost linkeru vyloučit ze spustitelného souboru zkompilovaná neodkazovaná globálních dat v souborech objektů **/Gw** možnost.

Můžete také použít [/OPT:ICF](../../build/reference/opt-optimizations.md) a [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) možnosti propojovacího programu dohromady a sloučit ve spustitelném souboru zkompilovaná všechny shodné jen pro čtení globálních dat napříč více souborů objektů **/Gw** možnost.

Další informace najdete v tématu [Představujeme /Gw přepínač kompilátoru](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) na blogu týmu Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Gw** a klikněte na tlačítko **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)