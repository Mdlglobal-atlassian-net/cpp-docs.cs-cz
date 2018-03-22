---
title: Operátor sledovacího odkazu (rozšíření komponent C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '%'
dev_langs:
- C++
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cbf1483c66bd8472149539af84b83755cae43cf
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="tracking-reference-operator-c-component-extensions"></a>Operátor sledovacího odkazu (rozšíření komponent C++)
A *sledovací odkaz* (`%`) se chová stejně jako obyčejnou referenční příručka C++ (`&`) s tím rozdílem, že když je objekt přiřazení sledovací odkaz, se zvýší počet odkazů objektu.  
  
## <a name="all-platforms"></a>Všechny platformy  
 Sledovací odkaz má následující vlastnosti.  
  
-   Přiřazení objektu sledovací odkaz způsobí, že se zvýší počet odkaz objektu.  
  
-   Nativní referenční dokumentace (&) je výsledek, když jste dereference *. Sledovací odkaz (%) je výsledek, když jste dereference ^. Tak dlouho, dokud máte % k objektu, objekt zůstanou aktivní v paměti.  
  
-   Tečky (`.`) operátor přístup ke členu se používá pro přístup ke členu objektu.  
  
-   Sledovací odkazy jsou platné pro typy hodnot a obslužné rutiny (například `String^`).  
  
-   Sledovací odkaz nelze přiřadit hodnotu null nebo `nullptr` hodnotu. Sledovací odkaz může přeřazena na jiný platný objekt tolikrát, kolikrát podle potřeby.  
  
-   Sledovací odkaz nelze použít jako adresu proveďte unární operátor.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Sledovací odkaz se chová jako odkaz na standardní C++, s tím rozdílem, že % je počítáno odkaz. Následující fragment kódu ukazuje, jak pro převod mezi % a ^ typy:  
  
```  
Foo^ spFoo = ref new Foo();  
Foo% srFoo = *spFoo;  
Foo^ spFoo2 = %srFoo;  
```  
  
 Následující příklad ukazuje, jak předat ^ funkce, která přebírá %.  
  
```  
  
ref class Foo sealed {};  
  
    // internal or private  
    void UseFooHelper(Foo% f)  
    {  
        auto x = %f;  
    }  
  
    // public method on ABI boundary  
    void UseFoo(Foo^ f)  
    {  
        if (f != nullptr) { UseFooHelper(*f); }  
    }  
```  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 V jazyce C + +/ CLI, můžete použít sledování odkaz na popisovač při vytvoření vazby na objekt typu CLR v haldě uvolňování paměti.  
  
 V modulu CLR, hodnota odkazu sledování proměnné se aktualizuje automaticky vždy, když má systém uvolňování přesune odkazovaného objektu.  
  
 Sledovací odkaz lze deklarovat pouze v zásobníku. Sledovací odkaz nemůže být členem třídy.  
  
 Není možné, že nativní C++ odkaz na objekt v haldě uvolňování paměti.  
  
 Další informace o sledování odkazů v jazyce C + +/ CLI, najdete v části:  
  
-   [Postupy: Používání sledovacích odkazů v jazyce C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující ukázka pro C + +/ CLI ukazuje způsob použití sledovací odkaz s typy nativní a spravovaná.  
  
```  
// tracking_reference_1.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
};  
  
value struct MyStruct {  
   int k;  
};  
  
int main() {  
   MyClass ^ x = ref new MyClass;  
   MyClass ^% y = x;   // tracking reference handle to reference object   
  
   int %ti = x->i;   // tracking reference to member of reference type  
  
   int j = 0;  
   int %tj = j;   // tracking reference to object on the stack  
  
   int * pi = new int[2];  
   int % ti2 = pi[0];   // tracking reference to object on native heap  
  
   int *% tpi = pi;   // tracking reference to native pointer  
  
   MyStruct ^ x2 = ref new MyStruct;  
   MyStruct ^% y2 = x2;   // tracking reference to value object  
  
   MyStruct z;  
   int %tk = z.k;   // tracking reference to member of value type  
  
   delete[] pi;  
}  
  
```  
  
 **Příklad**  
  
 Následující ukázka pro C + +/ CLI ukazuje, jak vytvořit vazbu sledovací odkaz na pole.  
  
```  
// tracking_reference_2.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   array<int> ^ a = ref new array<Int32>(5);  
   a[0] = 21;  
   Console::WriteLine(a[0]);  
   array<int> ^% arr = a;  
   arr[0] = 222;  
   Console::WriteLine(a[0]);  
}  
```  
  
 **Output**  
  
```Output  
21  
222  
```