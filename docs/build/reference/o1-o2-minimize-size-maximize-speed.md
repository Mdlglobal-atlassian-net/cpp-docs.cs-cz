---
title: /O1, /O2 (minimální velikost, maximální rychlost)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
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
ms.openlocfilehash: d33fe6bceae09267fd3f79ffe3dc26864e87c764
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320354"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (minimální velikost, maximální rychlost)

Vybere předdefinovanou sadu možností, které mají vliv velikost a rychlost generovaného kódu.

## <a name="syntax"></a>Syntaxe

> /O1 /O2

## <a name="remarks"></a>Poznámky

**/O1** a **/O2** – možnosti kompilátoru je rychlý způsob, jak nastavit několik možností, jak konkrétní optimalizace současně. **/O1** parametr nastaví možnosti jednotlivých optimalizace, které vytvářejí nejmenší kód ve většině případů. **/O2** parametr nastaví možnosti, které vytvoří ve většině případů nejrychlejší kód. **/O2** je výchozí nastavení pro buildy vydaných verzí. Tato tabulka ukazuje konkrétní možnosti, které určil institut NIST **/O1** a **/O2**:

|Možnost|Ekvivalent|
|------------|-------------------|
|**/ O1** (pro minimalizaci velikosti)|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/ O2** (maximální rychlost)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/Ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/ O1** a **/O2** se vzájemně vylučují.

> [!NOTE]
> **x86 konkrétní** tyto možnosti implikují použití vynechání ukazatele na rámec ([/Oy](oy-frame-pointer-omission.md)) možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, otevřete **C/C++** a klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/EH (model ošetření výjimek)](eh-exception-handling-model.md)
