---
title: Alokátorů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d7ae039fefc0137d317a15a803a0bf5d8205c31
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="allocators"></a>Alokátory

Alokátorů používá standardní knihovna C++ pro zpracování přidělení a navrácení elementů uložené v kontejnerech. Všechny standardní knihovna C++ kontejnery s výjimkou std::array mít parametr šablony typu `allocator<Type>`, kde `Type` představuje typ kontejneru elementu. Vector – třída je například deklarovaný následujícím způsobem:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

Standardní knihovna C++ poskytuje výchozí implementaci pro přidělení. C ++ 11 a novější je výchozí přidělení aktualizovat vystavení menší rozhraní; je volána nové přidělení *minimální allocator*. Konkrétně, minimální allocator na `construct()` člen podporuje přesun sémantikou, což může výrazně zlepšit výkon. Ve většině případů tuto výchozí přidělení by mělo být dostatečné. V C ++ 11 všechny standardní knihovna typy a funkce, která trvat přidělení podpora parametr typu minimální allocator rozhraní, včetně `std::function`, `shared_ptr, allocate_shared()`, a `basic_string`.  Další informace o přidělování výchozí najdete v tématu [allocator – třída](../standard-library/allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Psaní vlastních Allocator (C ++ 11)

Používá výchozí přidělení `new` a `delete` alokace a zrušit přidělení paměti. Pokud chcete použít jinou metodu přidělování paměti, například pomocí sdílené paměti, musíte vytvořit vlastní přidělení. Pokud cílíte na C ++ 11 a budete muset napsat nový vlastní allocator, nastavte minimální allocator Pokud je to možné. I v případě, že již byla implementována přidělení starého, zvažte, jestli je potřeba *minimální allocator* aby bylo možné využít výhod více efektivní `construct()` metoda, která bude k dispozici pro vás automaticky.

Minimální allocator vyžaduje mnohem méně často používaný a umožňují zaměřit se na `allocate` a `deallocate` členské funkce, které udělejte všechny práce. Při vytváření minimální allocator, neimplementuje žádné členy s výjimkou těch, které jsou uvedené v následujícím příkladu:

1. Převod kopírovacího konstruktoru (viz příklad)

1. operator==

1. operator!=

1. allocate

1. Zrušit přidělení

C ++ 11 výchozí `construct()` člena, která bude k dispozici pro vás ideální předávání a umožňuje přesunout sémantiku; mnohem je efektivnější v mnoha případech než starší verze.

> [!WARNING]
> Při kompilaci standardní knihovna C++ allocator_traits – třída zjišťuje členy, které jste zadali explicitně a poskytuje výchozí implementaci pro všechny členy, které nejsou k dispozici. Nezpůsobují konflikt s Tento mechanismus tím, že poskytuje specializace allocator_traits pro vaše allocator!

Následující příklad ukazuje na minimální implementace přidělení, který používá `malloc` a `free`. Všimněte si, nový typ výjimky `std::bad_array_new_length` která je vyvolána, pokud je pole velikost je menší než nula nebo větší než maximální povolená velikost.

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>Psaní vlastních Allocator (03 C ++)

V C ++ 03 musí všechny allocator použít s kontejnery standardní knihovna C++ implementovat následující definice typu:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Kromě toho žádné allocator použít s kontejnery standardní knihovna C++ musí implementovat následující metody:

|||
|-|-|
|Konstruktor|`deallocate`|
|Kopírovací konstruktor|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Další informace o těchto definic typů a metod najdete v tématu [allocator – třída](../standard-library/allocator-class.md).

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
