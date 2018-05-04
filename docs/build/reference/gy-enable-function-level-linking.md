---
title: -Gy (povolení propojení na úrovni funkcí) | Microsoft Docs
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
ms.openlocfilehash: 36e939a12cf23a9d9e476b676a5b068889414497
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="gy-enable-function-level-linking"></a>/Gy (povolení propojení na úrovni funkcí)
Umožňuje kompilátoru na jednotlivé funkce balíček ve formě zabalené funkce (COMDATs).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gy[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Linkeru vyžaduje, aby funkce samostatně zabalené jako COMDATs vyloučit nebo pořadí jednotlivých funkcí v souboru DLL nebo .exe.  
  
 Můžete použít možnosti linkeru [/OPT (optimalizace)](../../build/reference/opt-optimizations.md) vyloučit neregistrované zabalené funkce ze souboru .exe.  
  
 Můžete použít možnosti linkeru [/ORDER (funkce uveďte v pořadí)](../../build/reference/order-put-functions-in-order.md) zahrnout zabalené funkce v uvedeném pořadí, v souboru .exe.  
  
 Pokud jsou vytvářeny jako volání vždy spojených vložené funkce (což například dochází, pokud vložené je vypnuté nebo provést adresu funkce). Kromě toho jsou automaticky zabalené členské funkce C++ definované v deklaraci třídy; Další funkce nejsou a výběr této možnosti je nutné jejich kompilace jako zabalené funkce.  
  
> [!NOTE]
>  [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) možnost použít pro upravit a pokračovat, automaticky nastaví **/Gy** možnost.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **generování kódu** stránku vlastností.  
  
4.  Změnit **povolit propojení na úrovni funkcí** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)