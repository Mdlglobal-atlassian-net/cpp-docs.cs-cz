---
title: SafeInt – třída
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: c69dc7ed5e34d98d5acff8f2bc28c34761bd31c6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076823"
---
# <a name="safeint-class"></a>SafeInt – třída

Rozšiřuje primitivní prvky Integer, aby se zabránilo přetečení celého čísla, a umožňuje porovnat různé typy celých čísel.

> [!NOTE]
> Nejnovější verzi této knihovny najdete na adrese [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parametry

| Šablona  |  Popis |
|--------|------------|
| T         |  Typ celého čísla nebo logického parametru, který `SafeInt` nahrazovat. |
| E         |  Výčtový datový typ, který definuje zásady zpracování chyb. |
| U         |  Typ celého čísla nebo logického parametru pro sekundární operand. |

| Parametr  |  Popis |
|---------|-----------------|
| *zarovnání indirekce RHS*      |  pro Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatných funkcích. |
| *došlo*        |  pro Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatných funkcích. |
| *bit*     |  pro Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatných funkcích. |

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Název                          |  Popis |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  Výchozí konstruktor |

### <a name="assignment-operators"></a>Operátory přiřazení

| Název  |  Syntaxe |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Operátory přetypování

| Název              |  Syntaxe |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| signed char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| Nepodepsaný __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| Nepodepsaný __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| Nepodepsaný __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>Operátory porovnání

| Název  |  Syntaxe |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>Aritmetické operátory

| Název  |  Syntaxe |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>Logické operátory

| Název     |  Syntaxe |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>Poznámky

Třída `SafeInt` chrání proti přetečení celého čísla v matematických operacích. Zvažte například přidání dvou 8bitových celých čísel: jedna má hodnotu 200 a druhá má hodnotu 100. Správná Matematická operace by byla 200 + 100 = 300. Vzhledem k 8bitové celočíselné celočíselné velikosti se však ztratí horní bit a kompilátor vrátí 44 (300-2<sup>8</sup>) jako výsledek. Jakákoli operace, která závisí na této matematické rovnici, bude generovat neočekávané chování.

Třída `SafeInt` kontroluje, zda dojde k aritmetickému přetečení nebo zda se kód pokusí dělit nulou. V obou případech třída volá obslužnou rutinu chyb a upozorní program na potenciální problém.

Tato třída také umožňuje porovnat dva různé typy celých čísel, pokud jsou `SafeInt` objekty. Když porovnání provedete, je třeba nejprve převést čísla na stejný typ. Přetypování jednoho čísla na jiný typ často vyžaduje kontroly, aby se zajistilo, že nedochází ke ztrátě dat.

Tabulka Operators v tomto tématu uvádí matematické operátory a operátory porovnání podporované třídou `SafeInt`. Většina matematických operátorů vrací objekt `SafeInt` typu `T`.

Operace porovnání mezi `SafeInt` a integrálním typem lze provádět v obou směrech. Například `SafeInt<int>(x) < y` i `y> SafeInt<int>(x)` jsou platné a vrátí stejný výsledek.

Mnoho binárních operátorů nepodporuje použití dvou různých typů `SafeInt`. Jedním z příkladů je operátor `&`. `SafeInt<T, E> & int` se podporuje, ale `SafeInt<T, E> & SafeInt<U, E>` ne. V druhém příkladu kompilátor neví, jaký typ parametru má být vrácen. Jedním z řešení tohoto problému je přetypovat druhý parametr zpět na základní typ. Pomocí stejných parametrů lze to provést s `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> U všech bitových operací by měly mít dva různé parametry stejnou velikost. Pokud se velikosti liší, kompilátor vyvolá výjimku [vyhodnocení](../mfc/reference/diagnostic-services.md#assert) . Výsledky této operace nelze zaručit, aby byly přesné. Chcete-li vyřešit tento problém, přetypování menšího parametru, dokud nemá stejnou velikost jako větší parametr.

Pro operátory posunutí se při posunování více bitů, než je existence pro typ šablony, vyvolá výjimka vyhodnocení. To nebude mít žádný vliv na režim vydání. Kombinování dvou typů parametrů SafeInt je možné pro operátory posunutí, protože návratový typ je stejný jako původní typ. Číslo na pravé straně operátoru určuje počet bitů, které se mají posunout.

Při provádění logického porovnání s objektem SafeInt je porovnání čistě aritmetické. Zvažte například tyto výrazy:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

První příkaz se přeloží na **true**, ale druhý příkaz se přeloží na `false`. Bitový operátor negace 0 je 0xFFFFFFFF. Ve druhém příkazu porovnává výchozí operátor porovnání 0xFFFFFFFF až 0xFFFFFFFF a považuje se za rovné. Relační operátor pro třídu `SafeInt` si uvědomuje, že druhý parametr je záporný, zatímco první parametr je nepodepsaný. Proto i když je bitová reprezentace identická, `SafeInt` logický operátor, že unsigned integer je větší než-1.

Buďte opatrní při použití třídy `SafeInt` společně s operátorem `?:` Ternární. Vezměte v úvahu následující řádek kódu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilátor ho převede na toto:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Pokud je `flag` `false`, kompilátor vyvolá výjimku namísto přiřazení hodnoty-1 k `x`. Proto chcete-li se tomuto chování vyhnout, správný kód, který se má použít, je následující řádek.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` a `U` lze přiřadit logický typ, typ znaku nebo typ Integer. Celočíselné typy mohou být podepsány nebo bez znaménka a libovolná velikost od 8 do 64 bitů.

> [!NOTE]
> I když třída `SafeInt` akceptuje libovolný typ celého čísla, funguje efektivněji s typy bez znaménka.

`E` je mechanismus zpracování chyb, který `SafeInt` používá. V knihovně SafeInt jsou k dispozici dva mechanismy zpracování chyb. Výchozí zásada je `SafeIntErrorPolicy_SafeIntException`, což vyvolá výjimku [třídy SafeIntException –](../safeint/safeintexception-class.md) při výskytu chyby. Druhá zásada je `SafeIntErrorPolicy_InvalidParameter`, která zastaví program, pokud dojde k chybě.

Existují dvě možnosti přizpůsobení zásady chyb. První možností je nastavit parametr `E` při vytváření `SafeInt`. Tuto možnost použijte, pokud chcete změnit zásady zpracování chyb pouze pro jednu `SafeInt`. Druhou možností je definovat _SAFEINT_DEFAULT_ERROR_POLICY jako vlastní třídu pro zpracování chyb, než bude zahrnuta do knihovny `SafeInt`. Tuto možnost použijte, pokud chcete změnit výchozí zásady zpracování chyb pro všechny instance `SafeInt` třídy v kódu.

> [!NOTE]
> Přizpůsobená třída, která zpracovává chyby z knihovny SafeInt, by neměla vracet řízení kódu, který se nazývá obslužná rutina chyb. Po volání obslužné rutiny chyby nemůže být výsledek operace `SafeInt` důvěryhodný.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SafeInt`

## <a name="requirements"></a>Požadavky

**Hlavička:** SafeInt. h

**Obor názvů:** MSL:: Utilities

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt:: SafeInt

Vytvoří objekt `SafeInt`.

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)
```

### <a name="parameters"></a>Parametry

*došlo*<br/>
pro Hodnota nového objektu `SafeInt`. Toto musí být parametr typu T nebo U v závislosti na konstruktoru.

*b*<br/>
pro Logická hodnota nového objektu `SafeInt`.

*h*<br/>
pro `SafeInt` typu U. Nový objekt `SafeInt` bude mít stejnou hodnotu jako *u*, ale bude typu t.

U typ dat uložených v `SafeInt`. Může se jednat o logický, znakový nebo celočíselný typ. Pokud se jedná o celočíselný typ, může být podepsán nebo bez znaménka a musí být mezi 8 a 64 bity.

### <a name="remarks"></a>Poznámky

Vstupní parametr pro konstruktor, *i i* *u*musí být logický, znakový nebo celočíselný typ. Pokud je to jiný typ parametru, třída `SafeInt` volá [static_assert](../cpp/static-assert.md) , aby označovala Neplatný vstupní parametr.

Konstruktory, které používají typ šablony `U` automaticky převádí vstupní parametr na typ určený parametrem `T`. Třída `SafeInt` převádí data bez ztráty dat. Oznamuje `E` obslužné rutině chyb, pokud nemůže převést data na typ `T` bez ztráty dat.

Pokud vytvoříte `SafeInt` z logického parametru, musíte hodnotu inicializovat hned. Nelze vytvořit `SafeInt` pomocí `SafeInt<bool> sb;`kódu. Tím se vygeneruje chyba kompilace.
