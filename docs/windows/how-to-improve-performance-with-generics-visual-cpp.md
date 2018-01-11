---
title: "Postupy: zlepšení výkonu pomocí obecných typů (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- performance, C++
- Visual C++, performance
- Visual C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d8aad77236e5c1b2cdc8fe5958d87d8c53b8f05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-improve-performance-with-generics-visual-c"></a>Postupy: Zlepšení výkonu pomocí obecných typů (Visual C++)
S obecnými typy můžete vytvořit opakovaně použitelný kód na základě typu parametru. Skutečný typ parametr typu je odložení, dokud není zavolána kódem na straně klienta. Další informace o obecných typů najdete v tématu [obecné typy](../windows/generics-cpp-component-extensions.md).  
  
 Tento článek popisuje jak obecné vám mohou pomoci zvýšit výkon aplikace, která používá kolekce.  
  
## <a name="example"></a>Příklad  
 Rozhraní .NET Framework se dodává s mnoha třídy kolekce v <xref:System.Collections?displayProperty=fullName> oboru názvů. Většina těchto kolekcí, fungovat u objektů typu <xref:System.Object?displayProperty=fullName>. To umožňuje kolekce pro ukládání libovolného typu, protože všechny typy v rozhraní .NET Framework, i typy hodnot, jsou odvozeny od <xref:System.Object?displayProperty=fullName>. Existují však dvě nevýhody tohoto přístupu.  
  
 První Pokud kolekce je ukládání typy hodnot jako celá čísla, hodnota musí být před přidávají do kolekce do pole a nezabalený, pokud je hodnota načteny z kolekce. Toto jsou náročná operace.  
  
 Druhý neexistuje žádný způsob, jak řídit typy, které lze přidat do kolekce. Perfektně právní přidat celé číslo a řetězec ke stejné kolekci, je i v případě, že toto je pravděpodobně není co byla určena. Proto aby váš kód jako typově bezpečný, budete muset zkontrolujte, jestli typ načíst z kolekce skutečně co byl očekáván.  
  
 Následující příklad kódu ukazuje dva hlavní nevýhody před obecné typy kolekcí rozhraní .NET Framework.  
  
```  
// perf_pre_generics.cpp  
// compile with: /clr  
  
using namespace System;  
using namespace System::Collections;  
  
int main()  
{  
    // This Stack can contain any type.  
    Stack ^s = gcnew Stack();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
  
    // Push a String to the same Stack.  
    // The Stack now contains two different data types.  
    s->Push("Seven");  
  
    // Pop the items off the Stack.  
    // The item is returned as an Object, so a cast is  
    // necessary to convert it to its proper type.  
    while (s->Count > 0)  
    {  
        Object ^o = s->Pop();  
        if (o->GetType() == Type::GetType("System.String"))  
        {  
            Console::WriteLine("Popped a String: {0}", (String ^)o);  
        }  
        else if (o->GetType() == Type::GetType("System.Int32"))  
        {  
            Console::WriteLine("Popped an int: {0}", (int)o);  
        }  
        else  
        {  
            Console::WriteLine("Popped an unknown type!");  
        }  
    }  
}  
```  
  
```Output  
Popped a String: Seven  
Popped an int: 7  
```  
  
## <a name="example"></a>Příklad  
 Nové <xref:System.Collections.Generic?displayProperty=fullName> obor názvů obsahuje řadu stejné kolekce v nalezen <xref:System.Collections?displayProperty=fullName> obor názvů, ale bylo upraveno tak, aby přijímal parametry obecného typu. Tím se eliminuje dvě nevýhody neobecnou kolekcí: zabalení a rozbalení typy hodnot a že není možné určit typy k uložení do kolekce. Operace na dvě kolekce jsou identické; liší se pouze v tom, jak jsou vytvořeny instance.  
  
 Porovnání příklad uvedeno výše v tomto příkladu, který používá obecný <xref:System.Collections.Generic.Stack%601> kolekce. V rozsáhlých kolekcí, které se často přistupuje bude výrazně větší než v předchozím příkladu výkon tohoto příkladu.  
  
```  
// perf_post_generics.cpp  
// compile with: /clr  
  
#using <System.dll>  
  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main()  
{  
    // This Stack can only contain integers.  
    Stack<int> ^s = gcnew Stack<int>();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
    s->Push(14);  
  
    // You can no longer push a String to the same Stack.  
    // This will result in compile time error C2664.  
    //s->Push("Seven");  
  
    // Pop an item off the Stack.  
    // The item is returned as the type of the collection, so no  
    // casting is necessary and no unboxing is performed for  
    // value types.  
    int i = s->Pop();  
    Console::WriteLine(i);  
  
    // You can no longer retrieve a String from the Stack.  
    // This will result in compile time error C2440.  
    //String ^str = s->Pop();  
}  
```  
  
```Output  
14  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)