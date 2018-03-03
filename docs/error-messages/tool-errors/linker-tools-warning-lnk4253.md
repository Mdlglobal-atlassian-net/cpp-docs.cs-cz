---
title: "Upozornění linkerů Lnk4253 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d1142544852980b8bd1d543783a9ffdf3361879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4253"></a>Upozornění linkerů LNK4253
část sekci ' 1' není sloučí sekci "2"; již sloučí 'section3.  
  
 Linkeru zjistila víc požadavků konfliktní sloučení. Linkeru bude ignorovat jeden žádosti.  
  
 A **/MERGE** je zjištěn možnost nebo směrnice a `from` části již byla sloučena do jiné části z důvodu předchozí **/MERGE** možnost nebo – direktiva (nebo z důvodu implicitní korespondence z linker).  
  
 Chcete-li vyřešit LNK4253, odeberte jedno z požadavky sloučení.  
  
 Pokud je cílem x86 počítače a cíle systém Windows CE (ARM, MIPS, architekturu SH4 a Flash) s Visual C++. Část CRT je nyní jen pro čtení. Pokud váš kód závisí na předchozí chování (. CRT oddíly jsou pro čtení i zápis), může docházet k neočekávanému chování.  
  
 Další informace najdete v tématu,  
  
-   [/ MERGE (kombinované oddíly)](../../build/reference/merge-combine-sections.md)  
  
-   [comment (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Příklad  
 V následující ukázce linkeru je odeslán pokyn k sloučení `.rdata` části dvakrát, ale do různých oddílů. Následující ukázka generuje LNK4253.  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```