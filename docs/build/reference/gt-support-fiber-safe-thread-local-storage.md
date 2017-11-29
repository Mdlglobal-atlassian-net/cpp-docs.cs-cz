---
title: "-GT (Podpora úložiště Thread-Local zabezpečenými Vlákénky) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs: C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5912f241716bbaf9aba989dabbeb25d38ab465c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Podpora úložiště Thread-Local se zabezpečenými vlákénky)
Podporuje zabezpečení fiber pro data přidělen s použitím statické úložiště thread-local, to znamená, data, kterým je přiřazen `__declspec(thread)`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GT  
```  
  
## <a name="remarks"></a>Poznámky  
 Data deklarovat s `__declspec(thread)` se odkazuje prostřednictvím pole úložiště thread-local (TLS). Pole protokol TLS je pole adresy, které systém udržuje pro každé vlákno. Každou adresu v toto pole poskytuje umístění úložiště thread-local data.  
  
 Vlákno je objekt lightweight, který se skládá z zásobníku a kontext registrace a můžete naplánovat na různých vláken. Fiber můžete spustit na jakékoli vlákno. Protože fiber může získat odložit a restartovat později na jiném podprocesu, adresu TLS pole nesmí být do mezipaměti nebo optimalizovány jako běžné dílčím výrazu prostřednictvím volání funkce (viz [/Og (globální optimalizace)](../../build/reference/og-global-optimizations.md) možnost Podrobnosti). **/Gt optického** brání takové optimalizace.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **optimalizace** stránku vlastností.  
  
4.  Změnit **povolit optimalizace zabezpečenými** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)