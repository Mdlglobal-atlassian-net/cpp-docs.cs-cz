---
title: Kompilátoru (úroveň 4) upozornění C4212 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4212
dev_langs:
- C++
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb70cf045a1cc563e4eb009ed00ffe82be812b0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292000"
---
# <a name="compiler-warning-level-4-c4212"></a>C4212 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: deklarace funkce používá třemi tečkami  
  
 Prototyp funkce má proměnný počet argumentů. V definici funkce neexistuje.  
  
 Následující ukázka generuje C4212:  
  
```  
// C4212.c  
// compile with: /W4 /Ze /c  
void f(int , ...);  
void f(int i, int j) {}  
```