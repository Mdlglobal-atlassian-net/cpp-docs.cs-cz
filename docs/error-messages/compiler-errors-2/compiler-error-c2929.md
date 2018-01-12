---
title: "C2929 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2929
dev_langs: C++
helpviewer_keywords: C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64842c40bb2e773bd3c935e0de3664943522e7b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2929"></a>C2929 chyby kompilátoru
"identifikátor": explicitní vytvoření instance; Nelze explicitně vynutit a potlačit vytvoření instance šablony třídy člena  
  
 Zároveň je možné zabránit vytvoření instancí nelze explicitně doložit identifikátor.  
  
 Následující ukázka generuje C2929:  
  
```  
// C2929.cpp  
// compile with: /c  
template<typename T>  
class A {  
public:  
   A() {}  
};  
  
template A<int>::A();  
  
extern template A<int>::A();   // C2929  
```