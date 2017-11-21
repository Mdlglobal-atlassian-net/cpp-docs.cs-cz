---
title: "Upozornění linkerů Lnk4254 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4254
dev_langs: C++
helpviewer_keywords: LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47e8e020cdf8d888e77d212a25fa9344e744e895
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4254"></a>Upozornění linkerů LNK4254
část 'sekci 1' (posun) sloučí sekci "2" (posun) s různé atributy  
  
 Obsah jeden oddíl byly sloučeny do jiné, ale liší se atributy dvě části. Váš program mohou poskytovat neočekávané výsledky. Například data, která jste chtěli číst pouze nyní pravděpodobně v oddílu s možností zápisu.  
  
 Chcete-li vyřešit LNK4254, změnit nebo odebrat požadavek sloučení.  
  
 Pokud je cílem x86 počítače a cíle systém Windows CE (ARM, MIPS, architekturu SH4 a Flash) s Visual C++. Část CRT je jen pro čtení. Pokud váš kód závisí na předchozí chování (. CRT oddíly jsou pro čtení i zápis), může docházet k neočekávanému chování.  
  
 Další informace najdete v tématu,  
  
-   [/ MERGE (kombinované oddíly)](../../build/reference/merge-combine-sections.md)  
  
-   [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK4254.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```