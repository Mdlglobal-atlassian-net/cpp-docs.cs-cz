---
title: "-GX (povolení zpracování výjimek) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /gx
dev_langs: C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3013b4233621e63de0230e088dfc10ff65a5705d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="gx-enable-exception-handling"></a>/GX (povolení zpracování výjimek)
Zastaralé Umožňuje synchronní zpracování výjimek pomocí za předpokladu, že funkce deklarovat pomocí `extern "C"` nikdy vyvolat výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GX  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GX** je zastaralý. Použít ekvivalent [/EHsc](../../build/reference/eh-exception-handling-model.md) místo něj. Seznam – možnosti kompilátoru zastaralé, najdete v článku **zastaralé a odebrat – možnosti kompilátoru** kapitoly [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Ve výchozím nastavení **/EHsc**, ekvivalentní **/GX**, platí, když zkompilujete pomocí vývojovém prostředí sady Visual Studio. Při použití nástroje příkazového řádku, je zadána žádná výjimek. Jedná se o ekvivalent **/GX-**.  
  
 Další informace najdete v tématu [zpracování výjimek C++](../../cpp/cpp-exception-handling.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V navigačním podokně zvolte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku**.  
  
3.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md)