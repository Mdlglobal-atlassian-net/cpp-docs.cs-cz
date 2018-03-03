---
title: "C2383 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f89545b9428bd5e901c72d895b5c23317646c26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2383"></a>C2383 chyby kompilátoru
'*symbol*': výchozí argumenty nejsou povoleny na tento symbol  
  
 Kompilátor C++ neumožňuje výchozí argumenty ukazatelů na funkce.  
  
 Tento kód byl přijat ve Visual C++ compiler ve verzi před Visual Studio 2005, ale teď obsahuje chybu. Pro kód, který funguje ve všech verzích Visual C++ nepřiřazujte výchozí hodnota pro argument ukazatel funkce.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C2383 a zobrazuje možná řešení:  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```