---
title: nested_exception – třída
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 5741b3aa255f915500f5fe79ab5374c8c86f8814
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460179"
---
# <a name="nestedexception-class"></a>nested_exception – třída

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

### <a name="functions"></a>Funkce

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

Uložená výjimka zachycená tímto `nested_exception` objektem.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Poznámky

Pokud `nested_ptr()` vrátí ukazatel s hodnotou null, funkce volá `std::terminate()`. V opačném případě vyvolá uloženou výjimku zachycenou `*this`.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> výjimky

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Exception – třída](../standard-library/exception-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
