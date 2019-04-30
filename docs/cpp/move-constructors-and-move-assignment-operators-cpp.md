---
title: 'Postupy: Definovat konstruktory přesunutí a operátory přiřazení přesunutí (C++)'
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: b601c53c01940fe110036d569e0be9d43a123a91
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345015"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Konstruktory a operátory přiřazení pro přesunutí (C++)

Toto téma popisuje, jak zapisovat *konstruktor přesunu* a operátor přiřazení přesunu pro třídu jazyka C++. Konstruktor přesunu umožňuje prostředků, které vlastní objektem r-hodnoty k přesunutí do lvalue bez kopírování. Další informace o sémantice pohybu naleznete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Toto téma staví na následující třídě jazyka C++ `MemoryBlock`, která spravuje vyrovnávací paměti.

```cpp
// MemoryBlock.h
#pragma once
#include <iostream>
#include <algorithm>

class MemoryBlock
{
public:

   // Simple constructor that initializes the resource.
   explicit MemoryBlock(size_t length)
      : _length(length)
      , _data(new int[length])
   {
      std::cout << "In MemoryBlock(size_t). length = "
                << _length << "." << std::endl;
   }

   // Destructor.
   ~MemoryBlock()
   {
      std::cout << "In ~MemoryBlock(). length = "
                << _length << ".";

      if (_data != nullptr)
      {
         std::cout << " Deleting resource.";
         // Delete the resource.
         delete[] _data;
      }

      std::cout << std::endl;
   }

   // Copy constructor.
   MemoryBlock(const MemoryBlock& other)
      : _length(other._length)
      , _data(new int[other._length])
   {
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      std::copy(other._data, other._data + _length, _data);
   }

   // Copy assignment operator.
   MemoryBlock& operator=(const MemoryBlock& other)
   {
      std::cout << "In operator=(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      if (this != &other)
      {
         // Free the existing resource.
         delete[] _data;

         _length = other._length;
         _data = new int[_length];
         std::copy(other._data, other._data + _length, _data);
      }
      return *this;
   }

   // Retrieves the length of the data resource.
   size_t Length() const
   {
      return _length;
   }

private:
   size_t _length; // The length of the resource.
   int* _data; // The resource.
};
```

Následující postupy popisují, jak zapsat konstruktor přesunutí a operátor přiřazení přesunu pro vzorovou třídu C++.

### <a name="to-create-a-move-constructor-for-a-c-class"></a>Vytvoření konstruktoru přesunu pro třídu jazyka C++

1. Definujte metodu prázdného konstruktoru, který bere odkaz rvalue na typ třídy jako svůj parametr, jak je ukázáno v následujícím příkladu:

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. V konstruktoru přesunu přiřaďte datové členy třídy ze zdrojového objektu na objekt, který je vytvářen:

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. Přiřaďte datové členy zdrojového objektu na výchozí hodnoty. Tím se destruktoru zabrání uvolnění prostředků (například paměť) více než jednou:

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Vytvoření operátora přiřazení přesunu pro třídu jazyka C++

1. Definujte prázdný operátor přiřazení, který bere odkaz rvalue na typ třídy jako svůj parametr a vrátí odkaz na typ třídy, jak je ukázáno v následujícím příkladu:

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. V operátoru přiřazení přesunu přidejte podmíněný příkaz, který neprovádí operaci, pokud se pokusíte přiřadit objekt sám na sebe.

    ```cpp
    if (this != &other)
    {
    }
    ```

1. V podmíněném příkazu uvolněte veškeré prostředky (například paměť) z objektu, který je přiřazen.

   V následujícím příkladu se uvolní `_data` člena v objektu, který je přiřazen:

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   Postupujte podle kroků 2 a 3 v prvním postupu pro přenos datových členů ze zdrojového objektu na objekt, který je konstruován:

    ```cpp
    // Copy the data pointer and its length from the
    // source object.
    _data = other._data;
    _length = other._length;

    // Release the data pointer from the source object so that
    // the destructor does not free the memory multiple times.
    other._data = nullptr;
    other._length = 0;
    ```

1. Vrátí odkaz na aktuální objekt, jak je znázorněno v následujícím příkladu:

    ```cpp
    return *this;
    ```

## <a name="example"></a>Příklad

Následující příklad ukazuje kompletní konstruktor přesunu a operátor přiřazení přesunu pro `MemoryBlock` třídy:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "
             << other._length << ". Moving resource." << std::endl;

   // Copy the data pointer and its length from the
   // source object.
   _data = other._data;
   _length = other._length;

   // Release the data pointer from the source object so that
   // the destructor does not free the memory multiple times.
   other._data = nullptr;
   other._length = 0;
}

// Move assignment operator.
MemoryBlock& operator=(MemoryBlock&& other)
{
   std::cout << "In operator=(MemoryBlock&&). length = "
             << other._length << "." << std::endl;

   if (this != &other)
   {
      // Free the existing resource.
      delete[] _data;

      // Copy the data pointer and its length from the
      // source object.
      _data = other._data;
      _length = other._length;

      // Release the data pointer from the source object so that
      // the destructor does not free the memory multiple times.
      other._data = nullptr;
      other._length = 0;
   }
   return *this;
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak sémantika přesunu může zlepšit výkon aplikací. Příklad přidá dva prvky do vektorového objektu a pak vloží nový prvek mezi dva existující prvky. `vector` Třída používá sémantiky přesunutí pro efektivní provádění operace vložení přesunutím elementů Vektoru místo jejich kopírování.

```cpp
// rvalue-references-move-semantics.cpp
// compile with: /EHsc
#include "MemoryBlock.h"
#include <vector>

using namespace std;

int main()
{
   // Create a vector object and add a few elements to it.
   vector<MemoryBlock> v;
   v.push_back(MemoryBlock(25));
   v.push_back(MemoryBlock(75));

   // Insert a new element into the second position of the vector.
   v.insert(v.begin() + 1, MemoryBlock(50));
}
```

Tento příklad vytvoří následující výstup:

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In operator=(MemoryBlock&&). length = 75.
In operator=(MemoryBlock&&). length = 50.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Před Visual Studio 2010 tento příklad vytváří následující výstup:

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.
In ~MemoryBlock(). length = 75. Deleting resource.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In operator=(const MemoryBlock&). length = 75. Copying resource.
In operator=(const MemoryBlock&). length = 50. Copying resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Verze v tomto příkladu používá sémantiku přesunutí je mnohem efektivnější než verze, která nepoužívá sémantiku přesunutí, protože vykonává méně kopírování, přidělení paměti a operací zrušení přidělení paměti.

## <a name="robust-programming"></a>Robustní programování

Chcete-li zabránit nedostatku prostředků, vždy uvolněte prostředky (například paměť, popisovače souborů a sokety) v operátoru přiřazení přesunutí.

Chcete-li zabránit neobnovitelnému zničení prostředků, správně zpracovávejte vlastní přiřazení v operátoru přiřazení přesunutí.

Pokud zadáte konstruktor move a operátor přiřazení přesunu pro třídu, můžete vyloučit redundantní kód zápisem konstruktoru přesunutí, aby volání operátoru přiřazení přesunutí. Následující příklad ukazuje přepracovanou verzi konstruktoru přesunu, který volá operátor přiřazení přesunu:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

[Std::move](../standard-library/utility-functions.md#move) funkce zachová vlastnost rvalue *jiných* parametru.

## <a name="see-also"></a>Viz také:

[Deklarátor odkazu r-hodnoty: &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[std::move](../standard-library/utility-functions.md#move)