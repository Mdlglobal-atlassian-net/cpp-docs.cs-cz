---
title: C3381 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a27961694bc5fad4080d8aceaf2f1cb65404319c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251095"
---
# <a name="compiler-error-c3381"></a>C3381 chyby kompilátoru
'assembly': přístup ke specifikátorům sestavení jsou dostupné jenom v kódu kompilovat s možností/CLR  
  
 Nativní typy může být viditelné mimo sestavení, ale můžete zadat jenom sestavení přístupu pro nativní typy v **/CLR** kompilace.  
  
 Další informace najdete v tématu [zadejte viditelnost](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3381.  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```