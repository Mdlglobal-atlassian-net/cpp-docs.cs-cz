---
title: lock_guard – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b36567eb9767d65847da8e6492ffd817322b458
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lockguard-class"></a>lock_guard – třída

Reprezentuje šablonu, která může být vytvořena instance pro vytvoření objektu jejichž destruktor odemkne `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Poznámky

Argument šablony `Mutex` třeba zadat název *mutex typu*.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné – definice TypeDef

|Název|Popis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonymum argumentu šablony `Mutex`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[lock_guard](#lock_guard)|Vytvoří `lock_guard` objektu.|
|[lock_guard:: ~ lock_guard – destruktor](#dtorlock_guard_destructor)|Odemkne `mutex` byl předaný konstruktoru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mutex >

**Namespace:** – std

## <a name="lock_guard"></a>  lock_guard::lock_guard – konstruktor

Vytvoří `lock_guard` objektu.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

`Mtx` A *mutex typ* objektu.

### <a name="remarks"></a>Poznámky

První konstruktoru vytvoří objekt typu `lock_guard` a zámky `Mtx`. Pokud `Mtx` není rekurzivní mutex, musí ho odemknout, když je volána tento konstruktor.

Druhý konstruktor nezamyká `Mtx`. `Mtx` je nutné uzamknout, když je volána tento konstruktor. Konstruktor, vyvolá žádné výjimky.

## <a name="dtorlock_guard_destructor"></a>  lock_guard:: ~ lock_guard – destruktor

Odemkne `mutex` byl předaný konstruktoru.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Poznámky

Pokud `mutex` neexistuje spuštění destruktoru chování není definován.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex >](../standard-library/mutex.md)<br/>
