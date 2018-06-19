---
title: 'Postupy: deklarace hodnotových typů s použitím klíčového slova interior_ptr (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6015d5a61589b8ed2d38b6491392fd42e4f38ef1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879474"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)
`interior_ptr` Lze použít s typ hodnoty.  
  
> [!IMPORTANT]
>  Tato funkce jazyk podporuje **/CLR** – možnost kompilátoru, ale nejsou nástrojem **/ZW** – možnost kompilátoru.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující C + +/ CLI příklad ukazuje, jak používat `interior_ptr` s typ hodnoty.  
  
### <a name="code"></a>Kód  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### <a name="output"></a>Výstup  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V typu hodnoty `this` interior_ptr vyhodnotí jako ukazatel.  
  
 V těle nestatické členské – funkce typu hodnoty `V`, `this` je výraz typu `interior_ptr<V>` jehož hodnota je adresa objektu, pro kterou je tato funkce volána.  
  
### <a name="code"></a>Kód  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje způsob použití address-of – operátor s statické členy.  
  
 Adresa je statický člen typu Visual C++ poskytuje nativní ukazatel.  Adresu statické hodnoty Typ člena je spravovaný ukazatel, protože hodnota typ člena je přidělená v haldě runtime a přesunout modulem garbage collector v.  
  
### <a name="code"></a>Kód  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### <a name="output"></a>Výstup  
  
```  
22  
23  
hello  
```  
  
## <a name="see-also"></a>Viz také  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)