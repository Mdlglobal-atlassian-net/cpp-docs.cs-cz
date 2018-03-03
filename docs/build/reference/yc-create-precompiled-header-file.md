---
title: "-Yc (Vytvořit předkompilovaný hlavičkový soubor) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865b5e0fa7039a0b60f524c2f13a367569757d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Vytvořit předkompilovaný hlavičkový soubor)
Dá pokyn kompilátoru vytvořte soubor předkompilovaných hlaviček (.pch), který představuje stav kompilace v určitém místě.  
  
## <a name="syntax"></a>Syntaxe  
  
> __/Yc__
> __/Yc__*filename*  
  
  
## <a name="arguments"></a>Arguments  
*Název souboru*  
 Určuje soubor hlavičky (). Pokud se používá tento argument, kompilátor zkompiluje všechny kódu do a včetně souboru h.  
  
## <a name="remarks"></a>Poznámky  
 Když **/Yc** je zadán bez argument, kompilátor kompiluje všechny kód do konce základní zdrojového souboru, nebo do bodu v základního souboru kde [hdrstop –](../../preprocessor/hdrstop.md) – direktiva dojde. Výsledný soubor .pch má stejný název základní jako základní zdrojový soubor, pokud neurčíte název jiný soubor pomocí **hdrstop –** – Direktiva pragma nebo **/Fp** možnost.  
  
 Předkompilované kód je uložená v souboru s názvem vytvořené z základní název souboru zadaný **/Yc** možnost a .pch rozšíření. Můžete také [/Fp (název. Soubor pch)](../../build/reference/fp-name-dot-pch-file.md) možnost zadat název předkompilovaný hlavičkový soubor.  
  
 Pokud používáte __/Yc__*filename*, kompilátor kompiluje všechny kód do a včetně zadaný soubor pro pozdější použití s [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) možnost.  
  
 Pokud možnosti __/Yc__*filename* a __/Yu__*filename* dojít na stejném příkazovém řádku a obě odkazovat, nebo implikují, stejný název souboru __/Yc__*filename* přednost. Tato funkce zjednodušuje zápis soubory pravidel.  
  
 Další informace o předkompilovaných hlaviček najdete v tématu:  
  
-   [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)  
  
-   [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Vyberte soubor, sada. Souboru musí #include .h soubor, který obsahuje informace o předkompilovaných hlaviček. Projektu **/Yc** nastavení je možné přepsat na úrovni souborů.  
  
2.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
3.  Otevřete **vlastnosti konfigurace**, **C/C++**, **předkompilovaných hlaviček** stránku vlastností.  
  
4.  Změnit **předkompilovaných hlaviček** vlastnost.  
  
5.  Pokud chcete nastavit název souboru, upravte **předkompilovaný hlavičkový soubor** vlastnost.
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu následující kód:  
  
```cpp  
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
// ...  
```  
  
Pokud je tento kód zkompilovat pomocí příkazu `CL /YcMYAPP.H PROG.CPP`, kompilátor uloží všechny předběžném zpracování pro AFXWIN.h RESOURCE.h, a názvem MYAPP.pch MYAPP.h v předkompilovaný hlavičkový soubor.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md) [vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)