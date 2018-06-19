---
title: -Qpar (automatickou vektorizací) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 430bf1ebc79008d97435ecbcb3b15cf19dda5f8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375685"
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