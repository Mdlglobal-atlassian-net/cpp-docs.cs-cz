---
title: C2790 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11f1c90fed93666fad7513e2b4186a5baa2aa406
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2790"></a>C2790 chyby kompilátoru
'super: Toto klíčové slovo lze použít pouze v hlavní funkce člena třídy  
  
 Tato chybová zpráva se zobrazí, pokud uživatel někdy pokusí používá klíčové slovo [super](../../cpp/super.md) mimo kontext členské funkce.  
  
 Následující ukázka generuje C2790:  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```