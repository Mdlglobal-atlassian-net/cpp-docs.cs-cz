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
ms.openlocfilehash: c365b5cab5814d3992e6570949a69fc5d39c1dd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373443"
---
# <a name="safeint-class"></a>SafeInt – třída

Rozšiřuje celá základní primitiva, aby se zabránilo přetečení celého čísla a umožňuje porovnat různé typy celá čísla.

> [!NOTE]
> Nejnovější verze této knihovny [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)je umístěna na adrese .

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parametry

| Šablona  |  Popis |
|--------|------------|
| T         |  Typ celého čísla nebo logického `SafeInt` parametru, který nahrazuje. |
| E         |  Výčtový datový typ, který definuje zásady zpracování chyb. |
| U         |  Typ celého čísla nebo logického parametru pro sekundární operand. |

| Parametr  |  Popis |
|---------|-----------------|
| *rhs*      |  [v] Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatných funkcích. |
| *I*        |  [v] Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatných funkcích. |
| *Bitů*     |  [v] Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatných funkcích. |

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Name (Název)                          |  Popis |
|---------------------------|--------------------|
| [SafeInt::SafeInt](#safeint)  |  Výchozí konstruktor. |

### <a name="assignment-operators"></a>Operátory přiřazení

| Name (Název)  |  Syntaxe |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Operátory přetypování

| Name (Název)              |  Syntaxe |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| podepsaný znak       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| nepodepsané __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| nepodepsané __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| nepodepsané __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>Operátory porovnání

| Name (Název)  |  Syntaxe |
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

| Name (Název)  |  Syntaxe |
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

| Name (Název)     |  Syntaxe |
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

Třída `SafeInt` chrání před přetečení celé číslo v matematických operacích. Zvažte například přidání dvou 8bitových celá čísla: jeden má hodnotu 200 a druhý má hodnotu 100. Správná matematická operace by byla 200 + 100 = 300. Z důvodu limitu 8bitového celého čísla však dojde ke ztrátě horního bitu a výsledkem je kompilátor 44 (300 - 2<sup>8).</sup> Každá operace, která závisí na této matematické rovnici, bude generovat neočekávané chování.

Třída `SafeInt` zkontroluje, zda dojde k aritmetickému přetečení nebo zda se kód pokusí vydělit nulou. V obou případech třída volá obslužnou rutinu chyby upozornit program potenciální problém.

Tato třída také umožňuje porovnat dva různé typy celých čísel, pokud se jedná `SafeInt` o objekty. Obvykle při porovnání, musíte nejprve převést čísla na stejný typ. Přetypování jednoho čísla na jiný typ často vyžaduje kontroly, aby se ujistil, že nedojde ke ztrátě dat.

V tabulce Operátory v tomto tématu jsou `SafeInt` uvedeny matematické a porovnávací operátory podporované třídou. Většina matematických `SafeInt` operátorů `T`vrací objekt typu .

Srovnávací operace `SafeInt` mezi a integrální typ lze provádět v obou směrech. Například oba `SafeInt<int>(x) < y` `y> SafeInt<int>(x)` a jsou platné a vrátí stejný výsledek.

Mnoho binárních operátorů nepodporuje použití dvou různých `SafeInt` typů. Jedním z příkladů `&` je operátor. `SafeInt<T, E> & int`je podporován, `SafeInt<T, E> & SafeInt<U, E>` ale není. V druhém příkladu kompilátor neví, jaký typ parametru vrátit. Jedním z řešení tohoto problému je přetypovat druhý parametr zpět na základní typ. Pomocí stejných parametrů to lze provést `SafeInt<T, E> & (U)SafeInt<U, E>`pomocí aplikace .

> [!NOTE]
> Pro všechny bitové operace by měly mít dva různé parametry stejnou velikost. Pokud se velikosti liší, kompilátor vyvolá výjimku [ASSERT.](../mfc/reference/diagnostic-services.md#assert) Výsledky této operace nelze zaručit, že budou přesné. Chcete-li tento problém vyřešit, přetypovat menší parametr, dokud je stejná velikost jako větší parametr.

Pro operátory shift posunvíce bitů, než existují pro typ šablony vyvolá výjimku ASSERT. To nebude mít žádný vliv v režimu vydání. Míchání dvou typů parametrů SafeInt je možné pro operátory směny, protože návratový typ je stejný jako původní typ. Číslo na pravé straně operátoru označuje pouze počet bitů, které mají být posunuty.

Při provádění logické porovnání s Objekt SafeInt, porovnání je přísně aritmetické. Zvažte například tyto výrazy:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

První příkaz se překládá na **hodnotu**true `false`, ale druhý příkaz se překládá na . Bitové negace 0 je 0xFFFFFFFF. Ve druhém příkazu výchozí operátor porovnání porovná 0xFFFFFFFF na 0xFFFFFFFF a považuje je za stejné. Operátor porovnání pro `SafeInt` třídu si uvědomí, že druhý parametr je záporný vzhledem k tomu, že první parametr není podepsán. Proto i když bit reprezentace `SafeInt` je totožný, logický operátor si uvědomí, že nepodepsané celé číslo je větší než -1.

Buďte opatrní při `SafeInt` použití třídy `?:` společně s ternární operátor. Zvažte následující řádek kódu.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Kompilátor jej převede na toto:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Pokud `flag` `false`je , kompilátor vyvolá výjimku namísto přiřazení `x`hodnoty -1 . Proto, aby se zabránilo toto chování, správný kód, který chcete použít, je následující řádek.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T`a `U` může být přiřazen logický typ, typ znaku nebo typ celého čísla. Typy celého čísla mohou být podepsané nebo nepodepsané a libovolná velikost od 8 bitů do 64 bitů.

> [!NOTE]
> Přestože `SafeInt` třída přijímá jakýkoli druh celéčíslo, provádí efektivněji s nepodepsané typy.

`E`je mechanismus zpracování `SafeInt` chyb, který používá. S knihovnou SafeInt jsou k dispozici dva mechanismy zpracování chyb. Výchozí zásada `SafeIntErrorPolicy_SafeIntException`je , která při výskytu chyby vyvolá [výjimku třídy SafeIntException.](../safeint/safeintexception-class.md) Další zásadou `SafeIntErrorPolicy_InvalidParameter`je , která zastaví program, pokud dojde k chybě.

Existují dvě možnosti přizpůsobení zásad chyb. První možností je nastavení `E` parametru při `SafeInt`vytváření . Tuto možnost použijte, pokud chcete změnit zásady `SafeInt`zpracování chyb pouze pro jednu možnost . Druhou možností je definovat _SAFEINT_DEFAULT_ERROR_POLICY, aby se vaše vlastní třída `SafeInt` zpracování chyb před zahrnutím knihovny. Tuto možnost použijte, pokud chcete změnit výchozí zásady zpracování `SafeInt` chyb pro všechny instance třídy v kódu.

> [!NOTE]
> Vlastní třída, která zpracovává chyby z knihovny SafeInt, by neměla vrátit ovládací prvek kódu, který volal obslužnou rutinu chyby. Po volání obslužné rutiny chyby nelze důvěřovat výsledku `SafeInt` operace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SafeInt`

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Obor názvů:** msl::nástroje

## <a name="safeintsafeint"></a><a name="safeint"></a>BezpečnéInt::SafeInt

Vytvoří `SafeInt` objekt.

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

*I*<br/>
[v] Hodnota pro nový `SafeInt` objekt. To musí být parametr typu T nebo U, v závislosti na konstruktoru.

*B*<br/>
[v] Logická hodnota pro `SafeInt` nový objekt.

*U*<br/>
[v] A `SafeInt` typu U. Nový `SafeInt` objekt bude mít stejnou hodnotu jako *u*, ale bude typu T.

U Typ dat uložených `SafeInt`v . Může se jedná o logický, znakový nebo celý typ. Pokud se jedná o typ celé číslo, může být podepsánnebo nepodepsaný a být mezi 8 a 64 bitů.

### <a name="remarks"></a>Poznámky

Vstupní parametr pro *konstruktor, i* nebo *u*, musí být logický, znakový nebo lýtkový typ. Pokud se jedná o jiný `SafeInt` typ parametru, třída volá [static_assert](../cpp/static-assert.md) k označení neplatného vstupního parametru.

Konstruktory, které používají `U` typ šablony, automaticky převedou `T`vstupní parametr na typ určený programem . Třída `SafeInt` převádí data bez ztráty dat. Hlásí obslužné rutině `E` chyby, `T` pokud nemůže převést data na typ bez ztráty dat.

Pokud vytvoříte `SafeInt` z logického parametru, je třeba hodnotu okamžitě inicializovat. Nelze vytvořit `SafeInt` pomocí kódu `SafeInt<bool> sb;`. To vygeneruje chybu kompilace.
