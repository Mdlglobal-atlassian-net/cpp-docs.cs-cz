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
ms.openlocfilehash: 70343d4dbaf4b57c83d28e225419164906e2b1ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445146"
---
# <a name="safeint-class"></a>SafeInt – třída

Rozšiřuje primitivy celé číslo zabránit přetečení celého čísla a umožňuje vám srovnávat odlišné typy celých čísel.

> [!NOTE] 
> Nejnovější verzi této knihovny se nachází v [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parametry

Šablony | Popis
-------- | -------------------------------------------------------------------
T        | Typ celého čísla nebo parametr logické hodnoty, které `SafeInt` nahradí.
E        | Výčtový datový typ, který definuje chyba zpracování zásad.
U        | Typ celého čísla nebo parametr logické hodnoty pro sekundární operand.

Parametr | Popis
--------- | ---------------------------------------------------------------------------------------------------------------------
*Zarovnání indirekce RHS*     | [in] Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatné funkce.
*i*       | [in] Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatné funkce.
*Služba BITS*    | [in] Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatné funkce.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                         | Popis
---------------------------- | --------------------
[SafeInt::SafeInt](#safeint) | Výchozí konstruktor.

### <a name="assignment-operators"></a>Operátory přiřazení

Název | Syntaxe
---- | ---------------------------------------------------------------------------------------
=    | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`
=    | `SafeInt<T,E>& operator= (const T& rhs) throw()`
=    | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`
=    | `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`

### <a name="casting-operators"></a>Operátory přetypování

Název             | Syntaxe
---------------- | -----------------------------------
bool             | `operator bool() throw()`
char             | `operator char() const`
podepsané char      | `operator signed char() const`
unsigned char    | `operator unsigned char() const`
__int16          | `operator __int16() const`
__int16 bez znaménka | `operator unsigned __int16() const`
__int32          | `operator __int32() const`
__int32 bez znaménka | `operator unsigned __int32() const`
long             | `operator long() const`
unsigned long    | `operator unsigned long() const`
__int64          | `operator __int64() const`
unsigned __int64 | `operator unsigned __int64() const`
wchar_t          | `operator wchar_t() const`

### <a name="comparison-operators"></a>Operátory porovnání

Název | Syntaxe
---- | --------------------------------------------------------------------------
<    | `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`
<    | `bool operator< (SafeInt<T,E> rhs) const throw()`
>=   | `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`
>=   | `Bool operator>= (SafeInt<T,E> rhs) const throw()`
>    | `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`
>    | `Bool operator> (SafeInt<T,E> rhs) const throw()`
<=   | `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`
<=   | `bool operator<= (SafeInt<T,E> rhs) const throw()`
==   | `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`
==   | `bool operator== (bool rhs) const throw()`
==   | `bool operator== (SafeInt<T,E> rhs) const throw()`
!=   | `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`
!=   | `bool operator!= (bool b) const throw()`
!=   | `bool operator!= (SafeInt<T,E> rhs) const throw()`

### <a name="arithmetic-operators"></a>Aritmetické operátory

Název | Syntaxe
---- | ---------------------------------------------------------------------------------
+    | `const SafeInt<T,E>& operator+ () const throw()`
-    | `SafeInt<T,E> operator- () const`
++   | `SafeInt<T,E>& operator++ ()`
--   | `SafeInt<T,E>& operator-- ()`
%    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`
%    | `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`
%=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`
%=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`
*    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`
*    | `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`
*=   | `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`
*=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`
*=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`
/    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`
/    | `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`
/=   | `SafeInt<T,E>& operator/= (SafeInt<T,E> i)`
/=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`
/=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`
+    | `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`
+    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`
+=   | `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`
+=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`
+=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`
-    | `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`
-    | `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`
-=   | `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`
-=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`
-=   | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`

### <a name="logical-operators"></a>Logické operátory

Název    | Syntaxe
------- | -----------------------------------------------------------------------------------------------
!       | `bool operator !() const throw()`
~       | `SafeInt<T,E> operator~ () const throw()`
<<      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`
<<      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`
<<=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`
<<=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`
>>      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`
>>      | `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`
>>=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`
>>=     | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`
&       | `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`
&       | `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`
&=      | `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`
&=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`
&=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`
^       | `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`
^       | `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`
^=      | `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`
^=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`
^=      | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`
&#124;  | `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`
&#124;  | `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`
&#124;= | `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`
&#124;= | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`
&#124;= | `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`

## <a name="remarks"></a>Poznámky

`SafeInt` Třídy chrání proti přetečení celého čísla v matematické operace. Představte si třeba přidání dvou 8bitových celých čísel: jeden má hodnotu 200 a druhý má hodnotu 100. Správné matematickou operací může být 200 + 100 = 300. Nicméně z důvodu omezení 8bitové celé číslo, horní bit budou ztraceny a kompilátor vrátí 44 (300-2<sup>8</sup>) jako výsledek. Jakékoli operaci, která závisí na tomto matematické rovnice vygeneruje neočekávané chování.

`SafeInt` Třída zkontroluje, zda dojde k aritmetické přetečení nebo zda kód se pokusí dělení nulou. Třída v obou případech se volá obslužná rutina chyb upozornit program potenciální problém.

Tato třída také umožňuje porovnat dva různé typy celých čísel za předpokladu, že jsou `SafeInt` objekty. Obvykle když provádíte porovnání, je nutné nejprve převést čísla bude stejného typu. Kontroluje, ujistěte se, že nedochází ke ztrátě dat přetypování jedno číslo na jiný typ často vyžaduje.

V tabulce operátory v tomto tématu jsou uvedeny operátory matematické a porovnání podporovaných `SafeInt` třídy. Vrátí největší matematické operátory `SafeInt` objekt typu `T`.

Operace porovnání mezi `SafeInt` a celočíselného typu lze provést v obou směrech. Například obě `SafeInt<int>(x) < y` a `y> SafeInt<int>(x)` jsou platné a vrátí stejné výsledky.

Mnoho binárních operátorů nepodporují pomocí dvou různých `SafeInt` typy. Jedním z příkladů je `&` operátor. `SafeInt<T, E> & int` je podporováno, ale `SafeInt<T, E> & SafeInt<U, E>` není. V druhém příkladu kompilátor nezná typ parametru se má vrátit. Jedním řešením tohoto problému je přetypování druhý parametr zpět do základního typu. Pomocí stejné parametry to můžete udělat s `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> Všechny bitové operace dva různé parametry by měly mít stejnou velikost. Pokud se liší velikosti, vyvolá kompilátor [ASSERT](../mfc/reference/diagnostic-services.md#assert) výjimky. Výsledky této operace nelze zaručit přesné. Chcete-li tento problém vyřešit, přetypovat parametr menší dokud má stejnou velikost jako parametr větší.

Pro operátory posunutí posunutí další bitů než neexistuje pro typ šablony vyvolá výjimku kontrolní VÝRAZ. V režimu vydání, to nebude mít žádný vliv. Kombinování dva typy parametrů SafeInt – je možné pro operátory posunutí, protože návratový typ je stejný jako původní typ. Číslo na pravé straně operátoru pouze označuje počet bitů na posunu.

Při provádění logické porovnání s objektem SafeInt je výhradně aritmetické porovnání. Představte si třeba tyto výrazy:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

První příkaz se překládá na **true**, ale druhý příkaz přeloží na `false`. Bitová negace 0 je 0xFFFFFFFF. V druhém příkazu výchozí operátor porovnání porovná 0xFFFFFFFF na 0xFFFFFFFF a je rovna považuje za. Operátor porovnání pro `SafeInt` třídy si uvědomuje, že druhý parametr je záporné, že první parametr je bez znaménka. Proto, i když bitové reprezentace je stejné, `SafeInt` logický operátor, který si uvědomuje, že je celé číslo bez znaménka větší než -1.

Buďte opatrní při použití `SafeInt` třídy společně s `?:` Ternární operátor. Vezměte v úvahu následující řádek kódu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilátor převede na toto:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Pokud `flag` je `false`, kompilátor vyvolá výjimku namísto přiřazení hodnoty -1 pro `x`. Chcete-li toto chování vyhnout, je správný kód, který použije proto následující řádek.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` a `U` je možné přiřadit typu Boolean, typ znaku nebo typ integer. Celočíselné typy mohou být podepsaný nebo nepodepsaný řetězec a libovolné velikosti z 8 bitů na 64 bitů.

> [!NOTE]
> I když `SafeInt` třídy přijímá libovolný typ celé číslo, funguje efektivněji pomocí typů bez znaménka.

`E` je mechanismus zpracování chyb, které `SafeInt` používá. SafeInt – knihovna jsou součástí dva mechanismy zpracování chyb. Výchozí zásada je `SafeIntErrorPolicy_SafeIntException`, kterou vyvolá [SafeIntException – třída](../windows/safeintexception-class.md) výjimky, když dojde k chybě. Tato zásada je `SafeIntErrorPolicy_InvalidParameter`, které program zastaví, pokud dojde k chybě.

Existují dvě možnosti, jak upravit chybové zásady. První možností je nastavit parametr `E` při vytváření `SafeInt`. Tuto možnost použijte, pokud chcete změnit chyba zpracování zásad pro jedno `SafeInt`. Další možností je definování _SAFEINT_DEFAULT_ERROR_POLICY být vaše vlastní třídy zpracování chyb, než je zahrnout `SafeInt` knihovny. Tuto možnost použijte, pokud chcete změnit výchozí chyba zpracování zásad pro všemi instancemi `SafeInt` třídy v kódu.

> [!NOTE]
> Vlastní třída, která zpracovává chyby z SafeInt – knihovna by neměly vracet ovládací prvek kódu, který volá obslužná rutina chyb. Po zavolání obslužná rutina chyb, výsledek `SafeInt` operace nemůže být důvěryhodný.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SafeInt`

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** msl::utilities

## <a name="safeint"></a>SafeInt::SafeInt

Vytvoří `SafeInt` objektu.

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

*i*<br/>
[in] Hodnota pro novou `SafeInt` objektu. Musí se jednat o parametr typu T nebo U, v závislosti na konstruktor.

*b*<br/>
[in] Logická hodnota pro novou `SafeInt` objektu.

*u*<br/>
[in] A `SafeInt` z typu U. Nové `SafeInt` objektu bude mít stejnou hodnotu jako *u*, ale budou typu T.

U typu dat uložených v `SafeInt`. To může být typu logická hodnota, znak nebo celé číslo. Pokud je typ integer, může být podepsané nebo nepodepsané a mít délku 8 až 64 bitů.

### <a name="remarks"></a>Poznámky

Vstupní parametr pro konstruktor, *můžu* nebo *u*, musí být typu logická hodnota, znak nebo celé číslo. Pokud je jiný typ parametru, `SafeInt` třídy volání [static_assert](../cpp/static-assert.md) udávajících Neplatný vstupní parametr.

Konstruktory, které používají typ šablony `U` automaticky převést na typ zadaný vstupní parametr `T`. `SafeInt` Převede data bez ztráty dat třídy. Oznámí na obslužnou rutinu chyby `E` Pokud nemůže převést data na typ `T` bez ztráty dat.

Pokud jste vytvořili `SafeInt` z parametr logické hodnoty, je nutné inicializovat hodnotu okamžitě. Nelze vytvořit `SafeInt` pomocí kódu `SafeInt<bool> sb;`. Tím se vygeneruje chybu kompilace.
