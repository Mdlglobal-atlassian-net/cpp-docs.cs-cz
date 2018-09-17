---
title: -O1, - O2 (minimální velikost, maximální rychlost) | Dokumentace Microsoftu
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
ms.openlocfilehash: 832ea689b2db9a34b55664b695747079ac277bae
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702556"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (minimální velikost, maximální rychlost)

Vybere předdefinovanou sadu možností, které mají vliv velikost a rychlost generovaného kódu.

## <a name="syntax"></a>Syntaxe

> / O1, / O2 /

## <a name="remarks"></a>Poznámky

**/O1** a **/O2** – možnosti kompilátoru je rychlý způsob, jak nastavit několik možností, jak konkrétní optimalizace současně. **/O1** parametr nastaví možnosti jednotlivých optimalizace, které vytvářejí nejmenší kód ve většině případů. **/O2** parametr nastaví možnosti, které vytvoří ve většině případů nejrychlejší kód. **/O2** je výchozí nastavení pro buildy vydaných verzí. Tato tabulka ukazuje konkrétní možnosti, které určil institut NIST **/O1** a **/O2**:

|Možnost|Ekvivalent|
|------------|-------------------|
|**/ O1** (pro minimalizaci velikosti)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (maximální rychlost)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** a **/O2** se vzájemně vylučují.

> [!NOTE]
> **x86 konkrétní** tyto možnosti implikují použití vynechání ukazatele na rámec ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, otevřete **C/C++** a klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/EH (model ošetření výjimek)](../../build/reference/eh-exception-handling-model.md)
