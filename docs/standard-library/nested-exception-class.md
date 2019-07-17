---
title: nested_exception třídy
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: a568a8d9a3817883656406d63c3dd948539bb385
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267910"
---
# <a name="nestedexception-class"></a>nested_exception třídy

Tato třída popisuje výjimku pro použití s vícenásobnou dědičnost. Zaznamenává aktuálně zpracování výjimek a uloží jej pro pozdější použití.

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
|[rethrow_nested](#rethrow_nested)|Vyvolá výjimku uložené.|
|[nested_ptr](#nested_ptr)|Vrátí uložené výjimky.|

### <a name="op_as"></a> operátor =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Návratová hodnota

Uložené výjimky zachycené situace `nested_exception` objektu.

### <a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Poznámky

Pokud `nested_ptr()` vrátí ukazatel s hodnotou null, volání funkce `std::terminate()`. V opačném případě vyvolá uložené výjimka zachycena `*this`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimky >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[exception – třída](../standard-library/exception-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
