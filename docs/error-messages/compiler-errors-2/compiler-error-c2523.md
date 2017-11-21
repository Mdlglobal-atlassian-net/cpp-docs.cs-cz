---
title: "C2523 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2523
dev_langs: C++
helpviewer_keywords: C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9ec6a9196498f210e680acf17efd34ac84faf77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2523"></a>C2523 chyby kompilátoru
' třída:: ~ identifikátor ': Neshoda značky destruktor/finalizační metodu  
  
 Název destruktoru musí být název třídy sebou tildou (`~`). Konstruktor a destruktor jsou pouze členové, které mají stejný název jako třída.  
  
 Následující ukázka generuje C2523:  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```