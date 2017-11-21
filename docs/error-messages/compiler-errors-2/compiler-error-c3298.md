---
title: "C3298 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3298
dev_langs: C++
helpviewer_keywords: C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a21b2d28120cb5e1c936b632d67ff28bb6568210
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3298"></a>C3298 chyby kompilátoru
'constraint_1': 'constraint_2' nelze použít jako omezení, protože omezení ref má 'constraint_2' a 'constraint_1' omezení hodnoty  
  
 Nelze zadat vzájemně se vylučuje charakteristik omezení. Parametr obecného typu nemůže být například omezen na typ hodnoty a odkazového typu.  
  
 Další informace najdete v tématu [omezení obecných parametrů typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3298.  
  
```  
// C3298.cpp  
// compile with: /clr /c   
generic<class T, class U>  
where T : ref class  
where U : T, value class   // C3298  
public ref struct R {};  
```