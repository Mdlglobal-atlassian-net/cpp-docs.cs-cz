---
title: Obecné typy a šablony (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 567286ee24e9df968b2d352489fe12f2735854eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172344"
---
# <a name="generics-and-templates-ccli"></a>Obecné typy a šablony (C++/CLI)

Obecné typy a šablony jsou obě funkce jazyka, které poskytují podporu pro parametrizované typy. Liší se ale a mají odlišná použití. V tomto tématu najdete přehled mnoha rozdílů.

Další informace najdete v tématu [prostředí Windows Runtime a spravované šablony](windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Porovnávání šablon a generických typů

Klíčové rozdíly mezi obecnými a C++ šablonami:

- Obecné typy jsou obecné, dokud nebudou pro ně tyto typy nahrazeny za běhu. Šablony jsou specializované v době kompilace, takže nejsou pořád parametrizované typy za běhu.

- Modul CLR (Common Language Runtime) konkrétně podporuje obecné typy v jazyce MSIL. Vzhledem k tomu, že modul runtime ví o obecných typech, mohou být pro obecné typy nahrazeny konkrétní typy při odkazování na sestavení obsahující obecný typ. Šablony, na rozdíl od, překládat na běžné typy v době kompilace a výsledné typy nemusí být specializované v jiných sestaveních.

- Obecné typy specializované ve dvou různých sestaveních se stejnými argumenty typu jsou stejného typu. Šablony specializované ve dvou různých sestaveních se stejnými argumenty typu jsou posuzovány modulem runtime, aby byly různými typy.

- Obecné typy jsou generovány jako jediná část spustitelného kódu, který se používá pro všechny argumenty typu odkazu (pro typy hodnot, které mají jedinečnou implementaci na typ hodnoty, to není pravda). Kompilátor JIT ví o obecných typech a je schopný optimalizovat kód pro typ odkazu nebo hodnoty, které se používají jako argumenty typu. Šablony generují samostatný kód modulu runtime pro každou specializaci.

- Obecné typy nepovolují parametry šablony bez typu, například `template <int i> C {}`. Šablony je povolují.

- Obecné typy neumožňují explicitní specializaci (tj. vlastní implementaci šablony pro konkrétní typ). Šablony.

- Obecné typy neumožňují částečnou specializaci (vlastní implementace pro podmnožinu argumentů typu). Šablony.

- Obecné typy nepovolují, aby byl parametr typu použit jako základní třída pro obecný typ. Šablony.

- Šablony podporují parametry šablony šablony (například `template<template<class T> class X> class MyClass`), ale obecné typy ne.

## <a name="combining-templates-and-generics"></a>Kombinování šablon a generických typů

Základní rozdíl v obecných typech má důsledky pro sestavování aplikací, které kombinují šablony a obecné typy. Předpokládejme například, že máte třídu šablony, kterou chcete vytvořit obecnou obálku pro k vystavení této šablony pro jiné jazyky jako obecné. Nemůžete mít obecný parametr typu, který je poté předán do šablony, protože šablona musí mít tento parametr typu v době kompilace, ale obecný parametr typu nebude překládat do doby běhu. Vnoření šablony do obecného nebude fungovat buď proto, že neexistuje žádný způsob, jak rozšířit šablony v době kompilace pro libovolné obecné typy, které by mohly být vytvořeny za běhu.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje jednoduchý příklad použití šablon a obecných typů. V tomto příkladu třída šablony předá svůj parametr až do obecného typu. Opačná změna není možná.

Tento idiom může být použit, pokud chcete vytvořit stávající obecné rozhraní API s kódem šablony, který je místní pro sestavení C++/CLI, nebo pokud potřebujete přidat další vrstvu Parametrizace k obecnému typu, aby bylo možné využít některé funkce šablon, které nejsou podporovány obecnými typy.

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

[Obecné typy](generics-cpp-component-extensions.md)
