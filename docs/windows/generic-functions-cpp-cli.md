---
title: "Obecné funkce (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ebafa409680609d6e097b803be2b539ccdc7601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="generic-functions-ccli"></a>Obecné funkce (C++/CLI)
Obecné funkce je funkce, která je deklarovaný s parametry typu. Při volání, skutečné typy se používají místo parametrů typu.  
  
## <a name="all-platforms"></a>Všechny platformy  
 **Poznámky**  
  
 Tato funkce se nevztahuje na všech platformách.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 Tato funkce není podporována v prostředí Windows Runtime.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 Obecné funkce je funkce, která je deklarovaný s parametry typu. Při volání, skutečné typy se používají místo parametrů typu.  
  
 **Syntaxe**  
  
```  
[attributes] [modifiers]  
return-type identifier<type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{function-body}  
```  
  
 **Parametry**  
  
 *atributy* (volitelné)  
 Další deklarativní informace. Další informace o atributy a třídy atributů najdete v tématu atributy.  
  
 *Modifikátory* (volitelné)  
 Modifikátor pro funkce, například statický.  `virtual`není povolená, protože virtuální metody nesmí být obecný.  
  
 *Návratový typ*  
 Typ vrácený metodou Pokud je návratový typ void, není potřeba žádnou návratovou hodnotu.  
  
 *identifikátor*  
 Název funkce.  
  
 *parametr typu identifikátory*  
 Seznam identifikátorů oddělených čárkami.  
  
 *Parametry formal* (volitelné)  
 Seznam parametrů.  
  
 *Typ parametru omezení klauzule*  
 To určuje omezení na typy, které mohou být použity jako argumenty typu a má podobu uvedený v [omezení obecných parametrů typů (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
 *tělo funkce*  
 Text metodu, která mohou odkazovat na identifikátory parametr typu.  
  
 **Poznámky**  
  
 Obecné funkce jsou funkce deklarovat s parametr obecného typu. Mohou být metody třídy nebo struktura nebo samostatnou funkcí. Jeden obecný deklarace implicitně deklaruje řadu funkcí, které se liší pouze v rámci nahrazování jiný skutečný typ pro parametr obecného typu.  
  
 V jazyce Visual C++ nemusí být konstruktory třídě nebo struktuře deklarovat s parametry obecného typu.  
  
 Při volání, skutečný typ nahrazuje parametr obecného typu. Skutečný typ je možné explicitně zadat lomené závorky pomocí syntaxe podobné volání funkce šablony. Pokud volána bez parametrů typu, pokusí se kompilátor odvodit skutečný typ z parametry zadané ve volání funkce. Pokud argument určený typu nelze odvodit z použité parametry, kompilátor ohlásí chybu.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje obecné funkce.  
  
```  
// generics_generic_function_1.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
ref struct A {  
   generic <typename ItemType>  
   void G(ItemType) {}  
  
   generic <typename ItemType>  
   static void H(int i) {}  
};  
  
int main() {  
   A myObject;  
  
   // generic function call  
   myObject.G<int>(10);  
  
   // generic function call with type parameters deduced  
   myObject.G(10);  
  
   // static generic function call  
   A::H<int>(10);  
  
   // global generic function call  
   G<int>(10);  
}  
```  
  
 **Příklad**  
  
 Obecné funkce mohou být přetíženy na základě podpis nebo Arita, počet parametry typu na funkci. Obecné funkce také mohou být přetíženy s funkcemi neobecnou se stejným názvem, tak dlouho, dokud se liší v některé parametry typu funkce. Například mohou být přetíženy následující funkce:  
  
```  
// generics_generic_function_2.cpp  
// compile with: /clr /c  
ref struct MyClass {  
   void MyMythod(int i) {}  
  
   generic <class T>   
   void MyMythod(int i) {}  
  
   generic <class T, class V>   
   void MyMythod(int i) {}  
};  
```  
  
 **Příklad**  
  
 Následující příklad používá obecné funkce Najít první prvek v poli. Deklaruje `MyClass`, který dědí ze základní třídy `MyBaseClass`. `MyClass`obsahuje obecné funkci `MyFunction`, která volá jinou funkci Obecné, `MyBaseClassFunction`, v rámci základní třídy. V **hlavní**, obecné funkce `MyFunction`, se nazývá pomocí jiného typu argumentů.  
  
```  
// generics_generic_function_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyBaseClass {  
protected:  
   generic <class ItemType>  
   ItemType MyBaseClassFunction(ItemType item) {  
      return item;  
   }  
};  
  
ref class MyClass: public MyBaseClass {  
public:  
   generic <class ItemType>  
   ItemType MyFunction(ItemType item) {  
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);  
   }  
};  
  
int main() {  
   MyClass^ myObj = gcnew MyClass();  
  
   // Call MyFunction using an int.  
   Console::WriteLine("My function returned an int: {0}",  
                           myObj->MyFunction<int>(2003));  
  
   // Call MyFunction using a string.  
   Console::WriteLine("My function returned a string: {0}",  
   myObj->MyFunction<String^>("Hello generic functions!"));  
}  
```  
  
 **Output**  
  
```Output  
My function returned an int: 2003  
My function returned a string: Hello generic functions!  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)   
 [Obecné typy](../windows/generics-cpp-component-extensions.md)