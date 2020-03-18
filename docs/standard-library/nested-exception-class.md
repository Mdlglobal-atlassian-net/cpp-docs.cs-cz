---
title: nested_exception – třída
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: ed58eb6cc074b54ae6801d2b11089af9a79f8c8f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441614"
---
# <a name="nested_exception-class"></a>nested_exception – třída

Třída popisuje výjimku pro použití s vícenásobnou dědičností. Zachycuje Aktuálně zpracovávanou výjimku a uloží ji pro pozdější použití.

## <a name="syntax"></a>Syntaxe

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_as)||

### <a name="functions"></a>Functions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Vyvolá uloženou výjimku.|
|[nested_ptr](#nested_ptr)|Vrátí uloženou výjimku.|

### <a name="op_as"></a>operátor =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Návratová hodnota

Uložená výjimka zachycená tímto objektem `nested_exception`.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Poznámky

Pokud `nested_ptr()` vrátí ukazatel s hodnotou null, funkce volá `std::terminate()`. V opačném případě vyvolá uloženou výjimku zachycenou `*this`.

## <a name="requirements"></a>Požadavky

**Header:** \<> výjimky

**Obor názvů:** std

## <a name="see-also"></a>Viz také

\ [třídy výjimky](../standard-library/exception-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
