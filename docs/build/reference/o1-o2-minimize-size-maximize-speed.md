---
title: -O1, - O2 (minimální velikost, maximální rychlost) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /o2
- /o1
dev_langs:
- C++
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5003695c5ae2b16faf8aa80f68928858a3a48288
ms.sourcegitcommit: 4cdfff1114829599ab54178767f57664ad3424d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270549"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (minimální velikost, maximální rychlost)

Vybere předdefinovanou sadu možností, které mají vliv na velikost a rychlost generovaného kódu.

## <a name="syntax"></a>Syntaxe

> / O1  
> / O2

## <a name="remarks"></a>Poznámky

**/O1** a **/O2** – možnosti kompilátoru jsou rychlý způsob, jak nastavit několik možností konkrétní optimalizace současně. **/O1** možnost nastaví možnosti jednotlivých optimalizace, které vytvářejí kód nejmenší ve většině případů. **/O2** možnost nastaví možnosti, které vytvářejí kód nejrychlejší ve většině případů. **/O2** je výchozí nastavení pro verzi sestavení. Tato tabulka ukazuje konkrétní možnosti, které jsou nastavené jako **/O1** a **/O2**:

|Možnost|Ekvivalent hodnoty|
|------------|-------------------|
|**/ O1** (minimální velikost)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (maximální rychlost)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** a **/O2** se vzájemně vylučují.

> [!NOTE]  
> **x86 konkrétní**  
> Tyto možnosti implikují použití vynechání ukazatele ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, otevřete **C/C++** a potom zvolte **optimalizace** stránku vlastností.

1. Změnit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také

[/O – možnosti (optimalizace kódu)](../../build/reference/o-options-optimize-code.md)  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
[/EH (model ošetření výjimek)](../../build/reference/eh-exception-handling-model.md)
