---
title: "Upozornění linkerů Lnk4253 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4253
dev_langs: C++
helpviewer_keywords: LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fe7e60c3066e2981f1b826381691950b2ccd46d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4253"></a>Upozornění linkerů LNK4253
část sekci ' 1' není sloučí sekci "2"; již sloučí 'section3.  
  
 Linkeru zjistila víc požadavků konfliktní sloučení. Linkeru bude ignorovat jeden žádosti.  
  
 A **/MERGE** je zjištěn možnost nebo směrnice a `from` části již byla sloučena do jiné části z důvodu předchozí **/MERGE** možnost nebo – direktiva (nebo z důvodu implicitní korespondence z linker).  
  
 Chcete-li vyřešit LNK4253, odeberte jedno z požadavky sloučení.  
  
 Pokud je cílem x86 počítače a cíle systém Windows CE (ARM, MIPS, architekturu SH4 a Flash) s Visual C++. Část CRT je nyní jen pro čtení. Pokud váš kód závisí na předchozí chování (. CRT oddíly jsou pro čtení i zápis), může docházet k neočekávanému chování.  
  
 Další informace najdete v tématu,  
  
-   [/ MERGE (kombinované oddíly)](../../build/reference/merge-combine-sections.md)  
  
-   [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Příklad  
 V následující ukázce linkeru je odeslán pokyn k sloučení `.rdata` části dvakrát, ale do různých oddílů. Následující ukázka generuje LNK4253.  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```