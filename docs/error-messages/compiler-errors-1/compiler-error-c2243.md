---
title: C2243 chyby kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bc95540488b0723869c735b7fc80b15f6e763b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2243"></a>C2243 chyby kompilátoru
převod 'Převod type' z 'type1' na 'type2' existuje, ale je nedostupná  
  
 Přístup k ochrany (`protected` nebo `private`) nebylo možné provést převod ukazatel na odvozené třídy na ukazatel na základní třídy.  
  
 Následující ukázka generuje C2243:  
  
```  
// C2243.cpp  
// compile with: /c  
class B {};  
class D : private B {};  
class E : public B {};  
  
D d;  
B *p = &d;   // C2243  
  
E e;  
B *p2 = &e;  
```  
  
 Základní třídy s `protected` nebo `private` přístup nejsou přístupné pro klienty odvozené třídy. Tyto úrovně řízení přístupu slouží k označení, že je základní třídy implementaci podrobností, která by měla být neviditelná klientům. Veřejné odvození použijte, pokud chcete klientům odvozené třídy mají přístup k implicitní převod odvozené třídy ukazatele na ukazatel na základní třídy.