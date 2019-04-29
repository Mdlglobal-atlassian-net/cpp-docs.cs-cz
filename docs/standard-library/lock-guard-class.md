---
title: lock_guard – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 45a01c5fdd431bcfad1eeb5ab0531c11c89e9767
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413135"
---
# <a name="lockguard-class"></a>lock_guard – třída

Reprezentuje šablonu, která se dá vytvořit instance pro vytvoření objektu, jehož destruktor odemkne `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Poznámky

Argument šablony `Mutex` nutné pojmenovat *typ mutex*.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonymum pro argument šablony `Mutex`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[lock_guard –](#lock_guard)|Vytvoří `lock_guard` objektu.|
|[lock_guard –:: ~ lock_guard – destruktor](#dtorlock_guard_destructor)|Odemkne `mutex` , která byla předána do konstruktoru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="lock_guard"></a>  lock_guard::lock_guard – konstruktor

Vytvoří `lock_guard` objektu.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

*Mtx*<br/>
A *typ mutex* objektu.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt typu `lock_guard` a zámky *Mtx*. Pokud *Mtx* není rekurzivní mutex, musí být odemčený, když tento konstruktor je volán.

Druhý konstruktor nepoužívejte zámky *Mtx*. *Mtx* musí být uzamčen při volání tohoto konstruktoru. Žádné výjimky, vyvolá konstruktor.

## <a name="dtorlock_guard_destructor"></a>  lock_guard –:: ~ lock_guard – destruktor

Odemkne `mutex` , která byla předána do konstruktoru.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Poznámky

Pokud `mutex` neexistuje při spuštění destruktoru, není chování definováno.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
