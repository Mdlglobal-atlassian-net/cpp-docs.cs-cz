---
title: Upozornění linkerů Lnk4253 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae4e88e1fe1434cd638d5c31cc8fd4d5c02c4de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4253"></a>Upozornění linkerů LNK4253
část sekci ' 1' není sloučí sekci "2"; již sloučí 'section3.  
  
 Linkeru zjistila víc požadavků konfliktní sloučení. Linkeru bude ignorovat jeden žádosti.  
  
 A **/MERGE** je zjištěn možnost nebo směrnice a `from` části již byla sloučena do jiné části z důvodu předchozí **/MERGE** možnost nebo – direktiva (nebo z důvodu implicitní korespondence z linker).  
  
 Chcete-li vyřešit LNK4253, odeberte jedno z požadavky sloučení.  
  
 Pokud je cílem x86 počítače a cíle systém Windows CE (ARM, MIPS, architekturu SH4 a Flash) s Visual C++. Část CRT je nyní jen pro čtení. Pokud váš kód závisí na předchozí chování (. CRT oddíly jsou pro čtení i zápis), může docházet k neočekávanému chování.  
  
 Další informace najdete v tématu,  
  
-   [/MERGE (sloučení oddílů)](../../build/reference/merge-combine-sections.md)  
  
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