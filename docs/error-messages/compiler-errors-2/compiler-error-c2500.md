---
title: "C2500 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2500
dev_langs: C++
helpviewer_keywords: C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2b869ca0ba959e9b774a005298ef4456d0995156
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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