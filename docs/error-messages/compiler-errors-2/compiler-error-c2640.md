---
title: C2640 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2640
dev_langs:
- C++
helpviewer_keywords:
- C2640
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6951d6d56fa0e93e75725c5ce5b13fec7f3d78f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228872"
---
# <a name="compiler-error-c2640"></a>C2640 chyby kompilátoru
"identifikátor": __based – modifikátor neplatná na odkaz  
  
 `__based` Modifikátor lze použít pouze ukazatelů.  
  
 Následující ukázka generuje C2640:  
  
```  
// C2640.cpp  
void f(int i) {  
    void *vp;  
    int _based(vp) &vr = I;  // C2640  
}  
```