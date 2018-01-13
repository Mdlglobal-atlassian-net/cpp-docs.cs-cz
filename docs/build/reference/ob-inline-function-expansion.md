---
title: "-Ob (rozšíření vložené funkce) | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
dev_langs: C++
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
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b83d470eaf6a30698d8c2836620a0688daa35cc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ob-inline-function-expansion"></a>/Ob (rozbalení vložené funkce)

Ovládací prvky vložené rozšíření funkcí.

## <a name="syntax"></a>Syntaxe

> /Ob {0 | 1 | 2}

## <a name="arguments"></a>Arguments

**0**  
Zakáže vložené rozšíření. Ve výchozím nastavení, dojde k rozšíření uvážení kompilátoru na všechny funkce často označuje jako *automaticky vložené*.

**1**  
Umožňuje rozšíření jenom funkce, které jsou označeny [vložené](../../cpp/inline-functions-cpp.md), `__inline`, nebo `__forceinline`, nebo v členské funkce C++ definované v deklaraci třídy.

**2**  
Výchozí hodnota. Umožňuje rozšíření funkcí, které jsou označeny jako `inline`, `__inline`, nebo `__forceinline`a další funkce, která vybere kompilátoru.

**/ Ob2** je v ovlivňuje při [/O1, / O2 (velikost minimalizovat, maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nebo [/Ox (Povolit nejvíce rychlost optimalizace)](../../build/reference/ox-full-optimization.md) se používá.

Tato možnost vyžaduje, abyste povolili optimalizace pomocí **/O1**, **/O2**, **/Ox**, nebo **/Og**.  

## <a name="remarks"></a>Poznámky

Kompilátor zpracovává možnosti vloženého rozšíření a klíčová slova jako návrhy. Není zaručeno, že všechny funkce budou rozšířené vložené. Vložené rozšíření můžete zakázat, ale nemůže vynutit kompilátor vložené určitou funkci, i když se používá `__forceinline` – klíčové slovo.

Můžete použít `#pragma` [auto_inline –](../../preprocessor/auto-inline.md) – direktiva vyloučit funkce brány v úvahu jako kandidáty pro vložené rozšíření. Viz také `#pragma` [vnitřní](../../preprocessor/intrinsic.md) – direktiva.

> [!NOTE]
> Informace získané z profilace testovací spouští přepsání optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete v tématu [Profile-Guided optimalizace](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte položku **vlastnosti konfigurace**, **C/C++**a vyberte **optimalizace**.

1. Změnit **vložené funkce rozšíření** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)