---
title: Kompilátoru (úroveň 1) upozornění C4216 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4216
dev_langs:
- C++
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de645b2d036e7ed696a8065bbb9f8212ec5c596
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279607"
---
# <a name="compiler-warning-level-1-c4216"></a>C4216 kompilátoru upozornění (úroveň 1)
nestandardní rozšíření používané: dlouho float  
  
 Rozšíření Microsoft výchozí (/Ze) považovat **float dlouho** jako **dvojité**. Kompatibilita ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) neexistuje. Použití **dvojité** pro zachování kompatibility. Následující ukázka generuje C4216:  
  
```  
// C4216.cpp  
// compile with: /W1  
float long a;   // C4216  
  
// use the line below to resolve the warning  
// double a;  
  
int main() {  
}  
```