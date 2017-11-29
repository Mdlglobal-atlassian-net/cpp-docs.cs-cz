---
title: "-Qvec-report (úroveň sestav automatickou vektorizací) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e0df8e487f2f79029c73adfbf44cb3873bcfcaa3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Úroveň sestavy s automatickou vektorizací)
Povolí funkci vytváření sestav kompilátoru [automatickou vektorizací](../../parallel/auto-parallelization-and-auto-vectorization.md) a určuje úroveň informační zprávy pro výstup během kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ Qvec-report: 1**  
 Výstupy informační zpráva smyčky, které jsou vectorized for.  
  
 **/ Qvec-sestavy: 2**  
 Výstupy informační zpráva smyčky, které jsou vectorized a cykly, které nejsou vectorized společně s kód důvodu.  
  
 Informace o kódech důvod a zpráv najdete v tématu [nástrojů pro vektorizaci a paralelní zpracování zprávy](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru /Qvec-report v sadě Visual Studio  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**.  
  
2.  V **stránky vlastností** dialogovém **C/C++**, vyberte **příkazového řádku**.  
  
3.  V **další možnosti** zadejte `/Qvec-report:1` nebo `/Qvec-report:2`.  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Nastavení možnosti kompilátoru /Qvec-report prostřednictvím kódu programu  
  
-   Použijte tento příklad kódu v <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Paralelní programování v nativním kódu](http://go.microsoft.com/fwlink/?LinkId=263662)