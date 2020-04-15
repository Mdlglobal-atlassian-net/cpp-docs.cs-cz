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
ms.openlocfilehash: c1c5593aee19254d4348d4e8658ffe9c3f0cf1b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368255"
---
# <a name="safeint-functions"></a>Funkce jazyka SafeInt

Knihovna SafeInt poskytuje několik funkcí, které můžete použít bez vytvoření instance [třídy SafeInt](../safeint/safeint-class.md). Pokud chcete chránit jednu matematickou operaci před přetečením celého čísla, můžete tyto funkce použít. Pokud chcete chránit více matematických operací, měli byste vytvořit `SafeInt` objekty. Je efektivnější vytvářet `SafeInt` objekty než používat tyto funkce vícekrát.

Tyto funkce umožňují porovnat nebo provádět matematické operace se dvěma různými typy parametrů, aniž byste je museli nejprve převést na stejný typ.

Každá z těchto funkcí má `T` `U`dva typy šablon: a . Každý z těchto typů může být logický, znakový nebo integrální typ. Integrální typy mohou být podepsané nebo nepodepsané a libovolnou velikost od 8 bitů do 64 bitů.

> [!NOTE]
> Nejnovější verze této knihovny [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)je umístěna na adrese .

## <a name="in-this-section"></a>V tomto oddílu

Funkce                      | Popis
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Přidá dvě čísla a chrání před přetečením.
[Bezpečné vysílání](#safecast)         | Přetypová jeden typ parametru na jiný typ.
[SafeDivide](#safedivide)     | Vydělí dvě čísla a chrání proti dělení nulou.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Porovná dvě čísla. Tyto funkce umožňují porovnat dva různé typy čísel bez evidenit jejich typů.
[SafeModulus](#safemodulus)   | Provede operaci modulu na dvou číslech.
[SafeMultiply](#safemultiply) | Vynásobí dvě čísla dohromady a chrání před přetečením.
[SafeSubtract](#safesubtract) | Odečte dvě čísla a chrání před přetečením.

## <a name="related-sections"></a>Související oddíly

Sekce                                                  | Popis
-------------------------------------------------------- | ----------------------------------------------------
[Safeint](../safeint/safeint-class.md)                   | Třída. `SafeInt`
[Výjimka SafeInt](../safeint/safeintexception-class.md) | Třída výjimky specifická pro knihovnu SafeInt.

## <a name="safeadd"></a><a name="safeadd"></a>Bezpečné přidání

Přidá dvě čísla způsobem, který chrání před přetečením.

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
[v] První číslo přidat. Musí to být typu T.

*U*<br/>
[v] Druhé číslo přidat. Musí to být typu U.

*Výsledek*<br/>
[out] Parametr, `SafeAdd` kde je uložen výsledek.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud nedojde k žádné chybě; **false,** pokud dojde k chybě.

## <a name="safecast"></a><a name="safecast"></a>Bezpečné vysílání

Přetypová nos jednoho typu čísla na jiný typ.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parametry

*Z*<br/>
[v] Číslo zdroje, které chcete převést. To musí být `T`typu .

*Akce*<br/>
[out] Odkaz na nový typ čísla. To musí být `U`typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud nedojde k žádné chybě; **false,** pokud dojde k chybě.

## <a name="safedivide"></a><a name="safedivide"></a>Bezpečné dělení

Vydělí dvě čísla způsobem, který chrání před dělením nulou.

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
[v] Dělitel. Musí to být typu T.

*U*<br/>
[v] Dividenda. Musí to být typu U.

*Výsledek*<br/>
[out] Parametr, `SafeDivide` kde je uložen výsledek.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud nedojde k žádné chybě; **false,** pokud dojde k chybě.

## <a name="safeequals"></a><a name="safeequals"></a>SafeEquals

Porovná dvě čísla k určení, zda jsou stejné.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[v] První číslo porovnat. Musí to být typu T.

*U*<br/>
[v] Druhé číslo porovnat. Musí to být typu U.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *t* a *u* jsou stejné; jinak **false**.

### <a name="remarks"></a>Poznámky

Metoda vylepšuje, `==` protože `SafeEquals` umožňuje porovnat dva různé typy čísel.

## <a name="safegreaterthan"></a><a name="safegreaterthan"></a>SafeGreaterThan

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
[v] První číslo porovnat. To musí být `T`typu .

*U*<br/>
[v] Druhé číslo porovnat. To musí být `U`typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *t* je větší než *u*; jinak **false**.

### <a name="remarks"></a>Poznámky

`SafeGreaterThan`rozšiřuje operátor pravidelného porovnávání tím, že umožňuje porovnat dva různé typy čísel.

## <a name="safegreaterthanequals"></a><a name="safegreaterthanequals"></a>SafeGreaterThanEquals

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
[v] První číslo porovnat. To musí být `T`typu .

*U*<br/>
[v] Druhé číslo porovnat. To musí být `U`typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *t* je větší nebo rovna *u*; jinak **false**.

### <a name="remarks"></a>Poznámky

`SafeGreaterThanEquals`vylepšuje operátor porovnání standardů, protože umožňuje porovnat dva různé typy čísel.

## <a name="safelessthan"></a><a name="safelessthan"></a>SafelessThan

Určuje, zda je jedno číslo menší než jiné.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[v] První číslo. To musí být `T`typu .

*U*<br/>
[v] Druhá číslice. To musí být `U`typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *t* je menší než *u*; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda vylepšuje operátor `SafeLessThan` porovnání standardu, protože umožňuje porovnat dva různé typy čísel.

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>SafeLessThanEquals

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
[v] První číslo porovnat. To musí být `T`typu .

*U*<br/>
[v] Druhé číslo porovnat. To musí být `U`typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *t* je menší nebo rovno *u*; jinak **false**.

### <a name="remarks"></a>Poznámky

`SafeLessThanEquals`rozšiřuje operátor pravidelného porovnávání tím, že umožňuje porovnat dva různé typy čísel.

## <a name="safemodulus"></a><a name="safemodulus"></a>SafeModulus

Provede operaci modulu na dvou číslech.

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
[v] Dělitel. To musí být `T`typu .

*U*<br/>
[v] Dividenda. To musí být `U`typu .

*Výsledek*<br/>
[out] Parametr, `SafeModulus` kde je uložen výsledek.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud nedojde k žádné chybě; **false,** pokud dojde k chybě.

## <a name="safemultiply"></a><a name="safemultiply"></a>SafeMultiply

Násobí dvě čísla společně způsobem, který chrání před přetečením.

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
[v] První číslo k násobení. To musí být `T`typu .

*U*<br/>
[v] Druhé číslo násobit. To musí být `U`typu .

*Výsledek*<br/>
[out] Parametr, `SafeMultiply` kde je uložen výsledek.

### <a name="return-value"></a>Návratová hodnota

`true`pokud nedojde k žádné chybě; `false` pokud dojde k chybě.

## <a name="safenotequals"></a><a name="safenotequals"></a>SafeNotEquals

Určuje, zda nejsou dvě čísla rovna.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[v] První číslo porovnat. To musí být `T`typu .

*U*<br/>
[v] Druhé číslo porovnat. To musí být `U`typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *t* a *u* nejsou stejné; jinak **false**.

### <a name="remarks"></a>Poznámky

Metoda vylepšuje, `!=` protože `SafeNotEquals` umožňuje porovnat dva různé typy čísel.

## <a name="safesubtract"></a><a name="safesubtract"></a>BezpečnéSubtract

Odečte dvě čísla způsobem, který chrání před přetečením.

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
[v] První číslo v odčítání. To musí být `T`typu .

*U*<br/>
[v] Číslo odečíst od *t*. To musí být `U`typu .

*Výsledek*<br/>
[out] Parametr, `SafeSubtract` kde je uložen výsledek.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud nedojde k žádné chybě; **false,** pokud dojde k chybě.
