---
title: 'Alokátory: | Dokumentace Microsoftu'
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
ms.openlocfilehash: cc84748e35807ef0f270fe8fbbd7560a9a18e3b2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963492"
---
# <a name="allocators"></a>Alokátory

Alokátory používají standardní knihovny C++ pro zpracování přidělování a navracení zpět prvků uložených v kontejnerech. Všechny kontejnery standardní knihovny C++ s výjimkou std::array mít parametr šablony typu `allocator<Type>`, kde `Type` představuje typ prvku kontejneru. Například třída vektoru je deklarována následovně:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

Standardní knihovny C++ poskytuje výchozí implementaci pro přidělování. V C ++ 11 a novějším výchozího přidělujícího modulu se aktualizuje na vystavení menší rozhraní; nové allocator je volána *minimálních alokátorů*. Zejména minimálních alokátorů `construct()` člen podporuje sémantiku přesunu, což může výrazně zlepšit výkon. Ve většině případů by měla stačit tohoto výchozího přidělujícího modulu. V C ++ 11 standardní knihovny typů a funkcí, které provést všechny alokátoru typu parametru podporu rozhraní minimálních alokátorů včetně `std::function`, `shared_ptr, allocate_shared()`, a `basic_string`.  Další informace o výchozího přidělujícího modulu najdete v tématu [Allocator – třída](../standard-library/allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Psaní vlastního alokátoru (C ++ 11)

Pomocí výchozího přidělujícího modulu **nové** a **odstranit** přidělení a uvolnění paměti. Pokud chcete použít jinou metodu přidělení paměti, jako je třeba použití sdílené paměti, musíte vytvořit vlastní Alokátor. Pokud cílíte na C ++ 11 a budete muset napsat nový vlastní Alokátor, nastavte ji minimálních alokátorů. Pokud je to možné. I v případě, že už jste implementovali alokátoru starého typu, zvažte úpravu to přijde *minimálních alokátorů* abyste mohli využívat mnohem efektivnější `construct()` metodu, která vám poskytneme vám automaticky.

Minimálních alokátorů vyžaduje mnohem méně často používaný text a umožní vám zaměřit se na `allocate` a `deallocate` členské funkce, které všechnu práci udělat. Při vytváření minimálních alokátorů, neimplementuje žádné členy s výjimkou těch, které je znázorněno v následujícím příkladu:

1. Převod kopírovacího konstruktoru (viz příklad)

1. operator==

1. operator!=

1. allocate

1. zrušit přidělení

C ++ 11 výchozí `construct()` člena, který vám poskytneme vám perfektní přesměrování a umožňuje sémantiky přesunutí; je v mnoha případech mnohem efektivnější než starší verze.

> [!WARNING]
> V době kompilace standardní knihovny C++ používá třídu allocator_traits zjistit členy, které jste explicitně zadali a poskytuje výchozí implementaci členů, které nejsou k dispozici. Nejsou v konfliktu s Tento mechanismus poskytnutím specializací allocator_traits – pro vašeho allocator!

Následující příklad ukazuje minimální implementaci alokátoru, který používá `malloc` a `free`. Všimněte si použití nový typ výjimky `std::bad_array_new_length` která je vyvolána, pokud je velikost pole menší než nula nebo větší než maximální povolená velikost.

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

## <a name="writing-your-own-allocator-c03"></a>Psaní vlastního alokátoru (C ++ 03)

V C ++ 03 musí implementovat všechny Alokátor použitý s kontejnery standardní knihovny C++ následující definice typu:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Kromě toho všechny Alokátor použitý s kontejnery standardní knihovny C++ musí používat následující metody:

|||
|-|-|
|Konstruktor|`deallocate`|
|Kopírovací konstruktor|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Další informace o těchto definic typů a metod najdete v tématu [Allocator – třída](../standard-library/allocator-class.md).

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
