---
title: -Qsafe_fp_loads | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2b2ce52d-ba57-4bd3-a739-47a7f8bfaba9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9e572c8a4d353aaee4e82e8c7bdc3f719475c03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads
Vyžaduje pokyny pro přesunutí celé číslo s plovoucí desetinnou čárkou a zakáže optimalizace určité zatížení s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qsafe_fp_loads  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ Qsafe_fp_loads** je dostupný jenom v kompilátory, cílový x86; není k dispozici v kompilátory, které cílí x64 nebo ARM.  
  
 **/ Qsafe_fp_loads** vynutí kompilátor použijte pokyny pro přesunutí celé číslo místo s plovoucí desetinnou čárkou přesunutí pokynů pro přesun dat mezi pamětí a MMX zaregistruje. Tato možnost zakáže také zaregistrovat zatížení optimalizace pro hodnoty s plovoucí desetinnou čárkou, které je možné načíst v více cest řízení, pokud hodnota může způsobit výjimku na zatížení – například hodnotou NaN.  
  
 Tato možnost je přepsat [/fp: kromě](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** určuje podmnožinu chování kompilátoru, která je zadána **/fp: kromě**.  
  
 **/ Qsafe_fp_loads** není kompatibilní s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) a [/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md). Další informace o možnosti kompilátoru plovoucí bodu najdete v tématu [/fp (zadejte Floating-Point chování)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)