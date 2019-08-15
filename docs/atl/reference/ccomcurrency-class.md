---
title: CComCurrency – třída
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
ms.openlocfilehash: 11463b7113876abdf0743b9f8c7df373fadd99ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497292"
---
# <a name="ccomcurrency-class"></a>CComCurrency – třída

`CComCurrency`obsahuje metody a operátory pro vytváření a správu objektu měny.

## <a name="syntax"></a>Syntaxe

```
class CComCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|Konstruktor `CComCurrency` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Vrátí adresu `m_currency` datového členu.|
|[CComCurrency:: getzlomek](#getfraction)|Voláním této metody vrátíte zlomkovou komponentu `CComCurrency` objektu.|
|[CComCurrency:: GetInteger](#getinteger)|Voláním této metody vrátíte celočíselnou komponentu `CComCurrency` objektu.|
|[CComCurrency:: Round](#round)|Voláním této metody můžete zaokrouhlit `CComCurrency` objekt na nejbližší celočíselnou hodnotu.|
|[CComCurrency::SetFraction](#setfraction)|Voláním této metody nastavíte zlomkovou komponentu `CComCurrency` objektu.|
|[CComCurrency::SetInteger](#setinteger)|Voláním této metody nastavíte celočíselnou komponentu `CComCurrency` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CComCurrency:: operator-](#operator_-)|Tento operátor slouží k provádění odčítání u `CComCurrency` objektu.|
|[CComCurrency:: operator! =](#operator_neq)|Porovná `CComCurrency` dva objekty pro nerovnost.|
|[CComCurrency:: operator * – operátor](#operator_star)|Tento operátor slouží k provádění násobení u `CComCurrency` objektu.|
|[CComCurrency:: operator * =](#operator_star_eq)|Tento operátor slouží k provádění násobení u `CComCurrency` objektu a přiřazení výsledku.|
|[CComCurrency:: operator/](#operator_div)|Tento operátor slouží k dělení `CComCurrency` objektů.|
|[CComCurrency:: operator/=](#operator_div_eq)|Tento operátor slouží k dělení `CComCurrency` objektu a přiřazení výsledku.|
|[CComCurrency:: operator + – operátor](#operator_add)|Tento operátor slouží k přidání `CComCurrency` objektu.|
|[CComCurrency:: operator + =](#operator_add_eq)|Tento operátor slouží k doplnění `CComCurrency` objektu a přiřazení výsledku k aktuálnímu objektu.|
|[CComCurrency:: operator <](#operator_lt)|Tento operátor porovná `CComCurrency` dva objekty a určí menší.|
|[CComCurrency:: operator < =](#operator_lt_eq)|Tento operátor porovná `CComCurrency` dva objekty a určí rovnost nebo menší.|
|[CComCurrency:: operator =](#operator_eq)|Tento operátor přiřadí `CComCurrency` objekt nové hodnotě.|
|[CComCurrency:: operator-=](#operator_-_eq)|Tento operátor slouží k provedení odčítání u `CComCurrency` objektu a přiřazení výsledku.|
|[CComCurrency:: operator = = – operátor](#operator_eq_eq)|Tento operátor porovná `CComCurrency` dva objekty pro rovnost.|
|[CComCurrency:: operator >](#operator_gt)|Tento operátor porovná `CComCurrency` dva objekty a určí větší.|
|[CComCurrency:: operator > =](#operator_gt_eq)|Tento operátor porovná `CComCurrency` dva objekty a určí rovnost nebo větší.|
|[CComCurrency:: operator – měna](#operator_currency)|Přetypování objektu CURRENCY.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Proměnná měny vytvořená vaší instancí třídy.|

## <a name="remarks"></a>Poznámky

`CComCurrency`je obálka pro datový typ CURRENCY. MĚNA je implementována jako hodnota dvojkového doplňku s hodnotou příplatku, která je zvětšena o 10 000. To poskytuje číslo s pevnou desetinnou čárkou s 15 číslicemi nalevo od desetinné čárky a 4 číslicemi vpravo. Datový typ měna je velmi užitečný pro výpočty zahrnující peníze nebo pro výpočty s pevnou desetinnou čárkou, kde je přesnost důležitá.

`CComCurrency` Obálka implementuje operace aritmetického, přiřazení a porovnání pro tento typ s pevnou desetinnou čárkou. Pro řízení chyb zaokrouhlování, ke kterým může dojít při výpočtech s pevnou desetinnou čárkou, byly vybrány podporované aplikace.

`CComCurrency` Objekt poskytuje přístup k číslům na obou stranách desetinné čárky ve formě dvou komponent: celočíselná komponenta, která ukládá hodnotu nalevo od desetinné čárky, a zlomkovou komponentu, která ukládá hodnotu napravo od desetinná čárka. Zlomková komponenta se ukládá interně jako celočíselná hodnota mezi-9999 (CY_MIN_FRACTION) a + 9999 (CY_MAX_FRACTION). Metoda [CComCurrency::](#getfraction) getzloma vrátí hodnotu škálované faktorem 10000 (CY_SCALE).

Při zadávání celočíselné a zlomkové komponenty `CComCurrency` objektu si pamatujte, že desetinná komponenta je číslo v rozsahu 0 až 9999. To je důležité při obchodování s měnou, jako je US dolar, která vyjadřuje částky za použití jenom dvou platných číslic za desetinnou čárkou. I když se poslední dvě číslice nezobrazí, musí se vzít v úvahu.

|Value|Možná přiřazení CComCurrency|
|-----------|---------------------------------------|
|$10.50|CComCurrency (10, 5000) *nebo* CComCurrency (10.50)|
|$10.05|CComCurrency (10500) *nebo* CComCurrency (10.05)|

Hodnoty CY_MIN_FRACTION, CY_MAX_FRACTION a CY_SCALE jsou definovány v atlcur. h.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcur. h

##  <a name="ccomcurrency"></a>CComCurrency::CComCurrency

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
Proměnná typu CURRENCY

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Počáteční hodnota poskytnutá členské proměnné `m_currency`.

*cSrc*<br/>
Znak obsahující počáteční hodnotu poskytnutou členské proměnné `m_currency`.

*nInteger*, *nFraction*<br/>
Celočíselná a zlomková součást počáteční peněžní hodnoty. Další informace najdete v tématu [CComCurrency](../../atl/reference/ccomcurrency-class.md) Overview.

*pDispSrc*<br/>
`IDispatch` Ukazatel.

*varSrc*<br/>
Proměnná typu VARIANT. Národní prostředí aktuálního vlákna slouží k provedení převodu.

*szSrc*<br/>
Řetězec Unicode nebo ANSI obsahující počáteční hodnotu. Národní prostředí aktuálního vlákna slouží k provedení převodu.

### <a name="remarks"></a>Poznámky

Konstruktor nastaví počáteční hodnotu [CComCurrency:: m_currency](#m_currency)a přijímá celou škálu datových typů, včetně celých čísel, řetězců, čísel s plovoucí desetinnou čárkou, proměnných měny a dalších `CComCurrency` objektů. Pokud není zadána žádná hodnota, `m_currency` je nastavena na hodnotu 0.

V případě chyby, jako je přetečení, konstruktory chybí prázdná specifikace výjimky (**throw ()** ) `AtlThrow` s hodnotou HRESULT popisující chybu.

Při použití hodnot s plovoucí desetinnou čárkou nebo Double k přiřazení hodnoty si `CComCurrency(10.50)` Všimněte, že `CComCurrency(10,5000)` je ekvivalentem a nikoli `CComCurrency(10,50)`.

##  <a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr

Vrátí adresu `m_currency` datového členu.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu `m_currency` datového členu.

##  <a name="getfraction"></a>CComCurrency:: getzlomek

Voláním této metody vrátíte zlomkovou komponentu `CComCurrency` objektu.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí zlomkovou komponentu `m_currency` datového členu.

### <a name="remarks"></a>Poznámky

Desetinná komponenta je celočíselná hodnota o hodnotě 4 číslice mezi-9999 (CY_MIN_FRACTION) a + 9999 (CY_MAX_FRACTION). `GetFraction`Vrátí tuto hodnotu škálované hodnotou 10000 (CY_SCALE). Hodnoty CY_MIN_FRACTION, CY_MAX_FRACTION a CY_SCALE jsou definovány v atlcur. h.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

##  <a name="getinteger"></a>CComCurrency:: GetInteger

Voláním této metody získáte celočíselnou komponentu `CComCurrency` objektu.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celočíselnou komponentu `m_currency` datového členu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

##  <a name="m_currency"></a>CComCurrency::m_currency

Datový člen měny.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Poznámky

Tento člen má k dispozici měnu a pracuje s metodami této třídy.

##  <a name="operator_-"></a>CComCurrency:: operator-

Tento operátor slouží k provádění odčítání u `CComCurrency` objektu.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

`CComCurrency` Vrátí objekt představující výsledek odčítání. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

##  <a name="operator_neq"></a>CComCurrency:: operator! =

Tento operátor Porovná dva objekty pro nerovnost.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
`CComCurrency` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka, která je porovnána `CComCurrency` , nerovná objektu; v opačném případě false.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

##  <a name="operator_star"></a>CComCurrency:: operator * – operátor

Tento operátor slouží k provádění násobení u `CComCurrency` objektu.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Násobitel.

*běžný*<br/>
`CComCurrency` Objekt použitý jako násobitel.

### <a name="return-value"></a>Návratová hodnota

`CComCurrency` Vrátí objekt představující výsledek násobení. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

##  <a name="operator_star_eq"></a>CComCurrency:: operator\*=

Tento operátor slouží k provádění násobení u `CComCurrency` objektu a přiřazení výsledku.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Násobitel.

*běžný*<br/>
`CComCurrency` Objekt použitý jako násobitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

##  <a name="operator_div"></a>CComCurrency:: operator/

Tento operátor slouží k dělení `CComCurrency` objektů.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dělitel.

### <a name="return-value"></a>Návratová hodnota

`CComCurrency` Vrátí objekt představující výsledek dělení. Pokud je dělitel 0, dojde k selhání kontrolního výrazu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

##  <a name="operator_div_eq"></a>CComCurrency:: operator/=

Tento operátor slouží k dělení `CComCurrency` objektu a přiřazení výsledku.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dělitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. Pokud je dělitel 0, dojde k selhání kontrolního výrazu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

##  <a name="operator_add"></a>CComCurrency:: operator + – operátor

Tento operátor slouží k přidání `CComCurrency` objektu.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
`CComCurrency` Objekt, který má být přidán do původního objektu.

### <a name="return-value"></a>Návratová hodnota

`CComCurrency` Vrátí objekt představující výsledek přidání. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

##  <a name="operator_add_eq"></a>CComCurrency:: operator + =

Tento operátor slouží k doplnění `CComCurrency` objektu a přiřazení výsledku k aktuálnímu objektu.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
`CComCurrency` Objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

##  <a name="operator_lt"></a>CComCurrency:: operator&lt;

Tento operátor porovná `CComCurrency` dva objekty a určí menší.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší než druhý, v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

##  <a name="operator_lt_eq"></a>CComCurrency:: operator&lt;=

Tento operátor porovná `CComCurrency` dva objekty a určí rovnost nebo menší.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší nebo roven druhému, v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

##  <a name="operator_eq"></a>CComCurrency:: operator =

Tento operátor přiřadí `CComCurrency` objekt nové hodnotě.

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
Proměnná typu CURRENCY

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Číselná hodnota, která má být přiřazena `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

##  <a name="operator_-_eq"></a>CComCurrency:: operator-=

Tento operátor slouží k provedení odčítání u `CComCurrency` objektu a přiřazení výsledku.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je přetečení, Tento operátor volá `AtlThrow` s hodnotou HRESULT, která popisuje chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

##  <a name="operator_eq_eq"></a>CComCurrency:: operator = = – operátor

Tento operátor porovná `CComCurrency` dva objekty pro rovnost.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
`CComCurrency` Objekt, který chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou objekty stejné (tj `m_currency` . datové členy, celé číslo i zlomky v obou objektech mají stejnou hodnotu), jinak false.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

##  <a name="operator_gt"></a>CComCurrency:: operator&gt;

Tento operátor porovná `CComCurrency` dva objekty a určí větší.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než druhý, v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

##  <a name="operator_gt_eq"></a>CComCurrency:: operator&gt;=

Tento operátor porovná `CComCurrency` dva objekty a určí rovnost nebo větší.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*běžný*<br/>
A `CComCurrency` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší nebo roven druhému, FALSE jinak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

##  <a name="operator_currency"></a>CComCurrency:: operator – měna

Tyto operátory slouží k přetypování `CComCurrency` objektu na datový typ Měna.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na objekt měny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

##  <a name="round"></a>CComCurrency:: Round

Zavolejte tuto metodu, pokud chcete zaokrouhlit měnu na zadaný počet desetinných míst.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parametry

*nDecimals*<br/>
Počet číslic, které `m_currency` budou zaokrouhleny, v rozsahu od 0 do 4.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

##  <a name="setfraction"></a>CComCurrency::SetFraction

Voláním této metody nastavíte zlomkovou komponentu `CComCurrency` objektu.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parametry

*nFraction*<br/>
Hodnota, která má být přiřazena k zlomkové komponentě `m_currency` datového člena. Znaménko zlomkové komponenty musí být stejné jako celočíselná komponenta a hodnota musí být v rozsahu od-9999 (CY_MIN_FRACTION) do + 9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

##  <a name="setinteger"></a>CComCurrency::SetInteger

Voláním této metody nastavíte celočíselnou komponentu `CComCurrency` objektu.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parametry

*nInteger*<br/>
Hodnota, která má být přiřazena celočíselné komponentě `m_currency` datového členu. Znaménko celočíselné komponenty se musí shodovat s znaménkem existující zlomkové komponenty.

*nInteger* musí být v rozsahu CY_MIN_INTEGER až CY_MAX_INTEGER včetně. Tyto hodnoty jsou definovány v atlcur. h.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Viz také:

[COleCurrency – třída](../../mfc/reference/colecurrency-class.md)<br/>
[MĚNĚ](/windows/win32/api/wtypes/ns-wtypes-cy)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
