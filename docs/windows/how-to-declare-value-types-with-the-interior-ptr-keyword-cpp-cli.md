---
title: 'Postupy: deklarace hodnotových typů s použitím klíčového slova interior_ptr (C + +/ CLI) | Dokumentace Microsoftu'
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
ms.openlocfilehash: 38cbfb171e218f70d45e5ef2e6e850d791803611
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571185"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)
**Interior_ptr** jde použít s typem hodnoty.  
  
> [!IMPORTANT]
>  Této funkci jazyka podporuje `/clr` – možnost kompilátoru, ale ne za `/ZW` – možnost kompilátoru.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující C + +/ CLI příklad ukazuje, jak používat **interior_ptr** s typem hodnoty.  
  
### <a name="code"></a>Kód  
  
```cpp  
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
  
```Output  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V typu hodnoty **to** interior_ptr vyhodnocen jako ukazatel.  
  
 V těle nestatická členská funkce typu hodnoty `V`, **to** je výraz typu `interior_ptr<V>` jehož hodnota je adresu objektu, pro kterou je tato funkce volána.  
  
### <a name="code"></a>Kód  
  
```cpp  
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
 Následující příklad ukazuje způsob použití operátoru address-of se statickými členy.  
  
 Adresa statického členu typu Visual C++ poskytuje nativní ukazatel.  Adresu člena typu statické hodnoty je spravovaného ukazatele, protože člen typu hodnoty je přidělen na haldě modulu runtime a je možné přesunout pomocí systému uvolňování paměti.  
  
### <a name="code"></a>Kód  
  
```cpp  
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
  
```Output 
22  
23  
hello  
```  
  
## <a name="see-also"></a>Viz také  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)