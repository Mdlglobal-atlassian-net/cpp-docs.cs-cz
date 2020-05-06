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
ms.openlocfilehash: 3daf5dd5f9912194fd5d8aaeb4c7a312be142b69
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825339"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (minimální velikost, maximální rychlost)

Slouží k výběru předdefinované sady možností, které mají vliv na velikost a rychlost vygenerovaného kódu.

## <a name="syntax"></a>Syntaxe

> O1
> /O2

## <a name="remarks"></a>Poznámky

Možnosti kompilátoru **/O1** a **/O2** představují rychlý způsob, jak najednou nastavit několik specifických možností optimalizace. Možnost **/O1** nastaví jednotlivé možnosti optimalizace, které vytvářejí nejmenší kód ve většině případů. Možnost **/O2** nastaví možnosti, které vytvářejí nejrychlejší kód ve většině případů. Možnost **/O2** je výchozí pro sestavení vydaných verzí. Tato tabulka zobrazuje konkrétní možnosti, které jsou nastaveny pomocí **/O1** a **/O2**:

|Možnost|Ekvivalent|
|------------|-------------------|
|**/O1** (minimalizace velikosti)|[/Og](og-global-optimizations.md) [/OS](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/O2** (maximalizovat rychlost)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/O1** a **/O2** se vzájemně vylučují.

> [!NOTE]
> **Specifické pro procesory x86**\
> Tyto možnosti implikují použití možnosti vynechání ukazatele na rámec ([/Oy](oy-frame-pointer-omission.md)).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. V části **Vlastnosti konfigurace**otevřete **C/C++** a pak zvolte stránku vlastností **optimalizace** .

1. Upravte vlastnost **optimalizace** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/EH (model zpracování výjimek)](eh-exception-handling-model.md)
