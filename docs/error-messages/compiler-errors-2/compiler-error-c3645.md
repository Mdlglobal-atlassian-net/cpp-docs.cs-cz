---
title: C3645 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3645
dev_langs:
- C++
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a711f37e3ab54de5e3cfad77b82fbd603edfaf6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263824"
---
# <a name="compiler-error-c3645"></a>C3645 chyby kompilátoru
'function': __clrcall nelze použít na funkce, zkompilované na nativní kód  
  
 Přítomnost některé klíčová slova ve funkci způsobí, že funkce, která má být zkompilovány v nativním režimu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3645.  
  
```  
// C3645.cpp  
// compile with: /clr /c  
#pragma unmanaged   
int __clrcall dog() {}   // C3645  
```