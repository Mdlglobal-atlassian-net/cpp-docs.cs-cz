---
title: "Uživatelem definované operátory (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b02d6806abedb407d1c53ec8022e92983ce21d28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-operators-ccli"></a>Uživatelem definované operátory (C++/CLI)
Uživatelem definované operátory pro spravované typy jsou povoleny jako statické členy nebo členy instancí nebo v globálním oboru. Jenom statické operátory jsou však přístupné prostřednictvím metadata klientů, které jsou zapsány v jiném jazyce než v jazyce Visual C++.  
  
 V typu odkazu. jeden z parametrů statické uživatelem definovaný operátor musí mít jednu z těchto:  
  
-   Popisovač (`type` ^) na instanci nadřazených typů.  
  
-   Indirection odkaz na typ (`type`^ & nebo typ ^ %) na popisovač pro instanci nadřazených typů.  
  
 Typ hodnoty jeden z parametrů statické uživatelem definovaný operátor musí být jeden z těchto:  
  
-   Stejného typu jako nadřazených typ hodnoty.  
  
-   Dereference ukazatel typu (`type`^) do nadřazených typů.  
  
-   Indirection odkaz na typ (`type`% nebo `type`&) do nadřazených typů.  
  
-   Indirection odkaz na typ (`type`^ % nebo `type`^ &) pro popisovač.  
  
 Můžete definovat následující operátory:  
  
|Operátor|Unární nebo binární Forms?|  
|--------------|--------------------------|  
|!|Unární|  
|!=|binární|  
|%|binární|  
|&|Unární ani binární kód.|  
|&&|binární|  
|*|Unární ani binární kód.|  
|+|Unární ani binární kód.|  
|++|Unární|  
|,|binární|  
|-|Unární ani binární kód.|  
|--|Unární|  
|->|Unární|  
|/|binární|  
|<|binární|  
|<<|binární|  
|\<=|binární|  
|=|binární|  
|==|binární|  
|>|binární|  
|>=|binární|  
|>>|binární|  
|^|binární|  
|false|Unární|  
|true|Unární|  
|&#124;|binární|  
|&#124;&#124;|binární|  
|~|Unární|  
  
## <a name="example"></a>Příklad  
  
```cpp  
// mcppv2_user-defined_operators.cpp  
// compile with: /clr  
using namespace System;  
public ref struct X {  
   X(int i) : m_i(i) {}  
   X() {}  
  
   int m_i;  
  
   // static, binary, user-defined operator  
   static X ^ operator + (X^ me, int i) {  
      return (gcnew X(me -> m_i + i));  
   }  
  
   // instance, binary, user-defined operator  
   X^ operator -( int i ) {  
      return gcnew X(this->m_i - i);  
   }  
  
   // instance, unary, user-defined pre-increment operator  
   X^ operator ++() {  
      return gcnew X(this->m_i++);  
   }  
  
   // instance, unary, user-defined post-increment operator  
   X^ operator ++(int i) {  
      return gcnew X(this->m_i++);  
   }  
  
   // static, unary user-defined pre- and post-increment operator  
   static X^ operator-- (X^ me) {  
      return (gcnew X(me -> m_i - 1));  
   }  
};  
  
int main() {  
   X ^hX = gcnew X(-5);  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX + 1;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX - (-1);  
   System::Console::WriteLine(hX -> m_i);  
  
   ++hX;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX++;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX--;  
   System::Console::WriteLine(hX -> m_i);  
  
   --hX;  
   System::Console::WriteLine(hX -> m_i);  
}  
```  
  
```Output  
-5  
-4  
-3  
-2  
-1  
-2  
-3  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje souhrnnou operátor, který je k dispozici pouze při použití **/CLR** zkompilovat. Operátor souhrnnou vytvoří formulář přiřazení binárního operátoru, pokud není definován, kde na levé straně operátor přiřazení má typ CLR.  
  
```cpp  
// mcppv2_user-defined_operators_2.cpp  
// compile with: /clr  
ref struct A {  
   A(int n) : m_n(n) {};  
   static A^ operator + (A^ r1, A^ r2) {  
      return gcnew A( r1->m_n + r2->m_n);  
   };  
   int m_n;  
};  
  
int main() {  
   A^ a1 = gcnew A(10);  
   A^ a2 = gcnew A(20);  
  
   a1 += a2;   // a1 = a1 + a2   += not defined in source  
   System::Console::WriteLine(a1->m_n);  
}  
```  
  
```Output  
30  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)