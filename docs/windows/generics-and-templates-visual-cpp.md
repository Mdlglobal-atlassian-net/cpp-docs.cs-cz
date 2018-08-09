---
title: Obecné typy a šablony (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fbe4837a347c78bb3b7c05094adf442b69fa2f39
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649488"
---
# <a name="generics-and-templates-visual-c"></a>Obecné typy a šablony (Visual C++)
Obecné typy a šablony jsou obě vlastnosti jazyka, které poskytují podporu pro parametrizované typy. Nicméně se liší a mít různá použití. Toto téma obsahuje přehled o spoustu rozdílů.  
  
 Další informace najdete v tématu [Windows Runtime a spravované šablony](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
## <a name="comparing-templates-and-generics"></a>Porovnání šablony a obecné typy  
 Hlavní rozdíly mezi obecnými typy a šablony C++:  
  
-   Obecné typy jsou obecné, dokud typy jsou nahrazeny pro ně za běhu. Šablony jsou specializované v době kompilace, takže už nejsou stále parametrizované typy za běhu  
  
-   Modul common language runtime konkrétně podporuje obecné typy v jazyce MSIL. Vzhledem k tomu, že modul runtime ví o obecných typů, můžete určité typy nahrazena pro obecné typy při odkazování na sestavení obsahující obecného typu. Šablony, naproti tomu přeložit do běžných typů v době kompilace a výsledné typy nemusí být specializovaná v jiných sestaveních.  
  
-   Obecné typy se specializuje na dvě různá sestavení se stejným typem argumenty jsou stejného typu. Šablony se specializuje na dvě různá sestavení se stejným typem, který argumenty jsou považovány za tímto modulem různých typů.  
  
-   Obecné typy jsou generovány jako jediný spustitelný kód, který se používá pro všechny referenční argumenty typu (to neplatí pro typy hodnot, které mají jedinečné implementace na typ hodnoty). Kompilátor JIT ví o obecných typů a je možné optimalizovat kód pro typy odkazu nebo hodnoty, které se používají jako argumenty typu. Šablony generování kódu samostatný modul runtime pro každou specializaci.  
  
-   Obecné typy nejsou povoleny parametry šablony bez typu, jako například `template <int i> C {}`. Šablony umožňují je.  
  
-   Obecné typy neumožňují explicitní specializace (to znamená, vlastní implementaci šablony pro konkrétní typ). Šablony se provést.  
  
-   Obecné typy neumožňují částečná specializace (vlastní implementaci pro podmnožinu argumentů typu). Šablony se provést.  
  
-   Obecné typy neumožňují parametr typu má být použit jako základní třída pro obecného typu. Šablony se provést.  
  
-   Šablony podporují parametrů šablony – šablonu (například `template<template<class T> class X> class MyClass`), ale nejsou obecné typy.  
  
## <a name="combining-templates-and-generics"></a>Kombinování šablony a obecné typy  
  
Základní rozdíl v obecných typech má vliv na pro vytváření aplikací, které kombinují šablony a obecné typy. Předpokládejme například, že máte třídu šablony, kterou chcete vytvořit obecné obálku pro vystavit Tato šablona do jiných jazyků jako obecný. Obecný zkuste nemůže mít parametr typu, který potom předává na šablonu, protože šablony musí mít tento parametr typu v době kompilace, ale nevyřeší obecného parametru typu do modulu runtime. Vnoření šablony uvnitř obecného nebude fungovat, buď protože neexistuje žádný způsob, jak rozšířit šablony v době kompilace pro libovolného obecné typy, které může být vytvořena v době běhu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje jednoduchý příklad dohromady pomocí šablon a obecné typy. V tomto příkladu třída šablony předá svůj parametr prostřednictvím obecného typu. Opak není možné.  
  
 Tohoto idiomu může použít, když budete chtít vytvořit na existující obecného rozhraní API pomocí šablony kód, který je místní pro sestavení Visual C++, nebo když budete muset přidat další úroveň Parametrizace obecného typu, abyste mohli využívat některé funkce šablony není supporte d podle obecných typů.  
  
### <a name="code"></a>Kód  
  
```cpp  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
```Output  
F  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)