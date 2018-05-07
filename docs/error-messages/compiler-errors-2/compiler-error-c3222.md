---
title: C3222 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 424c0f1011d984dff59d3d952347ad4f7b90f515
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3222"></a>C3222 chyby kompilátoru
"parametr": výchozí argumenty pro člena nelze deklarovat, funkce spravované nebo WinRT typu nebo obecné funkce  
  
Není povoleno deklarovat parametru metody s argumentem výchozí. Formuláře přetížené metody, je jedním ze způsobů, chcete-li vyřešit tento problém. To znamená definovat metodu se stejným názvem bez parametrů a potom inicializujte proměnnou v těle metoda.  
  
Následující ukázka generuje C3222:  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  
