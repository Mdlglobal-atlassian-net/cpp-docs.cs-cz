---
title: C2833 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff066510292690bc940f18ab8d63605eb8627308
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244107"
---
# <a name="compiler-error-c2833"></a>C2833 chyby kompilátoru
'operátor operátor' není rozpoznaný operátor nebo typ  
  
 Slovo `operator` musí následovat operátor, který chcete přepsat, nebo typu, který chcete převést.  
  
 Seznam operátory, které lze definovat v spravovaného typu, najdete v části [uživatelem definované operátory](../../dotnet/user-defined-operators-cpp-cli.md).  
  
 Následující ukázka generuje C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```