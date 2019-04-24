---
title: Ccomcurrency – třída
ms.date: 11/04/2016
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: b2c07bc9c0b1e96f34798b20207dc0eb0362e534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246418"
---
# <a name="ccomcurrency-class"></a>Ccomcurrency – třída

`CComCurrency` obsahuje metody a operátory k vytváření a správě objekt měny.

## <a name="syntax"></a>Syntaxe

```
class CComCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|Konstruktor pro `CComCurrency` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Vrátí adresu `m_currency` datový člen.|
|[CComCurrency::GetFraction](#getfraction)|Voláním této metody vrátí desetinné složku `CComCurrency` objektu.|
|[CComCurrency::GetInteger](#getinteger)|Voláním této metody vrátí celočíselné složku `CComCurrency` objektu.|
|[CComCurrency::Round](#round)|Voláním této metody lze zaokrouhlit `CComCurrency` objektu na nejbližší celočíselnou hodnotu.|
|[CComCurrency::SetFraction](#setfraction)|Voláním této metody nastavte desetinné součást `CComCurrency` objektu.|
|[CComCurrency::SetInteger](#setinteger)|Voláním této metody nastavte součást celé číslo `CComCurrency` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComCurrency::operator-](#operator_-)|Tento operátor se používá k provedení odečtení na `CComCurrency` objektu.|
|[CComCurrency::operator! =](#operator_neq)|Porovná dva `CComCurrency` objekty nerovnost.|
|[CComCurrency::operator *](#operator_star)|Tento operátor se používá k provedení násobení na `CComCurrency` objektu.|
|[CComCurrency::operator * =](#operator_star_eq)|Tento operátor se používá k provedení násobení na `CComCurrency` objekt a přiřaďte ho výsledek.|
|[CComCurrency::operator /](#operator_div)|Tento operátor se používá k provedení dělení na `CComCurrency` objektu.|
|[CComCurrency::operator / =](#operator_div_eq)|Tento operátor se používá k provedení dělení na `CComCurrency` objekt a přiřaďte ho výsledek.|
|[CComCurrency::operator +](#operator_add)|Tento operátor se používá k provedení sčítání na `CComCurrency` objektu.|
|[CComCurrency::operator +=](#operator_add_eq)|Tento operátor se používá k provedení sčítání na `CComCurrency` objektu a výsledek přiřaďte do aktuálního objektu.|
|[CComCurrency::operator <](#operator_lt)|Tento operátor porovná dva `CComCurrency` objekty k určení menší než.|
|[CComCurrency::operator < =](#operator_lt_eq)|Tento operátor porovná dva `CComCurrency` objekty k určení rovnosti, nebo menší.|
|[CComCurrency::operator =](#operator_eq)|Tento operátor přiřadí `CComCurrency` objektu na novou hodnotu.|
|[CComCurrency::operator-=](#operator_-_eq)|Tento operátor se používá k provedení odečtení na `CComCurrency` objekt a přiřaďte ho výsledek.|
|[CComCurrency::operator ==](#operator_eq_eq)|Tento operátor porovná dva `CComCurrency` objekty pro rovnost.|
|[CComCurrency::operator >](#operator_gt)|Tento operátor porovná dva `CComCurrency` objekty k určení větší.|
|[CComCurrency::operator > =](#operator_gt_eq)|Tento operátor porovná dva `CComCurrency` objekty k určení rovnosti, nebo větší.|
|[CComCurrency::operator měny](#operator_currency)|Přetypuje objekt měny.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Proměnná měny vytvořil instanci třídy.|

## <a name="remarks"></a>Poznámky

`CComCurrency` představuje obálku pro datový typ MĚNA. MĚNY je implementovaný jako celočíselnou hodnotu 8bajtový dvojkového doplňku měřítkem řídit 10 000. Díky tomu číslo s pevnou desetinnou čárkou s 15 číslic nalevo od desetinné čárky a 4 číslice vpravo. Datový typ MĚNA. je velmi užitečné pro peněžních výpočtů nebo pro všechny výpočty s pevnou desetinnou čárkou, kdy přesnost je důležité.

`CComCurrency` Obálky implementuje operace aritmetické, přiřazení a porovnání tohoto typu s pevnou desetinnou čárkou. Podporované aplikace byly vybrány pro řízení zaokrouhlovací chyby, které se můžou objevit během výpočty s pevnou desetinnou čárkou.

`CComCurrency` Objekt poskytuje přístup k čísla na obou stranách desetinné čárky ve formě dvě součásti: jako součást celé číslo, který ukládá hodnotu nalevo od desetinné čárky a zlomkové komponenta, která ukládá hodnotu napravo desetinné čárky. Desetinné komponenty je interně uložené jako celočíselnou hodnotu mezi -9999 (CY_MIN_FRACTION) a +9999 (CY_MAX_FRACTION). Metoda [CComCurrency::GetFraction](#getfraction) vrací hodnotu měřítkem řídit 10000 (CY_SCALE).

Při zadávání celé číslo a komponenty zlomku z `CComCurrency` objektu, mějte na paměti, že je součást desetinné číslo v rozsahu 0 až 9 999. To je důležité, když se zabývají měny, jako je AMERICKÝ dolar, která vyjadřuje částky s použitím pouze dvě platné číslice za desetinnou čárkou. I když nejsou zobrazeny poslední dvě číslice, musíte vzít do úvahy.

|Hodnota|Je to možné ccomcurrency – přiřazení|
|-----------|---------------------------------------|
|$10.50|CComCurrency(10,5000) *nebo* CComCurrency(10.50)|
|$10.05|CComCurrency(10,500) *nebo* CComCurrency(10.05)|

Hodnoty CY_MIN_FRACTION CY_MAX_FRACTION a CY_SCALE jsou definovány v atlcur.h.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcur.h

##  <a name="ccomcurrency"></a>  CComCurrency::CComCurrency

Konstruktor

```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);
CComCurrency(USHORT usSrc);
CComCurrency(CHAR cSrc);
CComCurrency(DOUBLE dSrc);
CComCurrency(FLOAT fSrc);
CComCurrency(LONG lSrc);
CComCurrency(SHORT sSrc);
CComCurrency(BYTE bSrc);
CComCurrency(LONGLONG nInteger, SHORT nFraction);
explicit CComCurrency(LPDISPATCH pDispSrc);
explicit CComCurrency(const VARIANT& varSrc);
explicit CComCurrency(LPCWSTR szSrc);
explicit CComCurrency(LPCSTR szSrc);
```

### <a name="parameters"></a>Parametry

*curSrc*<br/>
Existující objekt `CComCurrency`.

*cySrc*<br/>
Proměnné typu MĚNA.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Počáteční hodnota předaná do proměnné člena `m_currency`.

*cSrc*<br/>
Znak obsahující počáteční hodnota předaná do proměnné člena `m_currency`.

*nInteger*, *nFraction*<br/>
Celé číslo a komponenty zlomku počáteční peněžní hodnoty. Zobrazit [ccomcurrency –](../../atl/reference/ccomcurrency-class.md) přehled pro další informace.

*pDispSrc*<br/>
`IDispatch` Ukazatele.

*varSrc*<br/>
Proměnné typu VARIANT. Národní prostředí aktuálního vlákna se používá k provedení převodu.

*szSrc*<br/>
Řetězec Unicode nebo ANSI obsahující počáteční hodnota. Národní prostředí aktuálního vlákna se používá k provedení převodu.

### <a name="remarks"></a>Poznámky

Konstruktor nastaví počáteční hodnotu [CComCurrency::m_currency](#m_currency)a přijímá širokou škálu datových typů včetně celá čísla, řetězce, čísla s plovoucí desetinnou čárkou, měny proměnné a další `CComCurrency` objekty. Pokud se nezadá žádná hodnota, `m_currency` je nastavena na hodnotu 0.

V případě chyby, jako je například přetečení, konstruktory chybí specifikaci výjimky prázdný (**throw()**) volání `AtlThrow` s chybou HRESULT popisující chybu.

Při použití hodnoty s plovoucí desetinnou čárkou nebo double pro přiřazení hodnoty, Všimněte si, že `CComCurrency(10.50)` je ekvivalentní `CComCurrency(10,5000)` a ne `CComCurrency(10,50)`.

##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr

Vrátí adresu `m_currency` datový člen.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu `m_currency` datový člen

##  <a name="getfraction"></a>  CComCurrency::GetFraction

Voláním této metody vrátí desetinné složku `CComCurrency` objektu.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí komponentu desetinné hodnoty `m_currency` datový člen.

### <a name="remarks"></a>Poznámky

Desetinné komponenta je 4 číslice celočíselnou hodnotu mezi -9999 (CY_MIN_FRACTION) a +9999 (CY_MAX_FRACTION). `GetFraction` Vrátí tuto hodnotu škálovat podle 10000 (CY_SCALE). Hodnoty CY_MIN_FRACTION CY_MAX_FRACTION a CY_SCALE jsou definovány v atlcur.h.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

##  <a name="getinteger"></a>  CComCurrency::GetInteger

Volání této metody k získání celého čísla součást `CComCurrency` objektu.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí komponentu celého čísla `m_currency` datový člen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

##  <a name="m_currency"></a>  CComCurrency::m_currency

Datový člen měny.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Poznámky

Tento člen obsahuje měny přistupovat a pracovat s nimi metody této třídy.

##  <a name="operator_-"></a>  CComCurrency::operator-

Tento operátor se používá k provedení odečtení na `CComCurrency` objektu.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek odčítání. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

##  <a name="operator_neq"></a>  CComCurrency::operator! =

Tento operátor porovná dva objekty nerovnost.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
`CComCurrency` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud položka, který se porovnává se nerovná `CComCurrency` objektu; jinak hodnota FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

##  <a name="operator_star"></a>  CComCurrency::operator *

Tento operátor se používá k provedení násobení na `CComCurrency` objektu.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Násobitel.

*Měna*<br/>
`CComCurrency` Objektu se používá jako násobitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek násobení. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

##  <a name="operator_star_eq"></a>  CComCurrency::operator \*=

Tento operátor se používá k provedení násobení na `CComCurrency` objekt a přiřaďte ho výsledek.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Násobitel.

*Měna*<br/>
`CComCurrency` Objektu se používá jako násobitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

##  <a name="operator_div"></a>  CComCurrency::operator /

Tento operátor se používá k provedení dělení na `CComCurrency` objektu.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dělitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt reprezentuje výsledek dělení. Pokud dělitel je 0, dojde k chybě vyhodnocení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

##  <a name="operator_div_eq"></a>  CComCurrency::operator / =

Tento operátor se používá k provedení dělení na `CComCurrency` objekt a přiřaďte ho výsledek.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dělitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objektu. Pokud dělitel je 0, dojde k chybě vyhodnocení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

##  <a name="operator_add"></a>  CComCurrency::operator +

Tento operátor se používá k provedení sčítání na `CComCurrency` objektu.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
`CComCurrency` Objekt přidán na původní objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek součtu. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

##  <a name="operator_add_eq"></a>  CComCurrency::operator +=

Tento operátor se používá k provedení sčítání na `CComCurrency` objektu a výsledek přiřaďte do aktuálního objektu.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
`CComCurrency` Objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

##  <a name="operator_lt"></a>  CComCurrency::operator &lt;

Tento operátor porovná dva `CComCurrency` objekty k určení menší než.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt menší než druhé, FALSE v opačném případě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

##  <a name="operator_lt_eq"></a>  CComCurrency::operator &lt;=

Tento operátor porovná dva `CComCurrency` objekty k určení rovnosti, nebo menší.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud je první objekt menší než nebo roven druhému, FALSE v opačném případě vrátí hodnotu TRUE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

##  <a name="operator_eq"></a>  CComCurrency::operator =

Tento operátor přiřadí `CComCurrency` objektu na novou hodnotu.

```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```

### <a name="parameters"></a>Parametry

*curSrc*<br/>
A `CComCurrency` objektu.

*cySrc*<br/>
Proměnné typu MĚNA.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Číselná hodnota pro přiřazení `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

##  <a name="operator_-_eq"></a>  CComCurrency::operator-=

Tento operátor se používá k provedení odečtení na `CComCurrency` objekt a přiřaďte ho výsledek.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je například přetečení, volá tento operátor `AtlThrow` s chybou HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

##  <a name="operator_eq_eq"></a>  CComCurrency::operator ==

Tento operátor porovná dva `CComCurrency` objekty pro rovnost.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
`CComCurrency` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se objekty rovnají (to znamená `m_currency` datové členy, obě celé číslo a desetinných v obou objekty mají stejnou hodnotu), FALSE, jinak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

##  <a name="operator_gt"></a>  CComCurrency::operator &gt;

Tento operátor porovná dva `CComCurrency` objekty k určení větší.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud je první objekt větší než druhý FALSE v opačném případě vrátí hodnotu TRUE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

##  <a name="operator_gt_eq"></a>  CComCurrency::operator &gt;=

Tento operátor porovná dva `CComCurrency` objekty k určení rovnosti, nebo větší.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud je první objekt větší než nebo roven druhému FALSE v opačném případě vrátí hodnotu TRUE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

##  <a name="operator_currency"></a>  CComCurrency::operator měny

Tyto operátory lze přetypovat `CComCurrency` objektu na datový typ MĚNA.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na objekt měny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

##  <a name="round"></a>  CComCurrency::Round

Voláním této metody lze zaokrouhlit měny zadaný počet desetinných míst.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parametry

*nDecimals*<br/>
Počet číslic, na který `m_currency` zaokrouhlen v rozsahu 0 až 4.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

##  <a name="setfraction"></a>  CComCurrency::SetFraction

Voláním této metody nastavte desetinné součást `CComCurrency` objektu.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parametry

*nFraction*<br/>
Hodnota má být přiřazena k desetinné součást `m_currency` datový člen. Znak desetinné součásti musí stejný jako součást celé číslo a hodnota musí být v rozsahu -9999 (CY_MIN_FRACTION) +9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

##  <a name="setinteger"></a>  CComCurrency::SetInteger

Voláním této metody nastavte součást celé číslo `CComCurrency` objektu.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parametry

*nInteger*<br/>
Hodnota, která má být přiřazená součást celé číslo `m_currency` datový člen. Znaménko celé číslo součásti musí odpovídat znaménko existující komponentu desetinné části.

*nInteger* musí být v rozsahu CY_MIN_INTEGER k CY_MAX_INTEGER (včetně). Tyto hodnoty jsou definovány v atlcur.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Viz také:

[COleCurrency – třída](../../mfc/reference/colecurrency-class.md)<br/>
[MĚNY](/windows/desktop/api/wtypes/ns-wtypes-tagcy)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
