---
title: -Gy (povolení propojení úrovni funkcí) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09faa1a1d2b6743b7fce31af32ba4fe1572b592e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705000"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (povolení propojení na úrovni funkcí)

Umožňuje kompilátoru vytvořit balíček individuálních funkcí ve formě zabalených funkcí (sekvence Comdat).

## <a name="syntax"></a>Syntaxe

```
/Gy[-]
```

## <a name="remarks"></a>Poznámky

Propojovací program vyžaduje funkce, ke které balí samostatně jako sekvence Comdat vyloučit nebo pořadí jednotlivých funkcí v souboru DLL nebo .exe.

Můžete použít možnost linkeru [/OPT (optimalizace)](../../build/reference/opt-optimizations.md) neodkazované zabalené funkce vyloučení ze souboru .exe.

Můžete použít možnost linkeru [/Order (Put funkcí v pořadí)](../../build/reference/order-put-functions-in-order.md) zahrnout zabalené funkce v zadaném pořadí v souboru .exe.

Vložené funkce jsou vždy zabaleny, pokud jsou vytvořeny jako volání (které dojde, například pokud vkládání je vypnout nebo vzít adresu funkce). Kromě toho jsou zabaleny automaticky členských funkcí jazyka C++ definované v deklaraci třídy; Další funkce nejsou, a výběrem této možnosti je potřeba kompilovat jako zabalené funkce.

> [!NOTE]
>  [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost použít pro funkce upravit a pokračovat, automaticky nastaví **/Gy** možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **generování kódu** stránku vlastností.

1. Upravit **povolit propojování na úrovní funkcí** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)