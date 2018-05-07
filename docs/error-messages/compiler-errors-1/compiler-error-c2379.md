---
title: C2379 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1016bedfa9df0e9dfacb56734ee60397108d046
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2379"></a>C2379 chyby kompilátoru
formální parametr číslo je jiného typu povýšení  
  
 Typ zadaného parametru není kompatibilní, prostřednictvím výchozí povýšení s typem v předchozí deklaraci. Jedná se o chybu v ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění s rozšíření Microsoft (**/Ze**).  
  
 Následující ukázka generuje C2379:  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```