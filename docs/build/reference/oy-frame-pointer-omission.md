---
title: /Oy (vynechání ukazatele na rámec)
ms.date: 11/19/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: 7884f52cc22766c6b1a864fc01abcd73f92cfabb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319964"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (vynechání ukazatele na rámec)

Zakazuje vytváření ukazatelů na rámce v zásobníku volání.

## <a name="syntax"></a>Syntaxe

> /Oy[-]

## <a name="remarks"></a>Poznámky

Tento parametr urychluje volání funkcí, protože není potřeba vytvářet a odebírat žádné ukazatele na rámce. Navíc se uvolní jeden další registr pro obecné použití.

**/Oy** povoluje vynechání ukazatele na rámce a **/Oy-** vynechání zakazuje. V x64 kompilátory, **/Oy** a **/Oy-** nejsou k dispozici.

Pokud váš kód vyžaduje adresování založených na snímcích, můžete zadat **/Oy-** za parametr **/Ox** nebo použitím [optimalizovat](../../preprocessor/optimize.md) s "**y**"a **vypnout** argumenty, které mají získat maximální optimalizaci s založených na snímcích adresování. Kompilátor rozpozná většinu situací, ve kterém se požaduje adresování pomocí založených na snímcích (například při `_alloca` a `setjmp` funkce a při zpracování strukturovaných výjimek).

[/Ox (povolení většina optimalizací pro rychlost)](ox-full-optimization.md) a [/O1, / O2 (minimalizovat velikost, maximální rychlost)](o1-o2-minimize-size-maximize-speed.md) možnosti implikují **/Oy**. Určení **/Oy-** po **/Ox**, **/O1**, nebo **/O2** zakáže **/Oy**, ať už jde o explicitní nebo implicitní.

**/Oy** díky – možnost kompilátoru pomocí ladicího programu obtížnější, protože kompilátor nezobrazuje informace o ukazateli na rámce. Pokud zadáte ladicí parametr kompilátoru ([/Z7, / zi, /ZI](z7-zi-zi-debug-information-format.md)), doporučujeme vám, že zadáte **/Oy-** za jakékoli jiné optimalizační parametry kompilátoru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **optimalizace** stránku vlastností.

1. Upravit **vypustit ukazatele na rámce** vlastnost. Tato vlastnost přidá nebo odebere pouze **/Oy** možnost. Pokud chcete přidat **/Oy-** možnosti, vyberte **příkazového řádku** vlastnost stránku a upravit **další možnosti**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
