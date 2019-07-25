---
title: Alokátory
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: cb1b0e0d1466d4af5ba255bdf3d00b11cd921fd6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457544"
---
# <a name="allocators"></a>Alokátory

Přidělování jsou používána C++ standardní knihovnou ke zpracování přidělování a navracení prvků uložených v kontejnerech. Všechny C++ standardní kontejnery knihovny s výjimkou std:: Array mají parametr šablony typu `allocator<Type>`, kde `Type` představuje typ prvku kontejneru. Například Třída Vector je deklarována takto:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

C++ Standardní knihovna poskytuje výchozí implementaci pro přidělování. V jazyce C++ 11 a novějším je výchozí přidělování Aktualizováno pro vystavení menšího rozhraní; nové přidělování se nazývá *minimální přidělování*. Konkrétně `construct()` člen minimálního přidělování podporuje sémantiku přesunutí, což může výrazně zlepšit výkon. Ve většině případů by měl být tento výchozí Alokátor dostačující. V jazyce c++ 11 všechny standardní typy knihoven a funkce, které přijímají parametr typu přidělování, podporují rozhraní minimálního přidělování `std::function`, `shared_ptr, allocate_shared()`včetně, `basic_string`a.  Další informace o výchozím přidělování najdete v tématu [Třída přidělování](../standard-library/allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Zápis vlastního přidělujícího modulu (C++ 11)

Výchozí Alokátor pomocí **New** a **Delete** přiděluje a uvolní paměť. Pokud chcete použít jinou metodu přidělování paměti, jako je například použití sdílené paměti, je nutné vytvořit vlastní přidělování. Pokud cílíte na C++ 11 a potřebujete napsat nový vlastní Alokátor, udělejte mu minimální přidělující, pokud je to možné. I v případě, že jste už implementovali přidělování starého stylu, zvažte jeho úpravu na *minimální přidělování* , aby bylo možné využít `construct()` efektivnější metodu, která bude k dispozici automaticky.

Minimální Alokátor vyžaduje mnohem méně často používaný text a umožňuje zaměřit se na `allocate` členské funkce a `deallocate` , které provedly veškerou práci. Při vytváření minimálního přidělujícího modulu Neimplementujte žádné členy kromě těch, které jsou uvedeny v následujícím příkladu:

1. převádění kopírovacího konstruktoru (viz příklad)

1. operator==

1. operator!=

1. allocate

1. uvolnit

Výchozí `construct()` člen c++ 11, který bude poskytnut pro vás, provede dokonalé přesměrování a umožní sémantiku přesunutí. je mnohem efektivnější v mnoha případech, než je starší verze.

> [!WARNING]
> V době kompilace používá C++ standardní knihovna třídu allocator_traits k detekci členů, které jste výslovně zadali, a poskytuje výchozí implementaci pro všechny členy, kteří nejsou přítomni. Nekoliduje s tímto mechanismem tím, že poskytujete specializaci allocator_traits pro váš Alokátor.

Následující příklad ukazuje minimální implementaci přidělování, který používá `malloc` a. `free` Všimněte si použití nového typu `std::bad_array_new_length` výjimky, který je vyvolána, pokud je velikost pole menší než nula nebo větší než maximální povolená velikost.

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

## <a name="writing-your-own-allocator-c03"></a>Zápis vlastního přidělujícího modulu (C++ 03)

V jazyce C++ 03 musí jakýkoli Alokátor použitý C++ se standardními kontejnery knihovny implementovat následující definice typů:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Kromě toho jakýkoli Alokátor použitý u C++ kontejnerů standardní knihovny musí implementovat následující metody:

|||
|-|-|
|Konstruktor|`deallocate`|
|Kopírovací konstruktor|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Další informace o těchto definicích a metodách typů naleznete v tématu [Třída přidělování](../standard-library/allocator-class.md).

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
