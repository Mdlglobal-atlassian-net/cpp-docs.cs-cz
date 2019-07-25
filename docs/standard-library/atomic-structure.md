---
title: atomic – struktura
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 1b3b60d71fcdf68fdf215820535c3bfb3d4dfb2b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456736"
---
# <a name="atomic-structure"></a>atomic – struktura

Popisuje objekt, který provádí atomické operace s uloženou hodnotou typu *ty*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Členové

|Člen|Popis|
|----------|-----------------|
|**BeginRequestEventArgs**||
|[atomic](#atomic)|Vytvoří atomový objekt.|
|**Operátory**||
|[Atomic:: operator ty](#op_ty)|Přečte a vrátí uloženou hodnotu. ([atomická:: Load](#load))|
|[Atomic:: operator =](#op_eq)|Použije zadanou hodnotu k nahrazení uložené hodnoty. ([atomická:: Store](#store))|
|[Atomic:: operator + +](#op_inc)|Zvýší uloženou hodnotu. Používá se pouze specializacemi integrálního a ukazatele.|
|[Atomic:: operator + =](#op_add_eq)|Přidá zadanou hodnotu k uložené hodnotě. Používá se pouze specializacemi integrálního a ukazatele.|
|[Atomic:: operator--](#op_dec)|Sníží uloženou hodnotu. Používá se pouze specializacemi integrálního a ukazatele.|
|[Atomic:: operator-=](#op_sub_eq)|Odečte zadanou hodnotu od uložené hodnoty. Používá se pouze specializacemi integrálního a ukazatele.|
|[Atomic:: operator & =](#op_and_eq)|Provede bitovou a zadanou hodnotu a uloženou hodnotu. Používá se pouze pro celočíselné specializace.|
|[Atomic:: operator&#124;=](#op_or_eq)|Provede logickou nebo zadanou hodnotu a uloženou hodnotu. Používá se pouze pro celočíselné specializace.|
|[Atomic:: operator ^ =](#op_xor_eq)|Provede bitovou exkluzivní nebo zadanou hodnotu a uloženou hodnotu. Používá se pouze pro celočíselné specializace.|
|**Funkce**||
|[compare_exchange_strong](#compare_exchange_strong)|Provede operaci *atomic_compare_and_exchange* **a vrátí** výsledek.|
|[compare_exchange_weak](#compare_exchange_weak)|Provede operaci *weak_atomic_compare_and_exchange* **a vrátí** výsledek.|
|[fetch_add](#fetch_add)|Přidá zadanou hodnotu k uložené hodnotě.|
|[fetch_and](#fetch_and)|Provede bitovou a zadanou hodnotu a uloženou hodnotu.|
|[fetch_or](#fetch_or)|Provede logickou nebo zadanou hodnotu a uloženou hodnotu.|
|[fetch_sub](#fetch_sub)|Odečte zadanou hodnotu od uložené hodnoty.|
|[fetch_xor](#fetch_xor)|Provede bitovou exkluzivní nebo zadanou hodnotu a uloženou hodnotu.|
|[is_lock_free](#is_lock_free)|Určuje, jestli jsou atomické operace s **tímto** *zámkem bezplatné*. Atomický typ je *bez zámku* , pokud žádné atomické operace na tomto typu nepoužívají zámky.|
|[spustit](#load)|Přečte a vrátí uloženou hodnotu.|
|[store](#store)|Použije zadanou hodnotu k nahrazení uložené hodnoty.|

## <a name="remarks"></a>Poznámky

*Typ daného* typu musí být *triviální*a kopírovatelné. To znamená, že použití [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) ke zkopírování jeho bajtů musí vytvořit *platný objekt* , který se porovná s původním objektem. Členské funkce [compare_exchange_weak](#compare_exchange_weak) a [compare_exchange_strong](#compare_exchange_strong) používají [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) k určení, zda se dvě *ty* hodnoty rovnají. U těchto funkcí nebudou použity `operator==`definované *ty*. Členské funkce `atomic` použití `memcpy` ke zkopírování hodnot typu *ty*.

Částečná specializace **,\< \* >atomická** , existuje pro všechny typy ukazatelů. Specializace umožňuje přidání posunu k hodnotě spravovaného ukazatele nebo odečtení posunu od něj. Aritmetické operace přebírají argument typu `ptrdiff_t` a upravují tento argument podle velikosti těch, aby byly  konzistentní s běžnými aritmetickými adresami.

Specializace existuje pro každý celočíselný typ kromě **bool**. Každá specializace poskytuje bohatou sadu metod pro atomovou aritmetické a logické operace.

||||
|-|-|-|
|**atomický\<znak >**|**neatomická\<> znak typu se znaménkem**|**Ne> znak pro atomovou\<bez znaménka**|
|**atomic\<char16_t>**|**atomic\<char32_t>**|**atomic\<wchar_t>**|
|**atomic\<short>**|**krátkodobý\<nepodepsaný krátký >**|**atomická\<>**|
|**atomická\<nepodepsaná int >**|**atomická\<dlouhá >**|**Ne>á atomická\<nepodepsaná dlouhá**|
|**atomická\<dlouhodobá >**|**Ne>é atomické\<nepodepsané dlouhé dlouhé**|

Integrální specializace jsou odvozeny z `atomic_integral` odpovídajících typů. Například atomická **\<nepodepsaná int >** je odvozena `atomic_uint`z.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<atomická >

**Obor názvů:** std

## <a name="atomic"></a>Atomic:: Atomic

Vytvoří atomový objekt.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Inicializační hodnota.

### <a name="remarks"></a>Poznámky

Atomické objekty nelze kopírovat ani přesouvat.

Objekty, které jsou\<instancemi*atomicky*> mohou být inicializovány pouze konstruktorem, který přebírá argument typu *ta a nikoli* pomocí agregační inicializace. Objekty atomic_integral lze ale inicializovat pouze pomocí agregační inicializace.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a>Atomic:: operator *ty*

Operátor pro typ zadaný pro šablonu\< *, atomická*>. Načte uloženou hodnotu v  **\*tomto**poli.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Poznámky

Tento operátor použije `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a>Atomic:: operator =

Ukládá zadanou hodnotu.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Objekt *,* který je.

### <a name="return-value"></a>Návratová hodnota

Vrátí *hodnotu*.

## <a name="op_inc"></a>Atomic:: operator + +

Zvýší uloženou hodnotu. Používá se pouze specializacemi integrálního a ukazatele.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

První dva operátory vrátí zvýšenou hodnotu; Poslední dva operátory vrátí hodnotu před přírůstku. Operátory používají rozhraní `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a>Atomic:: operator + =

Přidá zadanou hodnotu k uložené hodnotě. Používá se pouze specializacemi integrálního a ukazatele.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Celočíselná hodnota nebo hodnota ukazatele.

### <a name="return-value"></a>Návratová hodnota

Objekt *ty* , který obsahuje výsledek přidání.

### <a name="remarks"></a>Poznámky

Tento operátor používá `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a>Atomic:: operator--

Sníží uloženou hodnotu. Používá se pouze specializacemi integrálního a ukazatele.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

První dva operátory vrátí sníženou hodnotu; Poslední dva operátory vrátí hodnotu před sníženou hodnotou. Operátory používají rozhraní `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a>Atomic:: operator-=

Odečte zadanou hodnotu od uložené hodnoty. Používá se pouze specializacemi integrálního a ukazatele.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Celočíselná hodnota nebo hodnota ukazatele.

### <a name="return-value"></a>Návratová hodnota

Objekt *ty* , který obsahuje výsledek odčítání.

### <a name="remarks"></a>Poznámky

Tento operátor používá `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a>Atomic:: operator & =

Provede bitovou a zadanou hodnotu a uloženou  **\*hodnotu.** Používá se pouze pro celočíselné specializace.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Hodnota typu *ty*.

### <a name="return-value"></a>Návratová hodnota

Výsledek bitového a.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci čtení a úprav-zápisu, která nahradí uloženou  **\*hodnotu s** bitovým a *hodnotou* a aktuální hodnotou, která je  **\*uložena v rámci**omezení `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a>Atomic:: operator&#124;=

Provede logickou nebo zadanou hodnotu a uloženou  **\*hodnotu.** Používá se pouze pro celočíselné specializace.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Hodnota typu *ty*.

### <a name="return-value"></a>Návratová hodnota

Výsledek bitového operátoru OR.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci čtení a úprav-zápisu, která nahradí uloženou  **\*hodnotu s** bitovým nebo *hodnotou* a aktuální hodnotou, která je  **\*uložena v rámci**omezení `memory_order_seq_cst`omezení [memory_order](atomic-enums.md) .

## <a name="op_xor_eq"></a>Atomic:: operator ^ =

Provede bitovou exkluzivní nebo zadanou hodnotu a uloženou  **\*hodnotu.** Používá se pouze pro celočíselné specializace.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Osa*\
Hodnota typu *ty*.

### <a name="return-value"></a>Návratová hodnota

Výsledek bitového exkluzivního nebo.

### <a name="remarks"></a>Poznámky

Tento operátor provádí operaci čtení a úprav-zápisu, která nahradí uloženou  **\*hodnotu s** bitovým výhradním nebo *hodnotou* a aktuální hodnotou, která je  **\*uložena v rámci**omezení `memory_order_seq_cst` omezení [memory_order](atomic-enums.md) .

## <a name="compare_exchange_strong"></a>Atomic:: compare_exchange_strong

Provede operaci  **\*** atomické porovnání a výměny.

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

*Oček*\
Hodnota typu *ty*.

*Osa*\
Hodnota typu *ty*.

*Order1*\
První `memory_order` argument.

*Order2*\
Druhý `memory_order` argument.

### <a name="return-value"></a>Návratová hodnota

**Logická** hodnota, která určuje výsledek porovnání hodnoty.

### <a name="remarks"></a>Poznámky

Tato operace atomické porovnání a výměny porovnává hodnotu uloženou v  **\*tomto** případě s hodnotou *exp*. Pokud jsou hodnoty stejné, operace nahradí hodnotu uloženou v  **\*této** *hodnotě hodnotou* pomocí operace read-modify-write a použitím omezení pořadí paměti, která jsou určena parametrem *Order1*. Pokud se hodnoty neshodují, operace používá hodnotu, která je uložena v  **\*tomto** argumentu k nahrazení *exp* a použije omezení pořadí paměti, která jsou určena *Order2*.

Přetížení, která nemají druhý `memory_order` , používají implicitní *Order2* , která je založena na hodnotě *Order1*. Pokud  je `memory_order_acq_rel`Order1, *Order2* je `memory_order_acquire`. Pokud  je `memory_order_release`Order1, *Order2* je `memory_order_relaxed`. Ve všech ostatních případech se *Order2* rovná *Order1*.

Pro přetížení, která přijímají dva `memory_order` parametry, nesmí být `memory_order_release` hodnota *Order2* nebo `memory_order_acq_rel`a nesmí být silnější než hodnota *Order1*.

## <a name="compare_exchange_weak"></a>Atomic:: compare_exchange_weak

Provádí v  **\*tomto**případě slabé operace atomické porovnání a výměny.

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

*Oček*\
Hodnota typu *ty*.

*Osa*\
Hodnota typu *ty*.

*Order1*\
První `memory_order` argument.

*Order2*\
Druhý `memory_order` argument.

### <a name="return-value"></a>Návratová hodnota

**Logická** hodnota, která určuje výsledek porovnání hodnoty.

### <a name="remarks"></a>Poznámky

Tato operace atomické porovnání a výměny porovnává hodnotu uloženou v  **\*tomto** případě s hodnotou *exp*. Pokud jsou hodnoty stejné, operace nahradí hodnotu uloženou v  **\*této** *hodnotě hodnotou* pomocí operace read-modify-write a použitím omezení pořadí paměti, která jsou určena parametrem *Order1*. Pokud se hodnoty neshodují, operace používá hodnotu, která je uložena v  **\*tomto** argumentu k nahrazení *exp* a použije omezení pořadí paměti, která jsou určena *Order2*.

Slabé atomické porovnání a operace Exchange provádí výměnu, pokud se porovnávané hodnoty rovnají. Pokud se hodnoty neshodují, operace není zaručena k provedení výměny.

Přetížení, která nemají druhý `memory_order` , používají implicitní *Order2* , která je založena na hodnotě *Order1*. Pokud  je `memory_order_acq_rel`Order1, *Order2* je `memory_order_acquire`. Pokud  je `memory_order_release`Order1, *Order2* je `memory_order_relaxed`. Ve všech ostatních případech se *Order2* rovná *Order1*.

Pro přetížení, která přijímají dva `memory_order` parametry, nesmí být `memory_order_release` hodnota *Order2* nebo `memory_order_acq_rel`a nesmí být silnější než hodnota *Order1*.

## <a name="exchange"></a>Atomic:: Exchange

Použije zadanou hodnotu k nahrazení uložené hodnoty  **\*this**.

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

*Osa*\
Hodnota typu *ty*.

*Za*\
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Uložená hodnota  **\*tohoto** serveru před výměnou.

### <a name="remarks"></a>Poznámky

Tato operace provede operaci čtení a úprav-zápisu k použití *hodnoty* k nahrazení hodnoty, která je  **\*uložena v rámci**omezení paměti, která jsou určena podle *pořadí*.

## <a name="fetch_add"></a>Atomic:: fetch_add

Načte hodnotu uloženou v  **\*tomto**a potom do uložené hodnoty přidá zadanou hodnotu.

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

*Osa*\
Hodnota typu *ty*.

*Za*\
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Objekt *,* který obsahuje hodnotu uloženou v  **\*této** části před sčítáním.

### <a name="remarks"></a>Poznámky

Metoda provádí operaci čtení a úprav-zápisu k atomické přidání *hodnoty* do uložené hodnoty v  **\*tomto**a aplikuje omezení paměti, která jsou určena podle *pořadí.* `fetch_add`

## <a name="fetch_and"></a>Atomic:: fetch_and

Provede bitové a na hodnotu a existující hodnotu, která je uložena v  **\*tomto**.

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

*Osa*\
Hodnota typu *ty*.

*Za*\
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Objekt *ty* , který obsahuje výsledek bitového operátoru and.

### <a name="remarks"></a>Poznámky

Metoda provádí operaci čtení a úprav-zápisu, která nahradí uloženou  **\*hodnotu s** bitovým a *hodnotou* a aktuální hodnotou, která je  **\*uložena v rámci paměti** `fetch_and` omezení, která jsou určena podle *pořadí*.

## <a name="fetch_or"></a>Atomic:: fetch_or

Provede logickou hodnotu nebo na hodnotu a existující hodnotu, která je uložena v  **\*tomto**.

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

*Osa*\
Hodnota typu *ty*.

*Za*\
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Objekt *ty* , který obsahuje výsledek bitového operátoru OR.

### <a name="remarks"></a>Poznámky

Metoda provádí operaci čtení a úprav-zápisu, která nahradí uloženou  **\*hodnotu s** bitovým nebo *hodnotou* a aktuální hodnotou, která je  **\*uložena v rámci paměti** `fetch_or` omezení, která jsou určena podle *pořadí*.

## <a name="fetch_sub"></a>Atomic:: fetch_sub

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

*Osa*\
Hodnota typu *ty*.

*Za*\
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Objekt *ty* , který obsahuje výsledek odčítání.

### <a name="remarks"></a>Poznámky

Metoda provádí operaci čtení a úprav-zápisu pro atomovou odčítání *hodnoty* z uložené  **\*hodnoty v rámci**omezení paměti, která jsou určena podle *pořadí.* `fetch_sub`

## <a name="fetch_xor"></a>Atomic:: fetch_xor

Provede bitovou exkluzivní nebo na hodnotu a existující hodnotu, která je uložena v  **\*tomto**.

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

*Osa*\
Hodnota typu *ty*.

*Za*\
A `memory_order`.

### <a name="return-value"></a>Návratová hodnota

Objekt *,* který obsahuje výsledek bitového exkluzivního nebo.

### <a name="remarks"></a>Poznámky

Metoda provádí operaci čtení a úprav-zápisu, která nahradí uloženou  **\*hodnotu s** bitovým výhradním nebo *hodnotou* a aktuální hodnotou, která je uložena v  **\*tomto**a použije `fetch_xor` omezení paměti, která jsou určena podle *pořadí*.

## <a name="is_lock_free"></a>Atomic:: is_lock_free

Určuje, jestli jsou atomické operace s  **\*tímto** zámkem bezplatné.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Návratová hodnota

true, pokud jsou atomické operace v  **\*tomto** případě zamčené. v opačném případě false.

### <a name="remarks"></a>Poznámky

Atomický typ je bez zámku, pokud žádné atomické operace na tomto typu nepoužívají zámky.

## <a name="load"></a>atomická:: Load

Načte uloženou  **\*hodnotu v rámci**zadaného omezení paměti.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parametry

*Za*\
A `memory_order`. *Pořadí* nesmí být `memory_order_release` nebo `memory_order_acq_rel`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v  **\*tomto**.

## <a name="store"></a>Atomic:: Store

Ukládá zadanou hodnotu.

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

*Osa*\
Objekt *,* který je.

*Za*\
`memory_order` Omezení.

### <a name="remarks"></a>Poznámky

Tato členská funkce atomicky  ukládá hodnotu `*this`v v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="see-also"></a>Viz také:

[\<atomická >](../standard-library/atomic.md)\
[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
