---
title: Obecní delegáti (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ecbfebc49f76eee7bb753af3d07052d1e05d73be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="generic-delegates-visual-c"></a>Obecní delegáti (Visual C++)
Parametry obecného typu můžete použít s delegáti. Další informace o delegáti najdete v tématu [delegáta (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers>  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `attributes` (Volitelné)  
 Další deklarativní informace. Další informace o atributy a třídy atributů najdete v tématu atributy.  
  
 *Typ-parametr-identifikátory*  
 Čárkami oddělený seznam identifikátory pro parametry typu.  
  
 `type-parameter-constraints-clauses`  
 Má podobu uvedený v [omezení obecných parametrů typů (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *Modifikátory dostupnosti* (volitelné)  
 Modifikátory dostupnosti (například **veřejné**, `private`).  
  
 *Typ výsledku*  
 Návratový typ delegáta.  
  
 *Identifikátor*  
 Název delegát.  
  
 *Parametry formal* (volitelné)  
 Seznam parametrů delegáta.  
  
## <a name="example"></a>Příklad  
 V okamžiku, kdy je vytvořen objekt delegáta jsou zadány parametry typu delegáta. Delegát i přidružená metoda musí mít stejným podpisem. Následuje příklad obecný delegát deklarace.  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, že  
  
-   Nelze použít stejný objekt delegáta s jinou sestavené typy. Vytvořte různé delegáta pro různé typy objektů.  
  
-   – Obecný delegát může být přidružen obecná metoda.  
  
-   Když obecná metoda je volána bez zadání argumenty typu, pokusí se kompilátor odvození typu argumenty pro volání.  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic <class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic <class ItemType>  
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
int main() {  
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();  
   GenDelegate<int>^ myDelegate1 =  
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   GenDelegate<double>^ myDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   GenDelegate<int>^ myDelegate =  
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí obecný delegát `GenDelegate<ItemType>`a potom vytvoří instanci tím, že přidružíte metodě `MyMethod` používající parametr typu `ItemType`. Dvě instance delegáta (celé číslo a dvojitou) jsou vytvořeny a volání.  
  
```  
// generics_generic_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare generic delegate  
generic <typename ItemType>  
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);  
  
// Declare a generic class:  
generic <typename ItemType>  
ref class MyGenClass {  
public:  
   ItemType MyMethod(ItemType p1, ItemType% p2) {  
      p2 = p1;  
      return p1;  
    }  
};  
  
int main() {  
   int i = 0, j = 0;   
   double m = 0.0, n = 0.0;  
  
   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();   
  
   // Instantiate a delegate using int.  
   GenDelegate<int>^ MyDelegate1 =   
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   i = MyDelegate1(123, j);  
  
   Console::WriteLine(  
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);  
  
   // Instantiate a delegate using double.  
   GenDelegate<double>^ MyDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   m = MyDelegate2(0.123, n);  
  
   Console::WriteLine(  
      "Invoking the double delegate: m = {0}, n = {1}", m, n);  
}  
```  
  
```Output  
Invoking the integer delegate: i = 123, j = 123  
Invoking the double delegate: m = 0.123, n = 0.123  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)