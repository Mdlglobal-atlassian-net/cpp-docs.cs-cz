---
title: C3299 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3299
dev_langs:
- C++
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecaa0b8d3ee1a3d33a5d750cc559da63e036ff16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3299"></a>C3299 chyby kompilátoru
'member_function': nelze zadat omezení, se dědí z základní metody  
  
 Při přepisování obecné členské funkce, nelze zadat omezení klauzule (s opakováním, omezení znamená, že nejsou zděděné omezení).  
  
 Zdědí klauzulích omezení u obecné funkce, které jsou přepsání.  
  
 Další informace najdete v tématu [omezení obecných parametrů typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3299.  
  
```  
// C3299.cpp  
// compile with: /clr /c  
public ref struct R {  
   generic<class T>   
   where T : R  
   virtual void f();  
};  
  
public ref struct S : R {  
   generic<class T>   
   where T : R   // C3299  
   virtual void f() override;  
};  
```