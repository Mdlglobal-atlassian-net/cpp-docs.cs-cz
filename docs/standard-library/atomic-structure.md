---
title: Atomic – struktura | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 298fe2751cf25355e2075a2870c34bf17cedc222
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="atomic-structure"></a>atomic – struktura

Popisuje objekt, který provádí atomické operací na uložené hodnoty typu *Ty*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Členové

|Člen|Popis|
|----------|-----------------|
|**Konstruktor**||
|[atomic](#atomic)|Vytvoří objekt atomic.|
|**Operátory**||
|[Atomic::Operator Ty](#op_ty)|Přečte a vrátí uložené hodnoty. ([Atomic::Load –](#load))|
|[Atomic::Operator =](#op_eq)|Zadaná hodnota se používá k nahrazení uložené hodnoty. ([Atomic::Store –](#store))|
|[Atomic::Operator ++](#op_inc)|Zvýší uložené hodnoty. Používat pouze specializací integrální a ukazatel.|
|[Atomic::Operator +=](#op_add_eq)|Přidá zadanou hodnotu do uložené hodnoty. Používat pouze specializací integrální a ukazatel.|
|[Atomic::Operator--](#op_dec)|Snižuje uložené hodnoty. Používat pouze specializací integrální a ukazatel.|
|[Atomic::Operator-=](#op_sub_eq)|Odečte zadanou hodnotu z uložené hodnoty. Používat pouze specializací integrální a ukazatel.|
|[Atomic::Operator & =](#op_and_eq)|Provede bitové a na zadanou hodnotu a uložené hodnoty. Používat pouze celočíselné specializací.|
|[Atomic::Operator&#124;=](#op_or_eq)|Provede bitové nebo na zadané hodnoty a uložené hodnoty. Používat pouze celočíselné specializací.|
|[Atomic::Operator ^ =](#op_xor_eq)|Provede bitový exkluzivní nebo na zadané hodnoty a uložené hodnoty. Používat pouze celočíselné specializací.|
|**Funkce**||
|[compare_exchange_strong](#compare_exchange_strong)|Provede *atomic_compare_and_exchange* operace na **to** a vrátí výsledek.|
|[compare_exchange_weak](#compare_exchange_weak)|Provede *weak_atomic_compare_and_exchange* operace na **to** a vrátí výsledek.|
|[fetch_add](#fetch_add)|Přidá zadanou hodnotu do uložené hodnoty.|
|[fetch_and](#fetch_and)|Provede bitové a na zadanou hodnotu a uložené hodnoty.|
|[fetch_or](#fetch_or)|Provede bitové nebo na zadané hodnoty a uložené hodnoty.|
|[fetch_sub](#fetch_sub)|Odečte zadanou hodnotu z uložené hodnoty.|
|[fetch_xor](#fetch_xor)|Provede bitový exkluzivní nebo na zadané hodnoty a uložené hodnoty.|
|[is_lock_free](#is_lock_free)|Určuje, zda atomické operací na **to** jsou *zamykání*. Atomickým typem je *zamykání* Pokud žádné atomické operací na daný typ používat zámky.|
|[Zatížení](#load)|Přečte a vrátí uložené hodnoty.|
|[úložiště](#store)|Zadaná hodnota se používá k nahrazení uložené hodnoty.|

## <a name="remarks"></a>Poznámky

Typ *Ty* musí být *trivially kopírovatelná*. To znamená, pomocí [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) pro kopírování jeho bajtů musí vytvořit platný *Ty* objekt, který porovnává stejný jako původní objekt. [Compare_exchange_weak](#compare_exchange_weak) a [compare_exchange_strong](#compare_exchange_strong) členské funkce použití [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) k určení, zda dva *Ty* hodnoty jsou stejné. Tato funkce nebude používat *Ty*-definované **operátor ==**. Členské funkce **atomic** použít **memcpy** ke kopírování hodnoty typu *Ty*.

Částečná specializace ** atomic\<Ty * > **, existuje pro všechny typy ukazatele. Specializace umožňuje přidání posun na hodnotu spravované ukazatel nebo odčítání posun z něj. Aritmetické operace trvat argument typu **ptrdiff_t –** a upravit tento argument na základě velikosti *Ty* být konzistentní s aritmetické běžné adres.

Pro všechny integrální typy s výjimkou existuje specializace **bool**. Každý specializace poskytuje bohatou sadu metody pro atomické aritmetické a logických operací.

||||
|-|-|-|
|**Atomic\<char >**|**Atomic\<podepsané char >**|**Atomic\<nepodepsané char >**|
|**Atomic\<char16_t >**|**Atomic\<char32_t >**|**Atomic\<wchar_t >**|
|**Atomic\<krátké >**|**Atomic\<nepodepsané prostě >**|**Atomic\<int >**|
|**Atomic\<nepodepsané int >**|**Atomic\<dlouho >**|**Atomic\<nepodepsané dlouho >**|
|**Atomic\<dlouho dlouho >**|**Atomic\<nepodepsané dlouho dlouho >**|

Integrální specializací jsou odvozeny od odpovídající **atomic_integral** typy. Například **atomic\<nepodepsané int >** je odvozený od **atomic_uint**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<atomic >

**Namespace:** – std

## <a name="atomic"></a> Atomic::Atomic –

Vytvoří objekt atomic.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Inicializace hodnota.

### <a name="remarks"></a>Poznámky

Atomic objekty se nedá zkopírovat ani přesunout.

Objekty, které jsou instancemi atomic\<*Ty*> lze inicializovat pouze pomocí konstruktor, který přebírá argument typu *Ty* a ne prostřednictvím inicializace agregace. Objekty atomic_integral však můžete inicializovat pouze pomocí inicializace agregace.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> Atomic::Operator *Ty*

Operátor pro typ zadaný v šabloně, atomic\<*Ty*>. Načte hodnotu uloženou v  **\*to**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Poznámky

Tento operátor se vztahuje **memory_order_seq_cst** [memory_order –](atomic-enums.md).

## <a name="op_eq"></a> Atomic::Operator =

Ukládá zadanou hodnotou.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
A *Ty* objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí *hodnotu*.

## <a name="op_inc"></a> Atomic::Operator ++

Zvýší uložené hodnoty. Používat pouze specializací integrální a ukazatel.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první dva operátory zvýšena hodnotu; poslední dva operátory vrátí hodnotu před přírůstku. Operátory použít **memory_order_seq_cst** [memory_order –](atomic-enums.md).

## <a name="op_add_eq"></a> Atomic::Operator +=

Přidá zadanou hodnotu do uložené hodnoty. Používat pouze specializací integrální a ukazatel.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Celočíselný nebo ukazatel hodnota.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt obsahující výsledek přidání.

### <a name="remarks"></a>Poznámky

Tento operátor používá **memory_order_seq_cst** [memory_order –](atomic-enums.md).

## <a name="op_dec"></a> Atomic::Operator--

Snižuje uložené hodnoty. Používat pouze specializací integrální a ukazatel.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první dva operátory odečte hodnotu; poslední dva operátory vrátí hodnotu před snížení. Operátory použít **memory_order_seq_cst** [memory_order –](atomic-enums.md).

## <a name="op_sub_eq"></a> Atomic::Operator-=

Odečte zadanou hodnotu z uložené hodnoty. Používat pouze specializací integrální a ukazatel.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Celočíselný nebo ukazatel hodnota.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt obsahující výsledek odčítání.

### <a name="remarks"></a>Poznámky

Tento operátor používá **memory_order_seq_cst** [memory_order –](atomic-enums.md).

## <a name="op_and_eq"></a> Atomic::Operator & =

Provede bitové a na zadanou hodnotu a uložené hodnotu  **\*to**. Používat pouze celočíselné specializací.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

### <a name="return-value"></a>Návratová hodnota

Výsledek bitové hodnotě a.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci read-modify-write nahradit uložené hodnotu  **\*to** s bitové a z *hodnotu* a aktuální hodnotu, která je uložená v  **\*to**, v rámci omezení **memory_order_seq_cst** [memory_order –](atomic-enums.md).

## <a name="op_or_eq"></a> Atomic::Operator&#124;=

Provede bitové nebo na zadanou hodnotu a uložené hodnotu  **\*to**. Používat pouze celočíselné specializací.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

### <a name="return-value"></a>Návratová hodnota

Výsledek bitové hodnotě nebo.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci read-modify-write nahradit uložené hodnotu  **\*to** s bitové nebo z *hodnotu* a aktuální hodnotu, která je uložená v  **\*to**, v rámci omezení **memory_order_seq_cst** [memory_order –](atomic-enums.md) omezení.

## <a name="op_xor_eq"></a> Atomic::Operator ^ =

Provede bitový exkluzivní nebo na zadanou hodnotu a uložené hodnotu  **\*to**. Používat pouze celočíselné specializací.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

### <a name="return-value"></a>Návratová hodnota

Výsledek bitový exkluzivní nebo.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci read-modify-write nahradit uložené hodnotu  **\*to** s bitový exkluzivní nebo z *hodnotu* a aktuální hodnotu, která je uložená v  **\*to**, v rámci omezení **memory_order_seq_cst** [memory_order –](atomic-enums.md) omezení.

## <a name="compare_exchange_strong"></a> Atomic::compare_exchange_strong –

Provádí atomická operace porovnání a exchange  **\*to**.

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Exp*<br/>
Hodnotu typu *Ty*.

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Order1*<br/>
První **memory_order –** argument.

*Order2*<br/>
Druhý **memory_order –** argument.

### <a name="return-value"></a>Návratová hodnota

A **bool** určující výsledek porovnání hodnoty.

### <a name="remarks"></a>Poznámky

Tato atomické operace porovnání a exchange porovnává hodnotu, která je uložená v  **\*to** s *Exp*. Pokud jsou hodnoty stejné, operace nahradí hodnotu, která je uložená v  **\*to** s *hodnotu* pomocí operace read-modify-write a použitím pořadí omezení paměti, které jsou specifikace *Order1*. Pokud tyto hodnoty nebudou stejné, použije operaci hodnotou, která je uložená v  **\*to** nahradit *Exp* a platí omezení paměti pořadí, které jsou určené *Order2* .

Přetížení, které nemají druhý **memory_order –** použít implicitní *Order2* založený na hodnotu *Order1*. Pokud *Order1* je **memory_order_acq_rel**, *Order2* je **memory_order_acquire**. Pokud *Order1* je **memory_order_release**, *Order2* je **memory_order_relaxed**. Ve všech ostatních případech *Order2* rovná *Order1*.

Pro přetížení, které provést dvě **memory_order –** parametry, hodnota *Order2* nesmí být **memory_order_release** nebo **memory_order_acq_rel**a nesmí být vyšší než hodnota *Order1*.

## <a name="compare_exchange_weak"></a> Atomic::compare_exchange_weak –

Provádí slabé atomické porovnání a exchange operace  **\*to**.

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Exp*<br/>
Hodnotu typu *Ty*.

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Order1*<br/>
První **memory_order –** argument.

*Order2*<br/>
Druhý **memory_order –** argument.

### <a name="return-value"></a>Návratová hodnota

A **bool** určující výsledek porovnání hodnoty.

### <a name="remarks"></a>Poznámky

Tato atomické operace porovnání a exchange porovnává hodnotu, která je uložená v  **\*to** s *Exp*. Pokud jsou hodnoty stejné, operace nahradí hodnotu, která je uložená v  **\*to** s*hodnotu* pomocí operace read-modify-write a použitím pořadí omezení paměti, které jsou specifikace *Order1*. Pokud tyto hodnoty nebudou stejné, použije operaci hodnotou, která je uložená v  **\*to** nahradit *Exp* a platí omezení paměti pořadí, které jsou určené *Order2* .

Porovnávání weak atomic a exchange operace provede exchange, pokud jsou porovnávané hodnoty rovny. Pokud tyto hodnoty nebudou stejné, není zaručeno operaci provést exchange.

Přetížení, které nemají druhý **memory_order –** použít implicitní *Order2* založený na hodnotu *Order1*. Pokud *Order1* je **memory_order_acq_rel**, *Order2* je **memory_order_acquire**. Pokud *Order1* je **memory_order_release**, *Order2* je **memory_order_relaxed**. Ve všech ostatních případech *Order2* rovná *Order1*.

Pro přetížení, které provést dvě **memory_order –** parametry, hodnota *Order2* nesmí být **memory_order_release** nebo **memory_order_acq_rel**a nesmí být vyšší než hodnota *Order1*.

## <a name="exchange"></a> Atomic::Exchange –

Použije zadanou hodnotu k nahrazení uložené hodnotu  **\*to**.

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Pořadí*<br/>
A **memory_order –**.

### <a name="return-value"></a>Návratová hodnota

Uložené hodnoty z  **\*to** před exchange.

### <a name="remarks"></a>Poznámky

Tato operace provede operaci read-modify-write používat *hodnotu* nahradit hodnotou, která je uložená v  **\*to**, v rámci omezení paměti, které jsou určené  *Pořadí*.

## <a name="fetch_add"></a> Atomic::fetch_add –

Načte s hodnotou uloženou v  **\*to**a potom přičte zadanou hodnotu na hodnotu uložené.

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Pořadí*<br/>
A **memory_order –**.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje s hodnotou uloženou v  **\*to** před přidání.

### <a name="remarks"></a>Poznámky

**Fetch_add** metoda provádí operaci read-modify-write atomicky přidat *hodnotu* k hodnotě uložené v  **\*to**a použije paměť omezení, které jsou určené *pořadí*.

## <a name="fetch_and"></a> Atomic::fetch_and –

Provede bitové a na hodnotu a stávající hodnotu, která je uložená v  **\*to**.

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Pořadí*<br/>
A **memory_order –**.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt obsahující výsledek bitové hodnotě a.

### <a name="remarks"></a>Poznámky

**Fetch_and** metoda provádí operaci read-modify-write nahradit uložené hodnotu  **\*to** s bitové a z *hodnotu* a aktuální hodnota, která je uložená v  **\*to**, v rámci omezení paměti, které jsou určené *pořadí*.

## <a name="fetch_or"></a> Atomic::fetch_or –

Provede bitové nebo na hodnotu a stávající hodnotu, která je uložená v  **\*to**.

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Pořadí*<br/>
A **memory_order –**.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt obsahující výsledek bitové hodnotě nebo.

### <a name="remarks"></a>Poznámky

**Fetch_or** metoda provádí operaci read-modify-write nahradit uložené hodnotu  **\*to** s bitové nebo z *hodnotu* a že je aktuální hodnota který je uložený v  **\*to**, v rámci omezení paměti, které jsou určené *pořadí*.

## <a name="fetch_sub"></a> Atomic::fetch_sub –

Odečte zadanou hodnotu z uložené hodnoty.

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Pořadí*<br/>
A **memory_order –**.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt obsahující výsledek odčítání.

### <a name="remarks"></a>Poznámky

**Fetch_sub** metoda provádí operaci read-modify-write má atomicky odečíst *hodnotu* z uložené hodnoty v  **\*to**, v rámci paměť omezení, které jsou určené *pořadí*.

## <a name="fetch_xor"></a> Atomic::fetch_xor –

Provede bitový exkluzivní nebo na hodnotu a stávající hodnotu, která je uložená v  **\*to**.

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnotu typu *Ty*.

*Pořadí*<br/>
A **memory_order –**.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt obsahující výsledek bitový exkluzivní nebo.

### <a name="remarks"></a>Poznámky

**Fetch_xor** metoda provádí operaci read-modify-write nahradit uložené hodnotu  **\*to** s bitový exkluzivní nebo z *hodnotu* a aktuální hodnota, která je uložená v  **\*to**a platí omezení paměti, které jsou určené *pořadí*.

## <a name="is_lock_free"></a> Atomic::is_lock_free –

Určuje, zda atomické operací na  **\*to** jsou zamykání.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud atomické operací na  **\*to** jsou zámku volné, jinak hodnota false.

### <a name="remarks"></a>Poznámky

Atomickým typem je zamykání, pokud žádné atomické operací na daný typ pomocí zámky.

## <a name="load"></a> Atomic::Load –

Načte hodnotu uloženou v  **\*to**, v rámci zadaná paměťová omezení.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parametry

*Pořadí*<br/>
A **memory_order –**. *Pořadí* nesmí být **memory_order_release** nebo **memory_order_acq_rel**.

### <a name="return-value"></a>Návratová hodnota

Načtené hodnoty, které jsou uloženy v  **\*to**.

## <a name="store"></a> Atomic::Store –

Ukládá zadanou hodnotou.

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
A *Ty* objektu.

*Pořadí*<br/>
A **memory_order –** omezení.

### <a name="remarks"></a>Poznámky

Tato funkce člen atomicky ukládá *hodnotu* v `*this`, v rámci omezení paměti, které jsou určené *pořadí*.

## <a name="see-also"></a>Viz také

[\<Atomic >](../standard-library/atomic.md)<br/>
[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
