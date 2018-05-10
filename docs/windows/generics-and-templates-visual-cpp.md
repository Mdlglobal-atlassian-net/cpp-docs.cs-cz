---
title: Obecné typy a šablony (Visual C++) | Microsoft Docs
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
ms.openlocfilehash: 5d6dc0a64c5d225f6e80a21dc008e5a2486ad3d9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="generics-and-templates-visual-c"></a>Obecné typy a šablony (Visual C++)
Obecné typy a šablony jsou obě jazykové funkce, které poskytují podporu pro parametrizované typy. Však se liší a mít jiný používá. Toto téma obsahuje přehled mnoho rozdíly.  
  
 Další informace najdete v tématu [prostředí Windows Runtime a spravované šablony](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
## <a name="comparing-templates-and-generics"></a>Porovnání šablony a obecné typy  
 Hlavní rozdíly mezi obecné typy a šablonami C++:  
  
-   Obecné typy jsou obecné, dokud typy jsou nahrazena pro ně za běhu. Šablony se specializují v době kompilace, takže nejsou stále parametrizované typy za běhu  
  
-   Modul common language runtime konkrétně podporuje obecné typy v MSIL. Vzhledem k tomu, že modul runtime ví o obecných typech, můžete konkrétní typy nahrazena pro obecné typy při odkazování na sestavení obsahující obecného typu. Šablony, na rozdíl od vyřešte na běžné typy v době kompilace a výsledný typy nemusí specializuje v ostatních sestavení.  
  
-   Obecné typy specializuje ve dvou různých sestavení se stejným typem argumenty jsou stejného typu. Šablony specializované ve dvou různých sestavení stejného typu, který argumenty jsou považovány za modulem runtime různých typů.  
  
-   Obecné typy jsou generovány jako jediný spustitelný kód, který se používá pro všechny argumenty typu odkazu (to neplatí pro typy hodnot, které mají jedinečné implementace na typ hodnoty). Kompilátor JIT zná obecné typy a bude schopen optimalizovat kód pro hodnotou nebo odkazem typy, které se používají jako argumenty typu. Šablony generování kódu samostatný modul runtime pro každý specializace.  
  
-   Obecné typy neumožňují parametry šablon bez typu, například `template <int i> C {}`. Šablony umožňují je.  
  
-   Obecné typy neumožňují explicitní specializace (to znamená, vlastní implementaci šablony pro konkrétní typ). Šablony udělat.  
  
-   Obecné typy neumožňují částečná specializace (na vlastní implementace pro podmnožinu argumenty typu). Šablony udělat.  
  
-   Obecné typy neumožňují parametr typu, který se má použít jako základní třída pro obecný typ. Šablony udělat.  
  
-   Šablony podporují šablona šablony parametry (například `template<template<class T> class X> class MyClass`), ale nechcete obecné typy.  
  
## <a name="combining-templates-and-generics"></a>Kombinování šablony a obecné typy  
  
-   Základní rozdíl v obecných typech má důsledky pro vytváření aplikací, které spojují šablony a obecné typy. Předpokládejme například, že máte třídu šablony, kterou chcete vytvořit obecné obálku pro dané šablony pro jiné jazyky jako obecný vystavit. Nemůže mít proveďte obecný parametr typu, který potom předává když do šablony, protože šabloně musí mít tento parametr typu v době kompilace, ale obecná nevyřeší parametr typu dokud modulu runtime. Vnoření šablonu uvnitř obecný nebude fungovat, buď protože neexistuje žádný způsob, jak rozšířit šablony v době kompilace pro libovolný obecné typy, které může být vytvořena instance za běhu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje jednoduchý příklad pomocí šablony a obecné typy společně. V tomto příkladu šablony třídy předá její parametr prostřednictvím obecného typu. Naopak není možné.  
  
 Tato stylu může použít, když budete chtít vytvořit na existující obecné rozhraní API pomocí šablony kód, který je místní pro sestavení Visual C++, nebo když budete muset přidat další vrstvu Parametrizace typu Obecné využívat výhod určité funkce šablony není supporte d podle obecných typů.  
  
### <a name="code"></a>Kód  
  
```  
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
  
### <a name="output"></a>Výstup  
  
```  
F  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)