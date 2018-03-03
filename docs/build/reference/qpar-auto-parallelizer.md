---
title: "-Qpar (automatickou vektorizací) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 073c906e7ecdfcf933e4b91cbcf8d6a77324df76
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (automatický modul pro paralelní zpracování)
Umožňuje [automatickou vektorizací](../../parallel/auto-parallelization-and-auto-vectorization.md) funkce kompilátoru učinit automaticky paralelní smyčky v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>Poznámky  
 Když kompilátor automaticky parallelizes smyčky v kódu, šíří výpočetní mezi více jádry procesoru. Smyčka je paralelizovaná málo pouze v případě, že kompilátor zjistí, že je možné učinit a že paralelizace by zlepšit výkon.  
  
 `#pragma loop()` Direktivy jsou dostupné ke Optimalizátor paralelní konkrétní smyčky. Další informace najdete v tématu [smyčky](../../preprocessor/loop.md).  
  
 Informace o tom, jak povolit výstupní zprávy pro automatickou vektorizací najdete v tématu [/Qpar-report (úroveň sestav automatickou vektorizací)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru /Qpar v sadě Visual Studio  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**.  
  
2.  V **stránky vlastností** dialogovém **C/C++**, vyberte **příkazového řádku**.  
  
3.  V **další možnosti** zadejte `/Qpar`.  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Nastavení možnosti kompilátoru /Qpar prostřednictvím kódu programu  
  
-   Použijte tento příklad kódu v <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [/ Qpar-report (úroveň sestav automatickou vektorizací)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [#pragma loop()](../../preprocessor/loop.md)   
 [Paralelní programování v nativním kódu](http://go.microsoft.com/fwlink/p/?linkid=263662)