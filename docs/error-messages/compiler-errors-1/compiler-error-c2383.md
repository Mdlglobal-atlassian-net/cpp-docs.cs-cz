---
title: C2383 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81624ccd7f4857cb2f7d8474d393a9743ab1a2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196490"
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