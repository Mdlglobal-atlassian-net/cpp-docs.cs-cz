---
title: /Gy (povolení propojení na úrovni funkcí)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328283"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (povolení propojení na úrovni funkcí)

Umožňuje kompilátoru sbalit jednotlivé funkce ve formě balených funkcí (COMDAts).

## <a name="syntax"></a>Syntaxe

```
/Gy[-]
```

## <a name="remarks"></a>Poznámky

Propojovací systém vyžaduje, aby funkce byly zabaleny samostatně jako comdats vyloučit nebo objednat jednotlivé funkce v souboru DLL nebo EXE.

Pomocí možnosti propojovacího programu [/OPT (Optimalizace)](opt-optimizations.md) můžete vyloučit neodkazované sbalené funkce ze souboru EXE.

Možnost propojovacího zařízení [/ORDER (Put Functions in Order)](order-put-functions-in-order.md) můžete použít k zahrnutí zabalených funkcí v zadaném pořadí do souboru EXE.

Vložkové funkce jsou vždy zabaleny, pokud jsou vytvořena instance jako volání (ke kterému dochází, například pokud je vkládání vypnuto nebo máte adresu funkce). Kromě toho jsou členské funkce Jazyka C++ definované v deklaraci třídy automaticky zabaleny; ostatní funkce nejsou a výběr této možnosti je nutné zkompilovat jako zabalené funkce.

> [!NOTE]
> Možnost [/ZI](z7-zi-zi-debug-information-format.md) použitá pro úpravy a pokračování automaticky nastaví volbu **/Gy.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klikněte na stránku **vlastností Generování kódu.**

1. Upravte vlastnost **Povolit propojení na úrovni funkce.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
