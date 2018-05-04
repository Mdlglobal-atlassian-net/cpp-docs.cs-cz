---
title: -Od (zakázat (ladění)) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e287a9991f8192f16ec2f93e4068dc797ff72a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="od-disable-debug"></a>/Od (Zakázat (ladění))
Vypne všechny optimalizace programu a urychlí kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Od  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost je výchozí. Protože **/Od** potlačí pohyb kódu se zjednodušuje proces ladění. Další informace o možnostech kompilátoru pro ladění, najdete v části [/Z7, / zi, /ZI (formát informace ladění)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **optimalizace** stránku vlastností.  
  
4.  Změnit **optimalizace** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/Z7, /Zi, /ZI (formát informací o ladění)](../../build/reference/z7-zi-zi-debug-information-format.md)