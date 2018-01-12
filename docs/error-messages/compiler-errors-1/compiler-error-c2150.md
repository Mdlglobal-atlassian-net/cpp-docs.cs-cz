---
title: "C2150 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2150
dev_langs: C++
helpviewer_keywords: C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d31a8767f05ba8c58e07ffbabed4e7a96a919e6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2150"></a>C2150 chyby kompilátoru
  
> '*identifikátor*': bit pole musí mít typ int, 'podepsaný int' nebo 'unsigned int.  
  
 Základní typ pro bitové pole musí být `int`, `signed int`, nebo `unsigned int`.  
  
## <a name="example"></a>Příklad  
  
 Tento příklad ukazuje, jak můžete setkat C2150 a jak můžete opravit:  
  
```cpp  
// C2150.cpp  
// compile with: /c  
struct A {  
   float a : 8;    // C2150  
   int i : 8;      // OK  
};  
```