---
title: "C3222 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3222
dev_langs: C++
helpviewer_keywords: C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: edc882f340e92defeaa2db92d868680f7791e7b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
