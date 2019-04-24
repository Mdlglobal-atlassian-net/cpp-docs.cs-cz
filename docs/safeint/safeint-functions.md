---
title: Funkce jazyka SafeInt
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: e31cf35c903a0e7572ce7d47ada21c4603119cb2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179348"
---
# <a name="safeint-functions"></a>Funkce jazyka SafeInt

SafeInt – knihovna poskytuje několik funkcí, které lze použít bez vytvoření instance [SafeInt – třída](../safeint/safeint-class.md). Pokud chcete zabránit přetečení celého čísla jedné matematické operace, můžete tyto funkce. Pokud chcete chránit několik matematických operací, měli byste vytvořit `SafeInt` objekty. Je mnohem efektivnější, chcete-li vytvořit `SafeInt` objektů, než se tyto funkce používat více než jednou.

Tyto funkce umožňují snadno porovnat nebo provádění matematických operací na dva různé typy parametrů, aniž by bylo nutné je nejprve převést na stejný typ.

Každá z těchto funkcí má dva typy šablon: `T` a `U`. Každý z těchto typů může být logická hodnota, znak nebo celočíselného typu. Integrální typy mohou být podepsaný nebo nepodepsaný řetězec a libovolné velikosti z 8 bitů na 64 bitů.

> [!NOTE]
> Nejnovější verzi této knihovny se nachází v [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="in-this-section"></a>V tomto oddílu

Funkce                      | Popis
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Sečte dvě čísla a chrání proti přetečení.
[SafeCast](#safecast)         | Přetypování jednoho typu na jiný typ parametru.
[SafeDivide](#safedivide)     | Provede podíl dvou čísel a chrání proti dělení nulou.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Porovná dvě čísla. Tyto funkce umožňují snadno porovnat dva různé typy čísel beze změny jejich typy.
[SafeModulus](#safemodulus)   | Provádí operace numerického zbytku dvou čísel.
[SafeMultiply](#safemultiply) | Vynásobí dvě čísla společně a chrání proti přetečení.
[SafeSubtract](#safesubtract) | Odečte dvou čísel a chrání proti přetečení.

## <a name="related-sections"></a>Související oddíly

Sekce                                                  | Popis
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | `SafeInt` Třídy.
[SafeIntException](../safeint/safeintexception-class.md) | Třídy výjimek specifické pro SafeInt – knihovna.

## <a name="safeadd"></a>SafeAdd

Sečte dvě čísla způsobem, který chrání proti přetečení.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Chcete-li přidat o první číslo. Toto musí být typu T.

*u*<br/>
[in] Druhé číslo, které chcete přidat. Musí se jednat o typ U.

*výsledek*<br/>
[out] Parametr kde `SafeAdd` výsledek je uložen.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="safecast"></a>SafeCast

Přetypování jednom typu čísla do jiného typu.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
[in] Zdroj číslo k převedení. Musí se jednat o typ `T`.

*Komu*<br/>
[out] Odkaz na nový typ number. Musí se jednat o typ `U`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="safedivide"></a>SafeDivide

Provede podíl dvou čísel způsobem, který chrání před dělení nulou.

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Dělitel. Toto musí být typu T.

*u*<br/>
[in] Dividenda. Musí se jednat o typ U.

*výsledek*<br/>
[out] Parametr kde `SafeDivide` výsledek je uložen.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="safeequals"></a>SafeEquals

Porovná dvě čísla, chcete-li zjistit, jestli jsou shodné.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo k porovnání. Toto musí být typu T.

*u*<br/>
[in] Druhé číslo k porovnání. Musí se jednat o typ U.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* a *u* jsou stejné; jinak **false**.

### <a name="remarks"></a>Poznámky

Metoda rozšiřuje `==` protože `SafeEquals` umožňuje porovnat dva různé typy čísel.

## <a name="safegreaterthan"></a>SafeGreaterThan

Porovná dvě čísla.

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo k porovnání. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo k porovnání. Musí se jednat o typ `U`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* je větší než *u*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

`SafeGreaterThan` operátor porovnání regulární rozšiřuje tím, že můžete porovnat dva různé typy čísel.

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Porovná dvě čísla.

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo k porovnání. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo k porovnání. Musí se jednat o typ `U`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* je větší než nebo rovna hodnotě *u*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

`SafeGreaterThanEquals` operátor porovnání standardní zvyšuje, protože ho můžete porovnat dva různé typy čísel.

## <a name="safelessthan"></a>SafeLessThan

Určuje, zda je jedno číslo menší než jiný.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo. Musí se jednat o typ `U`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* je menší než *u*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

Tato metoda rozšiřuje standardní relační operátor protože `SafeLessThan` umožňuje porovnat dva různé typy číslo.

## <a name="safelessthanequals"></a>SafeLessThanEquals

Porovná dvě čísla.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo k porovnání. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo k porovnání. Musí se jednat o typ `U`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* je menší než nebo rovna hodnotě *u*; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

`SafeLessThanEquals` operátor porovnání regulární rozšiřuje tím, že můžete porovnat dva různé typy čísel.

## <a name="safemodulus"></a>SafeModulus

Provádí operace numerického zbytku dvou čísel.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Dělitel. Musí se jednat o typ `T`.

*u*<br/>
[in] Dividenda. Musí se jednat o typ `U`.

*výsledek*<br/>
[out] Parametr kde `SafeModulus` výsledek je uložen.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.

## <a name="safemultiply"></a>SafeMultiply

Vynásobí dvě čísla společně způsobem, který chrání proti přetečení.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo pro vynásobení. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo pro vynásobení. Musí se jednat o typ `U`.

*výsledek*<br/>
[out] Parametr kde `SafeMultiply` výsledek je uložen.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud nedojde k žádné chybě; `false` Pokud dojde k chybě.

## <a name="safenotequals"></a>SafeNotEquals

Určuje, pokud dvě čísla nejsou stejné.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo k porovnání. Musí se jednat o typ `T`.

*u*<br/>
[in] Druhé číslo k porovnání. Musí se jednat o typ `U`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *t* a *u* nejsou stejné; jinak **false**.

### <a name="remarks"></a>Poznámky

Metoda rozšiřuje `!=` protože `SafeNotEquals` umožňuje porovnat dva různé typy čísel.

## <a name="safesubtract"></a>SafeSubtract

Odečte dvě čísla způsobem, který chrání proti přetečení.

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] První číslo v odčítání. Musí se jednat o typ `T`.

*u*<br/>
[in] Číslo, které se má odečíst od *t*. Musí se jednat o typ `U`.

*výsledek*<br/>
[out] Parametr kde `SafeSubtract` výsledek je uložen.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.
