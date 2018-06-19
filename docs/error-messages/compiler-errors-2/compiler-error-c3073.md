---
title: C3073 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3073
dev_langs:
- C++
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f565973c386dbaa9c1146756e7ca1b1f75f4b43b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253613"
---
# <a name="compiler-error-c3073"></a>C3073 chyby kompilátoru
'type': Třída ref nemá definovaný uživatelem kopírovacího konstruktoru  
  
 V [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) kompilace, kompilátor nevygeneruje kopírovacího konstruktoru pro odkazového typu. V žádném **/CLR** kompilace, je nutné definovat vlastní kopírovací konstruktor pro typ odkaz Pokud očekáváte, že instance typu, který se má zkopírovat.  
  
 Další informace najdete v tématu [C++ – sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3073.  
  
```  
// C3073.cpp  
// compile with: /clr  
ref class R {  
public:  
   R(int) {}  
};  
  
ref class S {  
public:  
   S(int) {}  
   S(const S %rhs) {}   // copy constructor  
};  
  
void f(R) {}  
void f2(S) {}  
void f3(R%){}  
  
int main() {  
   R r(1);  
   f(r);   // C3073  
   f3(r);   // OK  
  
   S s(1);  
   f2(s);   // OK  
}  
```