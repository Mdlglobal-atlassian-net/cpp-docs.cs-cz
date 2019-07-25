---
title: lock_guard – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: f59860c3aaa9ef7458fe5e30b85b119dede52c72
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453847"
---
# <a name="lockguard-class"></a>lock_guard – třída

Představuje šablonu, která může být vytvořena pro vytvoření objektu, jehož destruktor odemkne `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Poznámky

Argument `Mutex` šablony musí pojmenovat *typ mutex*.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonymum pro argument `Mutex`šablony|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[lock_guard](#lock_guard)|`lock_guard` Vytvoří objekt.|
|[lock_guard:: ~ lock_guard – destruktor](#dtorlock_guard_destructor)|Odemkne `mutex` , která byla předána konstruktoru.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="lock_guard"></a>lock_guard:: lock_guard – konstruktor

`lock_guard` Vytvoří objekt.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

*MTX*\
Objekt *typu mutex* .

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt typu `lock_guard` a zamkne *MTX*. Pokud *MTX* není rekurzivní mutex, musí být odemčen při volání tohoto konstruktoru.

Druhý konstruktor nezamkne *MTX*. *MTX* musí být při volání tohoto konstruktoru uzamčena. Konstruktor nevyvolává žádné výjimky.

## <a name="dtorlock_guard_destructor"></a>lock_guard:: ~ lock_guard – destruktor

Odemkne `mutex` , která byla předána konstruktoru.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Poznámky

`mutex` Pokud při spuštění destruktoru neexistuje, chování není definováno.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
