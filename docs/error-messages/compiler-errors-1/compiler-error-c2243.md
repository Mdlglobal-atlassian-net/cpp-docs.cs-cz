---
title: "C2243 chyby kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2243
dev_langs: C++
helpviewer_keywords: C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9725239c7e7b8899c23584aa56d26ed77bd757a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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