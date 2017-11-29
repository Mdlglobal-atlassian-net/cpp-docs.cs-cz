---
title: "-GA (optimalizace pro aplikaci systému Windows) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs: C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 51da2e950a28efdc8ff1159c9316b8068baabed0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ga-optimize-for-windows-application"></a>/GA (optimalizace pro aplikaci systému Windows)
Výsledkem efektivnější kód pro soubor .exe pro přístup k proměnným úložiště thread-local (TLS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GA  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GA** rychlosti přístupu k datům deklarovat s [__declspec(thread)](../../cpp/declspec.md) v programu systému Windows. Pokud je tato možnost nastavená, [__tls_index](http://msdn.microsoft.com/library/windows/desktop/ms686749) makro se předpokládá, že chcete-li být 0.  
  
 Pomocí **/GA** pro knihovny DLL může mít za následek generování chybného kódu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)