---
title: C2500 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c05ffd59e415375dd3c7f94ae9bc377c0fc2b9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229219"
---
# <a name="compiler-error-c2500"></a>C2500 chyby kompilátoru
'identifier1': 'identifier2' je již přímé základní třída  
  
 Třídu nebo strukturu, zobrazí se více než jednou, v seznamu základní třídy.  
  
 Přímé základní je uvedených v seznamu základní. Nepřímý základní je základní třídou jednoho v seznamu základní třídy.  
  
 Třídu nelze zadat jako přímý základní třída více než jednou. Třída slouží jako nepřímé základní třída více než jednou.  
  
 Následující ukázka generuje C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```