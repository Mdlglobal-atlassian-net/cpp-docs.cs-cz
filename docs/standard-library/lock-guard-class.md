---
title: lock_guard – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351716"
---
# <a name="lock_guard-class"></a>lock_guard – třída

Představuje šablonu, která může být vytvořena instance k vytvoření objektu, jehož destruktor odemkne `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Poznámky

Argument `Mutex` šablony musí pojmenovat *typ mutex*.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonymum pro `Mutex`argument šablony .|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[lock_guard](#lock_guard)|Vytvoří `lock_guard` objekt.|
|[lock_guard::~lock_guard Destruktor](#dtorlock_guard_destructor)|`mutex` Odemkne, který byl předán konstruktoru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> mutex

**Obor názvů:** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>lock_guard::lock_guard konstruktor

Vytvoří `lock_guard` objekt.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

*Mtx*\
Objekt *typu mutex.*

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt typu `lock_guard` a uzamkne *Mtx*. Pokud *Mtx* není rekurzivní mutex, musí být odemknut, když je volán tento konstruktor.

Druhý konstruktor nezamyká *Mtx*. *Mtx* musí být uzamčen, když je volán tento konstruktor. Konstruktor nevyvolá žádné výjimky.

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard::~lock_guard Destruktor

`mutex` Odemkne, který byl předán konstruktoru.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Poznámky

`mutex` Pokud neexistuje při spuštění destruktoru, chování není definováno.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
