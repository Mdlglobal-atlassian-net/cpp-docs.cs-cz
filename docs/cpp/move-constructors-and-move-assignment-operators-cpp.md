---
title: 'Postupy: definování konstruktorů přesunutí a operátorů přiřazení přesunutí (C++)'
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: 2c8fed15787ec4b347694d8c4e40bf7912f3421d
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550768"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Konstruktory a operátory přiřazení pro přesunutí (C++)

Toto téma popisuje, jak napsat *konstruktor přesunu* a operátor přiřazení přesunu pro třídu jazyka C++. Konstruktor přesunu umožňuje přesunout prostředky vlastněné objektem rvalue do hodnoty lvalue bez kopírování. Další informace o tom, jak se sémantika přesunu, najdete v tématu [rvalue reference deklarátor:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

Toto téma se sestavuje na následující třídě jazyka C++, `MemoryBlock` která spravuje vyrovnávací paměť.

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

Následující postupy popisují, jak napsat konstruktor přesunu a operátor přiřazení přesunu pro ukázkovou třídu jazyka C++.

### <a name="to-create-a-move-constructor-for-a-c-class"></a>Vytvoření konstruktoru přesunutí pro třídu C++

1. Definujte prázdnou metodu konstruktoru, která jako svůj parametr převezme odkaz rvalue na typ třídy, jak je znázorněno v následujícím příkladu:

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. V konstruktoru přesunu přiřaďte datové členy třídy ze zdrojového objektu do objektu, který je sestaven:

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. Přiřaďte datové členy zdrojového objektu k výchozím hodnotám. To brání destruktoru v uvolnění prostředků (například paměti) vícekrát:

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Vytvoření operátoru přiřazení přesunutí pro třídu C++

1. Definujte prázdný operátor přiřazení, který převezme odkaz rvalue na typ třídy jako svůj parametr a vrátí odkaz na typ třídy, jak je znázorněno v následujícím příkladu:

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. V operátoru přiřazení přesunutí přidejte podmíněný příkaz, který neprovede žádnou operaci, pokud se pokusíte objekt přiřadit sám sobě.

    ```cpp
    if (this != &other)
    {
    }
    ```

1. V podmíněném příkazu uvolněte veškeré prostředky (například paměť) z objektu, který je přiřazen.

   Následující příklad uvolní `_data` člena z objektu, který je přiřazen k:

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   Postupujte podle kroků 2 a 3 v prvním postupu pro přenos datových členů ze zdrojového objektu do objektu, který je vytvořen:

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

1. Vraťte odkaz na aktuální objekt, jak je znázorněno v následujícím příkladu:

    ```cpp
    return *this;
    ```

## <a name="example"></a>Příklad

Následující příklad ukazuje úplný konstruktor přesunutí a operátor přiřazení přesunutí pro `MemoryBlock` třídu:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other) noexcept
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
MemoryBlock& operator=(MemoryBlock&& other) noexcept
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

Následující příklad ukazuje, jak sémantika přesunutí může zlepšit výkon aplikací. Příklad přidá dva prvky do vektorového objektu a pak vloží nový prvek mezi dva existující prvky. `vector`Třída používá sémantiku přesunutí k efektivnímu provedení operace vložení přesunutím prvků vektoru místo jejich kopírování.

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
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Před Visual Studio 2010 tento příklad vytvořil následující výstup:

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

Verze tohoto příkladu, který používá sémantiku přesunutí, je efektivnější než verze, která nepoužívá sémantiku přesunutí, protože provádí méně operací kopírování, přidělení paměti a zrušení přidělení paměti.

## <a name="robust-programming"></a>Robustní programování

Chcete-li zabránit nevracení prostředků, vždy uvolněte prostředky (například paměť, popisovače souborů a sokety) v operátoru přiřazení přesunutí.

Chcete-li zabránit neodstranitelné zničení prostředků, správně zpracujte samostatné přiřazení v operátoru přiřazení přesunutí.

Pokud poskytnete konstruktor přesunu i operátor přiřazení přesunu pro třídu, můžete eliminovat redundantní kód zápisem konstruktoru Move pro volání operátoru přiřazení přesunutí. Následující příklad ukazuje revidovanou verzi konstruktoru přesunu, která volá operátor přiřazení přesunu:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other) noexcept
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

Funkce [std:: Move](../standard-library/utility-functions.md#move) převede lvalue `other` na rvalue.

## <a name="see-also"></a>Viz také

[Deklarátor odkazu r-hodnoty: &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[std:: Move](../standard-library/utility-functions.md#move)
