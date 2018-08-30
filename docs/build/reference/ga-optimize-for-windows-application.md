---
title: -GA (optimalizace pro aplikaci Windows) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs:
- C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61bf8844a5471a97214ca6f3d3b5b473c9cd6217
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194660"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (optimalizace pro aplikaci systému Windows)
Výsledkem efektivnější kód pro soubor s příponou .exe pro přístup k proměnné úložiště thread local (TLS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GA  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GA** rychlosti přístupu k datům deklarována s [__declspec(thread)](../../cpp/declspec.md) v systému Windows. Když nastavíte tuto možnost, [__tls_index](/windows/desktop/ProcThread/thread-local-storage) makra je považován za 0.  
  
 Pomocí **/GA** pro knihovnu DLL může vést k generování chybného kódu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte na tlačítko **C/C++** složky.  
  
3.  Klikněte na tlačítko **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do kompilátoru **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)