---
title: packaged_task – třída
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: e759b1bc8cb47c5c943f29545e3b03ee535f3df7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370668"
---
# <a name="packagedtask-class"></a>packaged_task – třída

Popisuje, *asynchronního poskytovatele* , který je obálka volání signaturou volání `Ty(ArgTypes...)`. Jeho *přidružený asynchronní stav* obsahuje kopii jeho volatelný objekt kromě potenciální výsledek.

## <a name="syntax"></a>Syntaxe

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[packaged_task](#packaged_task)|Vytvoří `packaged_task` objektu.|
|[packaged_task::~packaged_task Destructor](#dtorpackaged_task_destructor)|Odstraní `packaged_task` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejný připojený asynchronní stav.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Volá volatelný objekt, který je uložený v přidruženém asynchronním stavu a atomicky ukládá vrácené hodnoty.|
|[reset](#reset)|Nahradí přidružený asynchronní stav.|
|[swap](#swap)|Vymění přidružený asynchronní stav zadaný objekt.|
|[platný](#valid)|Určuje, zda má objekt přidružený asynchronní stav.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|Přenese přidružený asynchronní stav ze zadaného objektu.|
|[packaged_task::operator()](#op_call)|Volá volatelný objekt, který je uložen v přidruženém asynchronním stavu, atomicky ukládá vrácené hodnoty a nastaví stav *připravené*.|
|[packaged_task::Operator bool](#op_bool)|Určuje, zda má objekt přidružený asynchronní stav.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí >

**Namespace:** std

## <a name="get_future"></a>  packaged_task::get_future –

Vrátí objekt typu `future<Ty>` , který má stejný *přidružený asynchronní stav*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud `packaged_task` objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud tato metoda již byla volána pro `packaged_task` objekt, který má stejný připojený asynchronní stav, vyvolá metoda výjimku `future_error` , který má kód chyby `future_already_retrieved`.

## <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit –

Volá volatelný objekt, který je uložen v *přidružený asynchronní stav* a atomicky ukládá vrácené hodnoty.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Poznámky

Pokud `packaged_task` objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již byly volány pro `packaged_task` objekt, který má stejný připojený asynchronní stav, vyvolá metoda výjimku `future_error` , který má kód chyby `promise_already_satisfied`.

V opačném případě tento operátor volá `INVOKE(fn, args..., Ty)`, kde *fn* je volatelný objekt, který je uložen v přidruženém asynchronním stavu. Žádné vrácené hodnoty se atomicky ukládá jako vrácený výsledek přidružený asynchronní stav.

Rozdíl od [packaged_task:: Operator()](#op_call), není přidružený asynchronní stav nastaven `ready` dokud všechny místní objekty ve volajícím vlákně nejsou zničeny. Vlákna, která jsou blokována v přidruženém asynchronním stavu obvykle nejsou odblokovány, dokud ukončí volající vlákno.

## <a name="op_eq"></a>  packaged_task::Operator =

Převody *přidružený asynchronní stav* ze zadaného objektu.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `packaged_task` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Po provedení této operace *vpravo* již nemá přidružený asynchronní stav.

## <a name="op_call"></a>  packaged_task:: Operator()

Volá volatelný objekt, který je uložen v *přidružený asynchronní stav*atomicky ukládá vrácené hodnoty a nastaví stav *připravené*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Poznámky

Pokud `packaged_task` objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již byly volány pro `packaged_task` objekt, který má stejný připojený asynchronní stav, vyvolá metoda výjimku `future_error` , který má kód chyby `promise_already_satisfied`.

V opačném případě tento operátor volá `INVOKE(fn, args..., Ty)`, kde *fn* je volatelný objekt, který je uložen v přidruženém asynchronním stavu. Některé vrácená hodnota je uložena atomicky jako vrácený výsledek přidružený asynchronní stav a stav je nastaven na hodnotu Připraveno. V důsledku toho budou odblokována veškerá vlákna, která jsou blokována v přidruženém asynchronním stavu.

## <a name="op_bool"></a>  packaged_task::Operator bool

Určuje, zda má objekt `associated asynchronous state`.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekt má přidružený asynchronní stav; v opačném případě **false**.

## <a name="packaged_task"></a>  packaged_task::packaged_task – konstruktor

Vytvoří `packaged_task` objektu.

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `packaged_task` objektu.

*alloc*<br/>
Přidělovač paměti. Další informace najdete v tématu [ \<alokátorů >](../standard-library/allocators-header.md).

*fn*<br/>
Objekt funkce.

### <a name="remarks"></a>Poznámky

První konstruktor zkonstruuje `packaged_task` objekt, který nemá žádné *přidružený asynchronní stav*.

Druhý konstruktor vytvoří `packaged_task` objektu a přenese přidružený asynchronní stav z *vpravo*. Po provedení této operace *vpravo* již nemá přidružený asynchronní stav.

Třetí konstruktor vytvoří `packaged_task` objekt, který obsahuje kopii *fn* uložené v příslušném asynchronním stavu.

Čtvrtý konstruktor vytvoří `packaged_task` objekt, který obsahuje kopii *fn* uložené v příslušném asynchronním stavu a používá `alloc` pro přidělení paměti.

## <a name="dtorpackaged_task_destructor"></a>  packaged_task –:: ~ packaged_task – destruktor

Odstraní `packaged_task` objektu.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Poznámky

Pokud *přidružený asynchronní stav* není *připravené*, úložišť – destruktor [future_error](../standard-library/future-error-class.md) výjimku, která má kód chyby `broken_promise` jako výsledek v přidružený asynchronní stav a veškerá vlákna, která jsou blokována v přidruženém asynchronním stavu budou odblokována.

## <a name="reset"></a>  packaged_task::Reset –

Používá nový *přidružený asynchronní stav* nahradit stávající přidružený asynchronní stav.

```cpp
void reset();
```

### <a name="remarks"></a>Poznámky

V důsledku toho tato metoda se spouští `*this = packaged_task(move(fn))`, kde *fn* je objekt funkce, která je uložena v přidruženém asynchronním stavu pro tento objekt. Proto se vymaže stav objektu, a [get_future](#get_future), [operator()](#op_call), a [make_ready_at_thread_exit](#make_ready_at_thread_exit) lze volat jako na nově vytvořeným objektem.

## <a name="swap"></a>  packaged_task::swap

Vymění přidružený asynchronní stav zadaný objekt.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `packaged_task` objektu.

## <a name="valid"></a>  packaged_task::valid –

Určuje, zda má objekt `associated asynchronous state`.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekt má přidružený asynchronní stav; v opačném případě **false**.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Další >](../standard-library/future.md)<br/>
