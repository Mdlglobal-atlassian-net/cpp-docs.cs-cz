---
title: -Oy (vynechání ukazatele na rámec) | Dokumentace Microsoftu
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
ms.openlocfilehash: 6c077b5a350d7381adc5412ca4a318713d720ad6
ms.sourcegitcommit: 1870c342d44b10990fd015e60856225c3026e8c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49963048"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (vynechání ukazatele na rámec)

Zakazuje vytváření ukazatelů na rámce v zásobníku volání.

## <a name="syntax"></a>Syntaxe

> /Oy [-]

## <a name="remarks"></a>Poznámky

Tento parametr urychluje volání funkcí, protože není potřeba vytvářet a odebírat žádné ukazatele na rámce. Navíc se uvolní jeden další registr pro obecné použití.

**/Oy** povoluje vynechání ukazatele na rámce a **/Oy-** vynechání zakazuje. **/Oy** je k dispozici pouze v x86 kompilátory.

Pokud váš kód vyžaduje adresování na základě EBP, můžete zadat **/Oy-** za parametr **/Ox** nebo použitím [optimalizovat](../../preprocessor/optimize.md) s "**y**" a **vypnout** argumenty k získání s adresováním na základě EBP maximální optimalizaci. Kompilátor rozpozná většinu situací, ve kterém se požaduje adresování pomocí na základě EBP (například při `_alloca` a `setjmp` funkce a při zpracování strukturovaných výjimek).

[/Ox (povolení většina optimalizací pro rychlost)](../../build/reference/ox-full-optimization.md) a [/O1, / O2 (minimalizovat velikost, maximální rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) možnosti implikují **/Oy**. Určení **/Oy-** po **/Ox**, **/O1**, nebo **/O2** zakáže **/Oy**, ať už jde o explicitní nebo implicitní.

**/Oy** díky – možnost kompilátoru pomocí ladicího programu obtížnější, protože kompilátor nezobrazuje informace o ukazateli na rámce. Pokud zadáte ladicí parametr kompilátoru ([/Z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), doporučujeme vám, že zadáte **/Oy-** za jakékoli jiné optimalizační parametry kompilátoru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **vypustit ukazatele na rámce** vlastnost. Tato vlastnost přidá nebo odebere pouze **/Oy** možnost. Pokud chcete přidat **/Oy-** , kliknutím na **příkazového řádku** a upravit **další možnosti**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Viz také

[/O – možnosti (optimalizace kódu)](../../build/reference/o-options-optimize-code.md)

[Možnosti kompilátoru](../../build/reference/compiler-options.md)

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
