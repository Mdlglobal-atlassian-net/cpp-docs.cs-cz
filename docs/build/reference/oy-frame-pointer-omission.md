---
title: -Oy (vynechání ukazatele) | Microsoft Docs
ms.custom: ''
ms.date: 09/22/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
dev_langs:
- C++
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6feb682d364c4c40fd01e4aff33404c4506d9c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="oy-frame-pointer-omission"></a>/Oy (vynechání ukazatele na rámec)

Zakazuje vytváření ukazatelů na rámce v zásobníku volání.

## <a name="syntax"></a>Syntaxe

> /Oy [-]

## <a name="remarks"></a>Poznámky

Tento parametr urychluje volání funkcí, protože není potřeba vytvářet a odebírat žádné ukazatele na rámce. Navíc se uvolní jeden další registr (EBP na procesorech Intel 386 nebo novějších) pro ukládání často používaných proměnných a podvýrazů.

**/Oy** umožňuje vynechání ukazatele na rámec a **/Oy-** zakáže vynechání. **/Oy** je k dispozici pouze v x86 kompilátory.

Pokud váš kód vyžaduje na základě EBP adresování, můžete zadat **/Oy-** možnost po **/Ox** možnost nebo použijte [optimalizovat](../../preprocessor/optimize.md) s "**y**" a **vypnout** argumenty k získání maximální optimalizace se na základě EBP adresování. Kompilátor zjistí většině situací, kdy je potřeba na základě EBP adresování (například s `_alloca` a `setjmp` funkce a s strukturované zpracování výjimek).

[/Ox (Povolit nejvíce rychlost optimalizace)](../../build/reference/ox-full-optimization.md) a [/O1, / O2 (velikost minimalizovat, maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) možnosti implikují **/Oy**. Určení **/Oy-** po **/Ox**, **/O1**, nebo **/O2** možnost zakáže **/Oy**, jestli je explicitní nebo implicitní.

**/Oy** díky – možnost kompilátoru pomocí ladicího programu obtížnější, protože kompilátor potlačí informace ukazatel na rámec. Pokud zadáte debug – možnost kompilátoru ([/Z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), doporučujeme vám, zda jste zadali **/Oy-** možnost po další možnosti optimalizace kompilátoru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte **C/C++** složky.

1. Klikněte **optimalizace** stránku vlastností.

1. Změnit **vynechání ukazatele na rámce** vlastnost. Tato vlastnost přidá nebo odebere pouze **/Oy** možnost. Pokud chcete přidat **/Oy-** možnost, klikněte na tlačítko **příkazového řádku** a upravovat **další možnosti**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Viz také

[/O – možnosti (optimalizace kódu)](../../build/reference/o-options-optimize-code.md)

[Možnosti kompilátoru](../../build/reference/compiler-options.md)

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)