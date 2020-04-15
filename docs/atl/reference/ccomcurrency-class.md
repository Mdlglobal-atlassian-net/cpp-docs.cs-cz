---
title: Třída CComCurrency
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
ms.openlocfilehash: 541944e03e9caf6cba15612cf9e7cbbd239555ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327947"
---
# <a name="ccomcurrency-class"></a>Třída CComCurrency

`CComCurrency`má metody a operátory pro vytváření a správu objektu CURRENCY.

## <a name="syntax"></a>Syntaxe

```
class CComCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomCurrency::CcomCurrency](#ccomcurrency)|Konstruktor pro `CComCurrency` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Vrátí adresu `m_currency` datového člena.|
|[CcomCurrency::Getfrakce](#getfraction)|Volání této metody vrátit zlomkové `CComCurrency` součásti objektu.|
|[CComCurrency::GetInteger](#getinteger)|Volání této metody vrátit celé číslo `CComCurrency` součást objektu.|
|[CcomCurrency::Zaoblené](#round)|Volání této metody `CComCurrency` zaokrouhlit objekt na nejbližší celočíselnou hodnotu.|
|[CcomCurrency::Setfraction](#setfraction)|Volání této metody nastavit zlomkové `CComCurrency` součásti objektu.|
|[CComCurrency::SetInteger](#setinteger)|Volání této metody nastavit komponentu celé `CComCurrency` číslo objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CComCurrency::operátor -](#operator_-)|Tento operátor se používá k `CComCurrency` provádění odčítání na objekt.|
|[CComCurrency::operátor !=](#operator_neq)|Porovná dva `CComCurrency` objekty pro nerovnost.|
|[CComCurrency::operátor *](#operator_star)|Tento operátor se používá k provádění `CComCurrency` násobení na objektu.|
|[CComCurrency::operátor *=](#operator_star_eq)|Tento operátor se používá k provádění `CComCurrency` násobení objektu a přiřadit mu výsledek.|
|[CComCurrency::operátor /](#operator_div)|Tento operátor se používá k `CComCurrency` provedení dělení na objekt.|
|[CComCurrency::operátor /=](#operator_div_eq)|Tento operátor se používá k `CComCurrency` provedení dělení na objekt a přiřadit mu výsledek.|
|[CComCurrency::operátor +](#operator_add)|Tento operátor se používá k `CComCurrency` provedení sčítání na objekt.|
|[CComCurrency::operátor +=](#operator_add_eq)|Tento operátor se používá k `CComCurrency` provedení sčítání na objekt a přiřadit výsledek aktuálníobjekt.|
|[CComCurrency::<operátora](#operator_lt)|Tento operátor porovná `CComCurrency` dva objekty k určení menší.|
|[CComCurrency::<operátora =](#operator_lt_eq)|Tento operátor porovná `CComCurrency` dva objekty k určení rovnosti nebo menší.|
|[CComCurrency::operátor =](#operator_eq)|Tento operátor přiřadí objekt u `CComCurrency` nové hodnoty.|
|[CComCurrency::operátor -=](#operator_-_eq)|Tento operátor se používá k `CComCurrency` provedení odčítání na objekt a přiřadit mu výsledek.|
|[CComCurrency::operátor ==](#operator_eq_eq)|Tento operátor porovnává `CComCurrency` dva objekty rovnosti.|
|[CComCurrency::>operátora](#operator_gt)|Tento operátor porovná `CComCurrency` dva objekty k určení větší.|
|[CComCurrency::>operátora =](#operator_gt_eq)|Tento operátor porovnává `CComCurrency` dva objekty k určení rovnosti nebo větší.|
|[CComCurrency::MĚNA operátora](#operator_currency)|Přetypová objekt MĚNA.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|Proměnná MĚNA vytvořená instancí třídy.|

## <a name="remarks"></a>Poznámky

`CComCurrency`je obálka datového typu MĚNA. MĚNA je implementována jako osmibajtová hodnota s doplňovací hodnotou dvou, která se mění o 10 000. To dává číslo s pevnou desetinnou čárkou s 15 číslicemi nalevo od desetinné čárky a 4 číslicemi vpravo. Datový typ MĚNA je velmi užitečný pro výpočty zahrnující peníze nebo pro výpočty s pevnou čárou, kde je důležitá přesnost.

Obálka `CComCurrency` implementuje aritmetické operace, operace přiřazení a porovnání pro tento typ pevného bodu. Podporované aplikace byly vybrány pro řízení chyb zaokrouhlení, ke kterým může dojít při výpočtech s pevnou špičkou.

Objekt `CComCurrency` poskytuje přístup k číslům na obou stranách desetinné čárky ve formě dvou součástí: celé součásti, která ukládá hodnotu vlevo od desetinné čárky, a zlomkové součásti, která ukládá hodnotu napravo od desetinné čárky. Zlomková součást je interně uložena jako celočíselná hodnota mezi -9999 (CY_MIN_FRACTION) a +9999 (CY_MAX_FRACTION). Metoda [CComCurrency::GetFraction](#getfraction) vrátí hodnotu zmenšenou koeficientem 10000 (CY_SCALE).

Při zadávání celé číslo a zlomkové součásti objektu, `CComCurrency` nezapomeňte, že zlomkové komponenty je číslo v rozsahu 0 až 9999. To je důležité při jednání s měnou, jako je americký dolar, který vyjadřuje částky pomocí pouze dvě významné číslice za desetinnou čárkou. I když poslední dvě číslice nejsou zobrazeny, je třeba je vzít v úvahu.

|Hodnota|Možná přiřazení CComCurrency|
|-----------|---------------------------------------|
|10,50 dolarů|CComCurrency(10 5000) *nebo* CComCurrency(10.50)|
|10,05 dolarů|CComCurrency(10 500) *nebo* CComCurrency(10.05)|

Hodnoty CY_MIN_FRACTION, CY_MAX_FRACTION a CY_SCALE jsou definovány v souboru atlcur.h.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcur.h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CcomCurrency::CcomCurrency

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
Proměnná typu MĚNA.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
Počáteční hodnota daná proměnné `m_currency`člena .

*Csrc*<br/>
Znak obsahující počáteční hodnotu přidělenou `m_currency`členské proměnné .

*nInteger*, *nFrakce*<br/>
Celé číslo a zlomkové složky počáteční peněžní hodnoty. Další informace naleznete v přehledu [ccomcurrency.](../../atl/reference/ccomcurrency-class.md)

*pDispSrc*<br/>
Ukazatel. `IDispatch`

*varSrc*<br/>
Proměnná typu VARIANT. Národní prostředí aktuálního vlákna se používá k provedení převodu.

*szSrc*<br/>
Řetězec Unicode nebo ANSI obsahující počáteční hodnotu. Národní prostředí aktuálního vlákna se používá k provedení převodu.

### <a name="remarks"></a>Poznámky

Konstruktor nastaví počáteční hodnotu [CComCurrency::m_currency](#m_currency)a přijímá širokou škálu datových typů, včetně celých čísel, řetězců, čísel `CComCurrency` s plovoucí desetinnou čárkou, proměnných MĚNY a dalších objektů. Pokud není k dispozici `m_currency` žádná hodnota, je nastavena na hodnotu 0.

V případě chyby, jako je například přetečení, konstruktory chybí prázdná `AtlThrow` specifikace výjimky **(throw()**) volání s HRESULT popisující chybu.

Při použití plovoucí desetinnou nebo dvojité hodnoty `CComCurrency(10.50)` přiřadit `CComCurrency(10,5000)` hodnotu, všimněte si, že je ekvivalentní a není `CComCurrency(10,50)`.

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr

Vrátí adresu `m_currency` datového člena.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu datového `m_currency` člena.

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CcomCurrency::Getfrakce

Volání této metody vrátit zlomkové `CComCurrency` součásti objektu.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí zlomkovou složku `m_currency` datového člena.

### <a name="remarks"></a>Poznámky

Zlomková součást je čtyřmístná celočíselná hodnota mezi -9999 (CY_MIN_FRACTION) a +9999 (CY_MAX_FRACTION). `GetFraction`vrátí tuto hodnotu o velikosti 10000 (CY_SCALE). Hodnoty CY_MIN_FRACTION, CY_MAX_FRACTION a CY_SCALE jsou definovány v souboru atlcur.h.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CComCurrency::GetInteger

Volání této metody získat celé číslo `CComCurrency` součást objektu.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celou komponentu datového `m_currency` prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CComCurrency::m_currency

Datový člen MĚNY.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Poznámky

Tento člen obsahuje měnu přistupovat a manipulovat pomocí metody této třídy.

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CComCurrency::operátor -

Tento operátor se používá k `CComCurrency` provádění odčítání na objekt.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt. `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek odčítání. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CComCurrency::operátor !=

Tento operátor porovnává dva objekty pro nerovnost.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt, `CComCurrency` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se porovnávaná položka nerovná objektu. `CComCurrency` jinak NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CComCurrency::operátor *

Tento operátor se používá k provádění `CComCurrency` násobení na objektu.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Multiplikátor.

*Měna*<br/>
Objekt `CComCurrency` použitý jako násobitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek násobení. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CComCurrency::operátor\*=

Tento operátor se používá k provádění `CComCurrency` násobení objektu a přiřadit mu výsledek.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Multiplikátor.

*Měna*<br/>
Objekt `CComCurrency` použitý jako násobitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CComCurrency::operátor /

Tento operátor se používá k `CComCurrency` provedení dělení na objekt.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dělitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek dělení. Pokud je dělitel 0, dojde k selhání neuplatnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CComCurrency::operátor /=

Tento operátor se používá k `CComCurrency` provedení dělení na objekt a přiřadit mu výsledek.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parametry

*nOperand*<br/>
Dělitel.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. Pokud je dělitel 0, dojde k selhání neuplatnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CComCurrency::operátor +

Tento operátor se používá k `CComCurrency` provedení sčítání na objekt.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt, `CComCurrency` který má být přidán do původního objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CComCurrency` objekt představující výsledek přidání. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CComCurrency::operátor +=

Tento operátor se používá k `CComCurrency` provedení sčítání na objekt a přiřadit výsledek aktuálníobjekt.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CComCurrency::operátor&lt;

Tento operátor porovná `CComCurrency` dva objekty k určení menší.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt. `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší než druhý, jinak NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CComCurrency::operátor&lt;=

Tento operátor porovná `CComCurrency` dva objekty k určení rovnosti nebo menší.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt. `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší nebo roven druhému, jinak NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CComCurrency::operátor =

Tento operátor přiřadí objekt u `CComCurrency` nové hodnoty.

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
Objekt. `CComCurrency`

*cySrc*<br/>
Proměnná typu MĚNA.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Číselná hodnota, která `CComCurrency` má být přiřazena objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CComCurrency::operátor -=

Tento operátor se používá k `CComCurrency` provedení odčítání na objekt a přiřadit mu výsledek.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt. `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CComCurrency` objekt. V případě chyby, jako je například přetečení, tento operátor volá `AtlThrow` s HRESULT popisující chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CComCurrency::operátor ==

Tento operátor porovnává `CComCurrency` dva objekty rovnosti.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt `CComCurrency` porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou `m_currency` objekty stejné (tj. datové členy, celé i zlomkové, v obou objektech mají stejnou hodnotu), JINAK NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CComCurrency::operátor&gt;

Tento operátor porovná `CComCurrency` dva objekty k určení větší.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt. `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt větší než druhý, JINAK NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CComCurrency::operátor&gt;=

Tento operátor porovnává `CComCurrency` dva objekty k určení rovnosti nebo větší.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parametry

*Měna*<br/>
Objekt. `CComCurrency`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt větší nebo roven druhému, jinak NEPRAVDA.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CComCurrency::MĚNA operátora

Tyto operátory se `CComCurrency` používají k přetypovat objekt do datového typu CURRENCY.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na objekt CURRENCY.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CcomCurrency::Zaoblené

Volání této metody zaokrouhlit měnu na zadaný počet desetinných míst.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parametry

*nDecimals*<br/>
Počet číslic, na `m_currency` které budou zaokrouhleny, v rozsahu 0 až 4.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CcomCurrency::Setfraction

Volání této metody nastavit zlomkové `CComCurrency` součásti objektu.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parametry

*nZlomek*<br/>
Hodnota, která má být přiřazena `m_currency` zlomkové součásti datového člena. Znaménko zlomkové součásti se musí shodovat s celočíselnou komponentou a hodnota musí být v rozsahu -9999 (CY_MIN_FRACTION) až +9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CComCurrency::SetInteger

Volání této metody nastavit komponentu celé `CComCurrency` číslo objektu.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parametry

*nInteger*<br/>
Hodnota, která má být přiřazena k `m_currency` celé součásti datového prvku. Znaménko celé součásti musí odpovídat znaménko existující zlomkové součásti.

*nInteger* musí být v rozsahu CY_MIN_INTEGER do CY_MAX_INTEGER včetně. Tyto hodnoty jsou definovány v souboru atlcur.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Viz také

[COleCurrency – třída](../../mfc/reference/colecurrency-class.md)<br/>
[Měny](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
