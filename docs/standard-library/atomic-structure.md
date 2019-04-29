---
title: atomic – struktura
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 258812f033d34f040d96847581d6f51692a933b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376666"
---
# <a name="atomic-structure"></a>atomic – struktura

Popisuje objekt, který provádí atomické operace na uložené hodnotě typu *Ty*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Členové

|Člen|Popis|
|----------|-----------------|
|**Konstruktor**||
|[atomic](#atomic)|Sestaví Atomický objekt.|
|**Operátory**||
|[Atomic::Operator Ty](#op_ty)|Přečte a vrátí uloženou hodnotu. ([Atomic::Load –](#load))|
|[Atomic::Operator =](#op_eq)|Používá zadanou hodnotu k nahrazení uložené hodnoty. ([Atomic::Store –](#store))|
|[Atomic::Operator ++](#op_inc)|Zvýší uloženou hodnotu. Používá se pouze specializacemi integrálu a ukazatele.|
|[Atomic::Operator +=](#op_add_eq)|Přidá zadanou hodnotu k uložené hodnotě. Používá se pouze specializacemi integrálu a ukazatele.|
|[atomic::operator--](#op_dec)|Sníží uloženou hodnotu. Používá se pouze specializacemi integrálu a ukazatele.|
|[Atomic::Operator-=](#op_sub_eq)|Odečte zadanou hodnotu od uložené hodnoty. Používá se pouze specializacemi integrálu a ukazatele.|
|[Atomic::Operator & =](#op_and_eq)|Provádí logické bitové a na zadanou hodnotu a uloženou hodnotu. Používá se pouze specializacemi integrálu.|
|[atomic::operator&#124;=](#op_or_eq)|Provádí logické bitové nebo na zadanou hodnotu a uloženou hodnotu. Používá se pouze specializacemi integrálu.|
|[Atomic::Operator ^ =](#op_xor_eq)|Provádí bitový exkluzivní nebo na zadanou hodnotu a uloženou hodnotu. Používá se pouze specializacemi integrálu.|
|**Funkce**||
|[compare_exchange_strong](#compare_exchange_strong)|Provádí *atomic_compare_and_exchange* operace **to** a vrátí výsledek.|
|[compare_exchange_weak](#compare_exchange_weak)|Provádí *weak_atomic_compare_and_exchange* operace **to** a vrátí výsledek.|
|[fetch_add](#fetch_add)|Přidá zadanou hodnotu k uložené hodnotě.|
|[fetch_and](#fetch_and)|Provádí logické bitové a na zadanou hodnotu a uloženou hodnotu.|
|[fetch_or](#fetch_or)|Provádí logické bitové nebo na zadanou hodnotu a uloženou hodnotu.|
|[fetch_sub](#fetch_sub)|Odečte zadanou hodnotu od uložené hodnoty.|
|[fetch_xor](#fetch_xor)|Provádí bitový exkluzivní nebo na zadanou hodnotu a uloženou hodnotu.|
|[is_lock_free](#is_lock_free)|Určuje, zda atomické operace na **to** jsou *bez zámku*. Atomický typ je *bez zámku* Pokud žádné atomické operace na daném typu nepoužívají zámky.|
|[Zatížení](#load)|Přečte a vrátí uloženou hodnotu.|
|[store](#store)|Používá zadanou hodnotu k nahrazení uložené hodnoty.|

## <a name="remarks"></a>Poznámky

Typ *Ty* musí být *triviálně kopírovatelné*. To znamená, že použití [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) ke kopírování jeho bajtů musí vytvořit platný *Ty* objekt, který porovnání roven původnímu objektu. [Compare_exchange_weak](#compare_exchange_weak) a [compare_exchange_strong](#compare_exchange_strong) členské funkce pomocí [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) k určení, zda dva *Ty* hodnoty jsou si rovny. Tyto funkce nepoužijí *Ty*-definované `operator==`. Členské funkce `atomic` použít `memcpy` ke kopírování hodnot typu *Ty*.

Částečná specializace **atomické\<Ty \* >** , existuje pro všechny typy ukazatelů. Specializace umožňuje přidání posunu k hodnotě spravovaného ukazatele nebo odečtení posunu od něj. Aritmetické operace přijímají argument typu `ptrdiff_t` a upravují tento argument v závislosti na velikosti *Ty* pro zajištění konzistence s běžnou aritmetikou adres.

Specializace existuje pro každý integrální typ kromě **bool**. Jednotlivé specializace poskytují bohatou sadu metod pro atomické aritmetické a logické operace.

||||
|-|-|-|
|**Atomic\<char >**|**Atomic\<podepsané char >**|**Atomic\<unsigned char >**|
|**atomic\<char16_t>**|**atomic\<char32_t>**|**atomic\<wchar_t>**|
|**atomic\<short>**|**Atomic\<unsigned short >**|**atomic\<int>**|
|**Atomic\<unsigned int >**|**Atomic\<dlouhé >**|**Atomic\<unsigned long >**|
|**Atomic\<long long >**|**Atomic\<unsigned long long. >**|

Integrální specializace jsou odvozeny z odpovídajících `atomic_integral` typy. Například **atomické\<unsigned int >** je odvozen z `atomic_uint`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<atomické >

**Namespace:** std

## <a name="atomic"></a> Atomic::Atomic –

Sestaví Atomický objekt.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Hodnota inicializace.

### <a name="remarks"></a>Poznámky

Atomické objekty nelze kopírovat nebo přesunout.

Objekty, které jsou instancemi atomic\<*Ty*> může být inicializovány pouze pomocí konstruktoru, který přebírá argument typu *Ty* a nikoli pomocí agregační inicializace. Objekty atomic_integral však mohou být inicializovány pouze pomocí agregační inicializace.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> Atomic::Operator *Ty*

Operátor pro typ určený k šabloně atomic\<*Ty*>. Načte uloženou hodnotu do  **\*to**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Poznámky

Tento operátor se vztahuje `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a> Atomic::Operator =

Uloží zadanou hodnotu.

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

Vrátí *hodnota*.

## <a name="op_inc"></a> Atomic::Operator ++

Zvýší uloženou hodnotu. Používá se pouze specializacemi integrálu a ukazatele.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

První dva operátory vrací hodnotu parametru zvýšena. poslední dva operátory vrací hodnotu před inkrementací. Použijte operátory `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a> Atomic::Operator +=

Přidá zadanou hodnotu k uložené hodnotě. Používá se pouze specializacemi integrálu a ukazatele.

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
Hodnota typu celé číslo nebo ukazatel.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje výsledek součtu.

### <a name="remarks"></a>Poznámky

Tento operátor se používá `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a> Atomic::Operator--

Sníží uloženou hodnotu. Používá se pouze specializacemi integrálu a ukazatele.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

První dva operátory vrací hodnotu snížen; poslední dva operátory vrací hodnotu před snížení. Použijte operátory `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a> Atomic::Operator-=

Odečte zadanou hodnotu od uložené hodnoty. Používá se pouze specializacemi integrálu a ukazatele.

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
Hodnota typu celé číslo nebo ukazatel.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje výsledek odčítání.

### <a name="remarks"></a>Poznámky

Tento operátor se používá `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a> Atomic::Operator & =

Provádí logické bitové a na zadanou hodnotu a uloženou hodnotu  **\*to**. Používá se pouze specializacemi integrálu.

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

Výsledek bitového a.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci čtení modify-write k nahrazení uložené hodnoty  **\*to** logickou bitovou hodnotou a z *hodnotu* a aktuální hodnotou, která je uložena v  **\*to**, v rámci omezení `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a> Atomic::Operator&#124;=

Provádí logické bitové nebo na zadanou hodnotu a uloženou hodnotu  **\*to**. Používá se pouze specializacemi integrálu.

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

Výsledek bitového nebo.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci čtení modify-write k nahrazení uložené hodnoty  **\*to** logickou bitovou hodnotou nebo z *hodnotu* a aktuální hodnotou, která je uložena v  **\*to**, v rámci omezení `memory_order_seq_cst` [memory_order](atomic-enums.md) omezení.

## <a name="op_xor_eq"></a> Atomic::Operator ^ =

Provádí bitový exkluzivní nebo na zadanou hodnotu a uloženou hodnotu  **\*to**. Používá se pouze specializacemi integrálu.

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

Tento operátor provádí operaci čtení modify-write k nahrazení uložené hodnoty  **\*to** s bitový exkluzivní nebo *hodnotu* a aktuální hodnotou, která je uložena v  **\*to**, v rámci omezení `memory_order_seq_cst` [memory_order](atomic-enums.md) omezení.

## <a name="compare_exchange_strong"></a> Atomic::compare_exchange_strong –

Provádí operaci atomické porovnání a záměna  **\*to**.

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
První `memory_order` argument.

*Order2*<br/>
Druhý `memory_order` argument.

### <a name="return-value"></a>Návratová hodnota

A **bool** označuje výsledek porovnání hodnoty.

### <a name="remarks"></a>Poznámky

Operaci atomické porovnání a záměna porovnává hodnotu uloženou v  **\*to** s *Exp*. Pokud jsou hodnoty stejné, operace nahradí hodnotu, která je uložena v  **\*to** s *hodnotu* pomocí operace čtení modify-write a použitím omezení pořadí paměti, které jsou určená *Order1*. Pokud nejsou hodnoty stejné, operace použije hodnotu uloženou v  **\*to** nahradit *Exp* a použije omezení pořadí paměti, která jsou určena podle *Order2* .

Přetížení, která nemají druhý `memory_order` použít implicitní *Order2* , která je založena na hodnotě *Order1*. Pokud *Order1* je `memory_order_acq_rel`, *Order2* je `memory_order_acquire`. Pokud *Order1* je `memory_order_release`, *Order2* je `memory_order_relaxed`. Ve všech ostatních případech *Order2* rovná *Order1*.

Pro přetížení, která berou dva `memory_order` parametry, hodnota *Order2* nesmí být `memory_order_release` nebo `memory_order_acq_rel`a nesmí být silnější než hodnota *Order1*.

## <a name="compare_exchange_weak"></a> Atomic::compare_exchange_weak –

Provede slabé atomické porovnání a záměna operace  **\*to**.

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
První `memory_order` argument.

*Order2*<br/>
Druhý `memory_order` argument.

### <a name="return-value"></a>Návratová hodnota

A **bool** označuje výsledek porovnání hodnoty.

### <a name="remarks"></a>Poznámky

Operaci atomické porovnání a záměna porovnává hodnotu uloženou v  **\*to** s *Exp*. Pokud jsou hodnoty stejné, operace nahradí hodnotu, která je uložena v  **\*to** s*hodnotu* pomocí operace čtení modify-write a použitím omezení pořadí paměti, které jsou určená *Order1*. Pokud nejsou hodnoty stejné, operace použije hodnotu uloženou v  **\*to** nahradit *Exp* a použije omezení pořadí paměti, která jsou určena podle *Order2* .

Slabé atomické porovnání a operace výměny provádějí výměnu, pokud porovnávané hodnoty jsou si rovny. Pokud nejsou hodnoty stejné, operace není zaručeno provedení výměny.

Přetížení, která nemají druhý `memory_order` použít implicitní *Order2* , která je založena na hodnotě *Order1*. Pokud *Order1* je `memory_order_acq_rel`, *Order2* je `memory_order_acquire`. Pokud *Order1* je `memory_order_release`, *Order2* je `memory_order_relaxed`. Ve všech ostatních případech *Order2* rovná *Order1*.

Pro přetížení, která berou dva `memory_order` parametry, hodnota *Order2* nesmí být `memory_order_release` nebo `memory_order_acq_rel`a nesmí být silnější než hodnota *Order1*.

## <a name="exchange"></a> Atomic::Exchange –

Používá zadanou hodnotu k nahrazení uložené hodnoty  **\*to**.

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

*Order*<br/>
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Uložené hodnoty  **\*to** před výměnou.

### <a name="remarks"></a>Poznámky

Tato operace provádí operaci čtení modify-write používat *hodnotu* k nahrazení hodnoty, která je uložena v  **\*to**, v rámci omezení paměti, která jsou určena podle  *Pořadí*.

## <a name="fetch_add"></a> Atomic::fetch_add –

Načte hodnotu uloženou v  **\*to**a poté přičte zadanou hodnotu k uložené hodnotě.

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

*Order*<br/>
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje hodnotu uloženou v  **\*to** před přidáním.

### <a name="remarks"></a>Poznámky

`fetch_add` Metoda provádí operaci čtení modify-write a přidává tak atomicky *hodnotu* do hodnoty uložené v proměnné  **\*to**a použije omezení paměti, která jsou určena podle *Pořadí*.

## <a name="fetch_and"></a> Atomic::fetch_and –

Provádí logické bitové a na hodnotu a existující hodnotu, která je uložena v  **\*to**.

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

*Order*<br/>
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje výsledek bitového a.

### <a name="remarks"></a>Poznámky

`fetch_and` Metoda provádí operaci čtení modify-write k nahrazení uložené hodnoty  **\*to** logickou bitovou hodnotou a z *hodnota* a aktuální hodnotou, která je uložena v  **\*to**, v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="fetch_or"></a> Atomic::fetch_or –

Provádí logické bitové nebo na hodnotu a existující hodnotu, která je uložena v  **\*to**.

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

*Order*<br/>
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje výsledek bitového nebo.

### <a name="remarks"></a>Poznámky

`fetch_or` Metoda provádí operaci čtení modify-write k nahrazení uložené hodnoty  **\*to** logickou bitovou hodnotou nebo z *hodnota* a aktuální hodnotou, která je uložena v  **\*to**, v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="fetch_sub"></a> Atomic::fetch_sub –

Odečte zadanou hodnotu od uložené hodnoty.

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

*Order*<br/>
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje výsledek odčítání.

### <a name="remarks"></a>Poznámky

`fetch_sub` Metoda provádí operaci čtení modify-write a odebírá tak atomicky *hodnotu* z hodnoty uložené v proměnné  **\*to**, v rámci omezení paměti, která jsou určena podle *Pořadí*.

## <a name="fetch_xor"></a> Atomic::fetch_xor –

Provádí bitový exkluzivní nebo na hodnotu a existující hodnotu, která je uložena v  **\*to**.

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

*Order*<br/>
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

A *Ty* objekt, který obsahuje výsledek bitový exkluzivní nebo.

### <a name="remarks"></a>Poznámky

`fetch_xor` Metoda provádí operaci čtení modify-write k nahrazení uložené hodnoty  **\*to** s bitový exkluzivní nebo *hodnota* a aktuální hodnota uložená v  **\*to**a použije omezení paměti, která jsou určena podle *pořadí*.

## <a name="is_lock_free"></a> Atomic::is_lock_free –

Určuje, zda atomické operace na  **\*to** jsou bez zámku.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud atomické operace na  **\*to** se zámek zdarma; jinak false.

### <a name="remarks"></a>Poznámky

Atomický typ je bez zámku, pokud žádné atomické operace na daném typu nepoužívají zámky.

## <a name="load"></a> Atomic::Load –

Načte uloženou hodnotu do  **\*to**, v rámci určených omezení paměti.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parametry

*Order*<br/>
A `memory_order`. *Pořadí* nesmí být `memory_order_release` nebo `memory_order_acq_rel`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v  **\*to**.

## <a name="store"></a> Atomic::Store –

Uloží zadanou hodnotu.

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

*Order*<br/>
A `memory_order` omezení.

### <a name="remarks"></a>Poznámky

Atomicky ukládá tato členská funkce *hodnotu* v `*this`, v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="see-also"></a>Viz také:

[\<Atomic >](../standard-library/atomic.md)<br/>
[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
