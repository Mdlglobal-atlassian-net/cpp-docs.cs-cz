---
title: C3622 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d8c7ab18bfba899c2df41becb457ed2e7725f81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260089"
---
# <a name="compiler-error-c3622"></a>C3622 chyby kompilátoru
'class': třídu deklarovaných jako '– klíčové slovo' nelze vytvořit instanci  
  
Byl proveden pokus o vytvoření instance třídy, označen jako [abstraktní](../../windows/abstract-cpp-component-extensions.md). Třída označen jako `abstract` může být základní třídy, ale nemůže být vytvořena instance.  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3622.  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
