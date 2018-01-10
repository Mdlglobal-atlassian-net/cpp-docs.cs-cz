---
title: "C3367 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3367
dev_langs: C++
helpviewer_keywords: C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e341266c37411d96a4cf313e6a101e48aeb2a85d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3367"></a>C3367 chyby kompilátoru
'static_member_function': statické funkce nelze použít k vytvoření nepřipojeného delegáta  
  
Při volání delegáta nevázaný musí předat instanci objektu. Vzhledem k tomu, že statické členské funkce je volána prostřednictvím název třídy, můžete pouze instance delegáta nesvázanou s funkcí člen instance.  
  
Další informace o nevázaní delegáti najdete v tématu [postupy: definování a používání delegátů (C + +/ CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3367.  
  
```cpp  
// C3367.cpp  
// compile with: /clr  
ref struct R {  
   void b() {}  
   static void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::b);   // OK  
   Del ^ b = gcnew Del(&R::f);   // C3367  
}  
```