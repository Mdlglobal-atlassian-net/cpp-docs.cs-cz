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
ms.openlocfilehash: 9643b8b4b4b26b3f7a8a59ed0085601b1a53094d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817969"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (povolení propojení na úrovni funkcí)

Umožňuje kompilátoru vytvořit balíček individuálních funkcí ve formě zabalených funkcí (sekvence Comdat).

## <a name="syntax"></a>Syntaxe

```
/Gy[-]
```

## <a name="remarks"></a>Poznámky

Propojovací program vyžaduje funkce, ke které balí samostatně jako sekvence Comdat vyloučit nebo pořadí jednotlivých funkcí v souboru DLL nebo .exe.

Můžete použít možnost linkeru [/OPT (optimalizace)](opt-optimizations.md) neodkazované zabalené funkce vyloučení ze souboru .exe.

Můžete použít možnost linkeru [/Order (Put funkcí v pořadí)](order-put-functions-in-order.md) zahrnout zabalené funkce v zadaném pořadí v souboru .exe.

Vložené funkce jsou vždy zabaleny, pokud jsou vytvořeny jako volání (které dojde, například pokud vkládání je vypnout nebo vzít adresu funkce). Kromě toho jsou zabaleny automaticky členských funkcí jazyka C++ definované v deklaraci třídy; Další funkce nejsou, a výběrem této možnosti je potřeba kompilovat jako zabalené funkce.

> [!NOTE]
>  [/Zi](z7-zi-zi-debug-information-format.md) možnost použít pro funkce upravit a pokračovat, automaticky nastaví **/Gy** možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **generování kódu** stránku vlastností.

1. Upravit **povolit propojování na úrovní funkcí** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
