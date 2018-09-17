---
title: -Ob (rozbalení vložené funkce) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
dev_langs:
- C++
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6755025ff07d79b7e6086fc8c8a59a3bdebdb777
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725254"
---
# <a name="ob-inline-function-expansion"></a>/Ob (rozbalení vložené funkce)

Řídí vložené rozšíření funkcí.

## <a name="syntax"></a>Syntaxe

> /Ob {0 | 1 | 2}

## <a name="arguments"></a>Arguments

**0**<br/>
Zakáže vložené rozšíření. Ve výchozím nastavení, rozbalení dojde podle uvážení kompilátoru pro všechny funkce často označuje jako *auto-inlining*.

**1**<br/>
Umožňuje rozšíření pouze funkce označené [vložené](../../cpp/inline-functions-cpp.md), `__inline`, nebo `__forceinline`, nebo v C++ členské funkce definované v deklaraci třídy.

**2**<br/>
Výchozí hodnota. Povolí rozšíření funkcí označených jako `inline`, `__inline`, nebo `__forceinline`a všechny další funkce, které kompilátor zvolí.

**/ Ob2** je v účinku po [/O1, / O2 (minimalizovat velikost, maximální rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nebo [/Ox (povolení většina optimalizací pro rychlost)](../../build/reference/ox-full-optimization.md) se používá.

Tato možnost vyžaduje, abyste povolili optimalizace pomocí **/O1**, **/O2**, **/Ox**, nebo **/og**.

## <a name="remarks"></a>Poznámky

Kompilátor zpracovává možnosti vloženého rozšíření a klíčová slova jako návrhy. Není zaručeno, že budou všechny funkce rozbalena po vložení. Vložené rozšíření můžete zakázat, ale nelze provést vynucení kompilátoru k vložení funkce, i když se používá `__forceinline` – klíčové slovo.

Můžete použít `#pragma` [auto_inline](../../preprocessor/auto-inline.md) směrnice pro vyloučení funkcí v úvahu jako kandidáty pro vložené rozšíření. Viz také `#pragma` [vnitřní](../../preprocessor/intrinsic.md) směrnice.

> [!NOTE]
> Informace shromážděné z testovacích běhů profilování potlačení optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete v tématu [Profile-Guided optimalizace](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **C/C++** a vyberte **optimalizace**.

1. Upravit **rozbalení vložených funkcí** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)