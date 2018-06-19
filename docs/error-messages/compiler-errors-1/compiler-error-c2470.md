---
title: C2470 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2470
dev_langs:
- C++
helpviewer_keywords:
- C2470
ms.assetid: e17d2cb8-b84c-447c-976a-625f0c96f3fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcd0a8d0d860bb4c3514d31099626cc578339149
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196711"
---
# <a name="compiler-error-c2470"></a>C2470 chyby kompilátoru
'function': vypadá jako definice funkce, ale neexistuje žádný seznam parametrů; přeskočení zřejmá textu  
  
 Definice funkce chybí jeho seznam argumentů.  
  
 Následující ukázka generuje C2470:  
  
```  
// C2470.cpp  
int MyFunc {};  // C2470  
void MyFunc2() {};  //OK  
  
int main(){  
   MyFunc();  
   MyFunc2();  
}  
```