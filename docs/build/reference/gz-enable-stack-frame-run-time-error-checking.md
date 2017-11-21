---
title: "-GZ (Povolit zásobníku rámečku Kontrola chyb za běhu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /gz
dev_langs: C++
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3e4dc59154d64d79db0f4d15471b51ce67bed58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Povolit běhovou kontrolu chyb rámce zásobníku)
Provádí stejné operace, jako [/RTC (kontroluje chyby Run-Time)](../../build/reference/rtc-run-time-error-checks.md) možnost. Zastaralé  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GZ  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GZ** jsou pouze pro použití v nonoptimized ([/Od (zakázat (ladění))](../../build/reference/od-disable-debug.md)) sestavení.  
  
 **/GZ** je zastaralé od verze Visual Studio 2005; použít [/RTC (kontroluje chyby Run-Time)](../../build/reference/rtc-run-time-error-checks.md) místo. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
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