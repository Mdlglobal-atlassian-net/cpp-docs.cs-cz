---
title: unique_lock – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 784969bea25bfff49a21c23b350afbfc8bdab59a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383513"
---
# <a name="uniquelock-class"></a>unique_lock – třída

Reprezentuje šablonu, která se dá vytvořit instance vytvořit objekty, které spravují zamykání a odemykání `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Poznámky

Argument šablony `Mutex` nutné pojmenovat *typ mutex*.

Interně `unique_lock` uchovává ukazatel na přidruženou `mutex` objektu a **bool** , která označuje, zda vlastní aktuální vlákno `mutex`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`mutex_type`|Synonymum pro argument šablony `Mutex`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[unique_lock –](#unique_lock)|Vytvoří `unique_lock` objektu.|
|[~unique_lock Destructor](#dtorunique_lock_destructor)|Uvolní všechny prostředky, které jsou přidružené k `unique_lock` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví přidruženého `mutex`.|
|[mutex](#mutex)|Získá uložený ukazatel na přidruženou `mutex`.|
|[owns_lock](#owns_lock)|Určuje, zda volající vlákno vlastní přidružené `mutex`.|
|[Vydání verze](#release)|Zruší přidružení `unique_lock` objekt z přidruženého `mutex` objektu.|
|[swap](#swap)|Zamění přidruženého `mutex` a stav vlastnictví zadaný objekt.|
|[try_lock](#try_lock)|Pokusy o získání vlastnictví přidruženého `mutex` bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusy o získání vlastnictví přidruženého `mutex` bez blokování.|
|[try_lock_until](#try_lock_until)|Pokusy o získání vlastnictví přidruženého `mutex` bez blokování.|
|[unlock](#unlock)|Uvolní vlastnictví objektu přidruženého `mutex`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[bool – operátor](#op_bool)|Určuje, jestli má volající vlákno vlastnictví přidruženého `mutex`.|
|[operátor =](#op_eq)|Zkopíruje uloženou `mutex` ukazatele a přidružené vlastnictví stav ze zadaného objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

*unique_lock –*<br/>

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="lock"></a>  Zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví přidruženého `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud uloženou `mutex` ukazatel hodnotu NULL, tato metoda vyvolá [system_error](../standard-library/system-error-class.md) , který má kód chyby `operation_not_permitted`.

Pokud volající vlákno již vlastní přidružené `mutex`, tato metoda vyvolá `system_error` , který má kód chyby `resource_deadlock_would_occur`.

Jinak tato metoda volá `lock` přidruženého `mutex` a nastaví příznak vlastnictví interní vlákna **true**.

## <a name="mutex"></a>  objekt mutex

Získá uložený ukazatel na přidruženou `mutex`.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>  bool – operátor

Určuje, jestli má volající vlákno vlastnictví přidružené vzájemně vyloučený přístup.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vlákno vlastní mutex; v opačném případě **false**.

## <a name="op_eq"></a>  operátor =

Zkopíruje uloženou `mutex` ukazatele a přidružené vlastnictví stav ze zadaného objektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
A `unique_lock` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pokud volající vlákno vlastní dříve přidružené `mutex`, než tato metoda volá `unlock` na `mutex`, přiřadí nové hodnoty.

Po zkopírování, tato metoda nastaví *jiných* do stavu vytvořené s výchozím nastavením.

## <a name="owns_lock"></a>  owns_lock

Určuje, zda volající vlákno vlastní přidružené `mutex`.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vlastní vlákno `mutex`; v opačném případě **false**.

## <a name="release"></a>  Vydání verze

Zruší přidružení `unique_lock` objekt z přidruženého `mutex` objektu.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnotu uloženou `mutex` ukazatele.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví hodnotu uloženou `mutex` ukazatel na 0 a nastaví vnitřní `mutex` vlastnictví příznak **false**.

## <a name="swap"></a>  Prohození

Zamění přidruženého `mutex` a stav vlastnictví zadaný objekt.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
A `unique_lock` objektu.

## <a name="try_lock"></a>  try_lock –

Pokusy o získání vlastnictví přidruženého `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud uloženou `mutex` ukazatel hodnotu NULL, vyvolá metoda výjimku [system_error](../standard-library/system-error-class.md) , který má kód chyby `operation_not_permitted`.

Pokud volající vlákno již vlastní `mutex`, vyvolá metoda výjimku `system_error` , který má kód chyby `resource_deadlock_would_occur`.

## <a name="try_lock_for"></a>  try_lock_for –

Pokusy o získání vlastnictví přidruženého `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud uloženou `mutex` ukazatel hodnotu NULL, vyvolá metoda výjimku [system_error](../standard-library/system-error-class.md) , který má kód chyby `operation_not_permitted`.

Pokud volající vlákno již vlastní `mutex`, vyvolá metoda výjimku `system_error` , který má kód chyby `resource_deadlock_would_occur`.

## <a name="try_lock_until"></a>  try_lock_until

Pokusy o získání vlastnictví přidruženého `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
Bod v čase, který určuje mezní hodnotu, po jejímž uplynutí metody se již nebude pokoušet o získání vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud uloženou `mutex` ukazatel hodnotu NULL, vyvolá metoda výjimku [system_error](../standard-library/system-error-class.md) , který má kód chyby `operation_not_permitted`.

Pokud volající vlákno již vlastní `mutex`, vyvolá metoda výjimku `system_error` , který má kód chyby `resource_deadlock_would_occur`.

## <a name="unique_lock"></a>  unique_lock – konstruktor

Vytvoří `unique_lock` objektu.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>Parametry

*Mtx*<br/>
Typ objektu mutex.

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.

*Abs_time*<br/>
Bod v čase, který určuje mezní hodnotu, po jejímž uplynutí metody se již nebude pokoušet o získání vlastnictví `mutex`.

*Jiné*<br/>
A `unique_lock` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, který má hodnotu ukazatele přidružené mutex 0.

Druhý konstruktor přesune stav přidružený vzájemně vyloučený přístup z *jiných*. Po přesunutí *jiných* už nejsou přidružené mutex.

Zbývající úložiště konstruktory & *Mtx* jako uloženou `mutex` ukazatele. Vlastnictví `mutex` se určuje podle druhý argument, pokud existuje.

|||
|-|-|
|`No argument`|Vlastnictví je získán voláním `lock` metoda přidruženého `mutex` objektu.|
|`Adopt`|Předpokládá se vlastnictví. `Mtx` musí být uzamčen při volání konstruktoru.|
|`Defer`|Volající vlákno není považováno za vlastní `mutex` objektu. `Mtx` nesmí být uzamčen při volání konstruktoru.|
|`Try`|Vlastnictví je určena voláním `try_lock` přidruženého `mutex` objektu. Konstruktoru nevyvolá žádnou akci.|
|`Rel_time`|Vlastnictví je určena voláním `try_lock_for(Rel_time)`.|
|`Abs_time`|Vlastnictví je určena voláním `try_lock_until(Abs_time)`.|

## <a name="dtorunique_lock_destructor"></a>  ~ unique_lock – destruktor

Uvolní všechny prostředky, které jsou přidružené k `unique_lock` objektu.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno vlastní přidružené `mutex`, vlastnictví verze destruktor voláním odemknout v `mutex` objektu.

## <a name="unlock"></a>  Odemknutí

Uvolní vlastnictví objektu přidruženého `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní přidruženého `mutex`, tato metoda vyvolá [system_error](../standard-library/system-error-class.md) , který má kód chyby `operation_not_permitted`.

Jinak tato metoda volá `unlock` přidruženého `mutex` a nastaví příznak vlastnictví interní vlákna **false**.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
