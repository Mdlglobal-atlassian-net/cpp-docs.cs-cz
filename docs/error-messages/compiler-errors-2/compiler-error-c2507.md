---
title: C2507 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2507
dev_langs:
- C++
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82bd4fb028712093a44ada4ae58e97c2fbcf7eed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230532"
---
# <a name="compiler-error-c2507"></a>C2507 chyby kompilátoru
"identifikátor": příliš mnoho virtuálních modifikátory na základní třídě.  
  
 Třídu nebo strukturu je deklarován jako `virtual` více než jednou. Pouze jeden `virtual` modifikátoru může zobrazit pro každou třídu v seznamu základní třídy.  
  
 Následující ukázka generuje C2507:  
  
```  
// C2507.cpp  
// compile with: /c  
class A {};  
class B : virtual virtual public A {};   // C2507  
class C : virtual public A {};   // OK  
```