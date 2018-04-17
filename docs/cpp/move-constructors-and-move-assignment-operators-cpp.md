---
title: 'Postupy: definování přesunutí konstruktory a operátory přiřazení pro přesunutí (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bc9ce3d397b96ec45a0dbee5fefdb09d01b3f28
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Konstruktory a operátory přiřazení pro přesunutí (C++)
Toto téma popisuje, jak napsat *přesunout konstruktor* a operátor move přiřazení pro třídu C++. Konstruktor move umožňuje prostředků, které vlastní objekt rvalue se přesune do lvalue bez kopírování. Další informace o přesunutí sémantiku najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 Toto téma staví na následující třídy C++ `MemoryBlock`, který spravuje vyrovnávací paměti.  
  
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
  
 Následující postupy popisují, jak napsat konstruktor move a operátor move přiřazení například třídami C++.  
  
### <a name="to-create-a-move-constructor-for-a-c-class"></a>Chcete-li vytvořit konstruktor move pro třídu C++  
  
1.  Metodu prázdný konstruktor, která přebírá rvalue odkaz na typ třídy jako jeho parametr definujte, jak je ukázáno v následujícím příkladu:  
  
    ```cpp  
    MemoryBlock(MemoryBlock&& other)  
       : _data(nullptr)  
       , _length(0)  
    {  
    }  
    ```  
  
2.  V konstruktor move přiřadíte členy třídy dat ze zdrojového objektu k objektu, který je vytvářen:  
  
    ```cpp  
    _data = other._data;  
    _length = other._length;  
    ```  
  
3.  Datové členy zdrojového objektu přiřadíte výchozí hodnoty. To brání destruktoru uvolnění prostředků (např. paměti) vícekrát:  
  
    ```cpp  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Chcete-li vytvořit operátor přiřazení přesunutí pro třídu C++  

1.  Operátor přiřazení prázdný, který přebírá rvalue odkaz na typ třídy jako jeho parametr a vrátí odkaz na typ třídy definujte, jak je ukázáno v následujícím příkladu:  
  
    ```cpp  
    MemoryBlock& operator=(MemoryBlock&& other)  
    {  
    }  
    ```  
  
2.  Operátor přiřazení přesunutí přidejte podmíněného příkaz, který provádí žádná operace, pokud se pokusíte přiřaďte objekt na sebe sama.  
  
    ```cpp  
    if (this != &other)  
    {  
    }  
    ```  
  
3.  V příkazu podmíněného bez objekt, který je přiřazen k žádné prostředky (např. paměti).  
  
     Následující příklad uvolní `_data` člena z objektu, který je právě přiřazován na:  
  
    ```cpp  
    // Free the existing resource.  
    delete[] _data;  
    ```  
  
     Postupujte podle kroků 2 a 3 v prvním postupu pro přenos datových členů ze zdrojového objektu k objektu, který je vytvářen:  
  
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
  
4.  Vrátí odkaz na aktuální objekt, jak je znázorněno v následujícím příkladu:  
  
    ```cpp  
    return *this;  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kompletní přesunout konstruktor a operátor move assignment pro `MemoryBlock` třídy:  
  
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
 Následující příklad ukazuje, jak přesunout sémantiku může zlepšit výkon aplikací. V příkladu přidá dva elementy do objektu vector a vloží nového elementu mezi dvěma stávající elementy. `vector` Používá třída přesunout sémantiku k provedení operace vložení efektivně přesunutím elementy vektoru namísto kopírování je.  
  
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
  
```  
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
  
 Tento příklad před Visual Studio 2010, vytváří následující výstup:  
  
```  
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
  
 Verze tohoto příkladu, používá přesouvat sémantiku je efektivnější než verze, která nepoužívá přesunout sémantiku, protože vykonává méně copy, přidělení paměti a operace zrušení přidělení paměti.  
  
## <a name="robust-programming"></a>Robustní programování  
 Aby nedostatku prostředků vždy uvolněte prostředky (například paměť, obslužné rutiny souborů a sockets) v operátor přiřazení move.  
  
 Aby se zabránilo neopravitelné odstranění prostředků, řádně zpracovávejte vlastní přiřazení v operátor přiřazení move.  
  
 Pokud zadáte konstruktor move a operátor přiřazení přesunutí pro třídu, můžete eliminovat redundantní kód napsáním konstruktor move volat operátor přiřazení move. Následující příklad ukazuje upravenou verzi přesunutí konstruktor, který volá operátor move přiřazení:  
  
```  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   *this = std::move(other);  
}  
```  
  
 [Std::move](../standard-library/utility-functions.md#move) funkce uchovává vlastnost rvalue `other` parametr.  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor odkazu rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md)   
 [\<nástroj > přesunout](http://msdn.microsoft.com/en-us/abef7e85-9dd6-4724-85da-d7f7fe95dca9)