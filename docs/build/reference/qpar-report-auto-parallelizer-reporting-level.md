---
title: "-Qpar-report (úroveň sestav automatickou vektorizací) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 96dff858d068f9d9bf9c6c47e1f444603c2a5729
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (úroveň sestav s automatickou vektorizací)
Povolí funkci vytváření sestav v kompilátoru [automatickou vektorizací](../../parallel/auto-parallelization-and-auto-vectorization.md) a určuje úroveň informační zprávy pro výstup během kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qpar-report:{1}{2}  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ Qpar-report: 1**  
 Výstupy informační zpráva smyčky, které jsou paralelizovaná málo for.  
  
 **/ Qpar-sestavy: 2**  
 Výstupy informační zpráva pro cykly, které jsou paralelizovaná málo a také pro cykly, které nejsou paralelizovaná málo společně s kód důvodu.  
  
 Zprávy jsou hlášeny stdout. Pokud žádné informační zprávy nahlásí, pak buď kód obsahuje žádné smyčky nebo úroveň sestav nebyl nastaven na smyčky sestavy, které nejsou paralelizovaná málo. Další informace o kódech důvod a zpráv najdete v tématu [nástrojů pro vektorizaci a paralelní zpracování zprávy](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru /Qpar-report v sadě Visual Studio  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**.  
  
2.  V **stránky vlastností** dialogovém **C/C++**, vyberte **příkazového řádku**.  
  
3.  V **další možnosti** zadejte `/Qpar-report:1` nebo `/Qpar-report:2`.  
  
### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Nastavení možnosti kompilátoru /Qpar-report prostřednictvím kódu programu  
  
-   Použijte tento příklad kódu v <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Paralelní programování v nativním kódu](http://go.microsoft.com/fwlink/?LinkId=263662)