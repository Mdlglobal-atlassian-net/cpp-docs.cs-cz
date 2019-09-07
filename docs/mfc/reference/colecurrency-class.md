---
title: COleCurrency – třída
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: fc7c64ada1100b0fc0a51670de3e8ec04b141b04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741638"
---
# <a name="colecurrency-class"></a>COleCurrency – třída

Zapouzdřuje `CURRENCY` datový typ automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|`COleCurrency` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleCurrency::Format](#format)|Generuje formátovanou řetězcovou reprezentaci `COleCurrency` objektu.|
|[COleCurrency:: GetStatus](#getstatus)|Získá stav (platnost) tohoto `COleCurrency` objektu.|
|[COleCurrency::P arseCurrency](#parsecurrency)|Přečte hodnotu měny z řetězce a nastaví hodnotu `COleCurrency`.|
|[COleCurrency::SetCurrency](#setcurrency)|Nastaví hodnotu tohoto `COleCurrency` objektu.|
|[COleCurrency:: SetStatus](#setstatus)|Nastaví stav (platnost) pro tento `COleCurrency` objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|`COleCurrency` Zkopíruje hodnotu.|
|[operator +,-](#operator_plus_minus)|Přidá, odečte a změní znaménka `COleCurrency` hodnot.|
|[operator + =,-=](#operator_plus_minus_eq)|Přidá a odečte `COleCurrency` hodnotu z tohoto `COleCurrency` objektu.|
|[*/– operátor](#operator_star)|Škáluje `COleCurrency` hodnotu pomocí celočíselné hodnoty.|
|[operator * =,/=](#operator_star_div_eq)|Škáluje `COleCurrency` tuto hodnotu celočíselnou hodnotou.|
|[operátor < <](#operator_stream)|Vytvoří `COleCurrency` výstup hodnoty do `CArchive` nebo `CDumpContext`.|
|[operátor > >](#operator_stream)|Vstup objektu z `CArchive`. `COleCurrency`|
|[operátor CURRENCY](#operator_currency)|`COleCurrency` Převede hodnotu na měnu.|
|[operator = =, <, < = atd.](#colecurrency_relational_operators)|Porovná `COleCurrency` dvě hodnoty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Obsahuje základní měnu pro tento `COleCurrency` objekt.|
|[COleCurrency::m_status](#m_status)|Obsahuje stav tohoto `COleCurrency` objektu.|

## <a name="remarks"></a>Poznámky

`COleCurrency`nemá základní třídu.

MĚNA je implementována jako 8 bajtů, celočíselná hodnota 2 doplňku škálovaná hodnotou 10 000. To poskytuje číslo s pevnou desetinnou čárkou s 15 číslicemi nalevo od desetinné čárky a 4 číslicemi vpravo. Datový typ měna je velmi užitečný pro výpočty zahrnující peníze nebo pro výpočty s pevnou desetinnou čárkou, kde je přesnost důležitá. Je jedním z možných typů pro `VARIANT` datový typ automatizace OLE.

`COleCurrency`také implementuje některé základní aritmetické operace typu s pevnou desetinnou čárkou. Byly vybrány podporované operace pro řízení chyb zaokrouhlení, ke kterým dochází při výpočtech s pevnou desetinnou čárkou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleCurrency`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="colecurrency"></a>COleCurrency::COleCurrency

`COleCurrency` Vytvoří objekt.

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*cySrc*<br/>
Hodnota měny, která se má zkopírovat do nového `COleCurrency` objektu

*curSrc*<br/>
Existující `COleCurrency` objekt, který má být zkopírován do nového `COleCurrency` objektu.

*varSrc*<br/>
Existující `VARIANT` datová struktura ( `COleVariant` pravděpodobně objekt), která má být převedena na hodnotu měny (VT_CY) a zkopírována do nového `COleCurrency` objektu.

*nUnits*, *nFractionalUnits* značí jednotky a zlomkovou část (v 1/10000) hodnoty, které mají být zkopírovány do nového `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvoří nové `COleCurrency` objekty inicializované na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů. Pokud není uvedeno jinak, je stav nové `COleCurrency` položky nastavený na platná.

- COleCurrency () vytvoří `COleCurrency` objekt inicializovaný jako 0 (nula).

- COleCurrency (`cySrc`) vytvoří `COleCurrency` objekt z hodnoty [měny](/windows/win32/api/wtypes/ns-wtypes-cy~r1) .

- COleCurrency (`curSrc`) vytvoří `COleCurrency` objekt z existujícího `COleCurrency` objektu. Nový objekt má stejný stav jako zdrojový objekt.

- COleCurrency (`varSrc`) vytvoří `COleCurrency` objekt. Pokusí se převést strukturu [variant](/windows/win32/api/oaidl/ns-oaidl-variant) nebo `COleVariant` objekt na hodnotu Currency (VT_CY). Pokud je tento převod úspěšný, převedená hodnota se zkopíruje do nového `COleCurrency` objektu. Pokud není, hodnota `COleCurrency` objektu je nastavena na hodnotu nula (0) a jeho stav na neplatné.

- `COleCurrency(`nUnits`, `nFractionalUnits`) Constructs a `COleCurrency objekt ze zadaných číselných komponent. Pokud je absolutní hodnota zlomkové části větší než 10 000, provede se příslušná úprava jednotek. Všimněte si, že jednotky a zlomkové součásti jsou určeny pomocí podepsaných dlouhých hodnot.

Další informace naleznete v části [Měna](/windows/win32/api/wtypes/ns-wtypes-cy~r1) a [varianty](/windows/win32/api/oaidl/ns-oaidl-variant) v Windows SDK.

### <a name="example"></a>Příklad

Následující příklady znázorňují účinky nulového parametru a konstruktorů dvou parametrů:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="format"></a>COleCurrency:: Format

Zavolejte tuto členskou funkci pro vytvoření formátované reprezentace hodnoty měny.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Označuje příznaky pro nastavení národního prostředí. Pro měnu je relevantní jenom tento příznak:

- LOCALE_NOUSEROVERRIDE místo vlastního nastavení uživatele použít výchozí nastavení národního prostředí systému.

*lcid*<br/>
Označuje ID národního prostředí, které se má použít pro převod.

### <a name="return-value"></a>Návratová hodnota

A `CString` který obsahuje formátovanou hodnotu měny.

### <a name="remarks"></a>Poznámky

Formátuje hodnotu pomocí specifikací místního jazyka (ID národního prostředí). V vrácené hodnotě není zahrnutý symbol měny. Pokud je stav tohoto `COleCurrency` objektu null, vrácená hodnota je prázdný řetězec. Pokud je stav neplatný, vrácený řetězec je určen řetězcovým prostředkem IDS_INVALID_CURRENCY.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="getstatus"></a>COleCurrency:: GetStatus

Chcete-li získat stav (platnost) daného `COleCurrency` objektu, zavolejte tuto členskou funkci.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleCurrency` hodnoty.

### <a name="remarks"></a>Poznámky

Návratová hodnota je definována `CurrencyStatus` výčtovým typem, který je definován `COleCurrency` v rámci třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

  - `COleCurrency::valid`Označuje, že `COleCurrency` tento objekt je platný.

  - `COleCurrency::invalid`Indikuje, že `COleCurrency` tento objekt je neplatný. to znamená, že jeho hodnota může být nesprávná.

  - `COleCurrency::null`Označuje, že `COleCurrency` tento objekt má hodnotu null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

Stav `COleCurrency` objektu je neplatný v následujících případech:

- Je-li jeho hodnota nastavena z hodnoty typu `COleVariant` variant nebo hodnota, která nemohla být převedena na hodnotu měny.

- V případě, že došlo k přetečení nebo podtečení během operace aritmetického přiřazení, například `+=` nebo **\* =** .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na hodnotu neplatné pomocí funkci [SetStatus](#setstatus).

Další informace o operacích, které můžou nastavit stav na neplatné, najdete v následujících členských funkcích:

- [COleCurrency](#colecurrency)

- [operátor =](#operator_eq)

- [operátor + –](#operator_plus_minus)

- [operator + = a-= – operátor](#operator_plus_minus_eq)

- [*/– operátor](#operator_star)

- [operator * = a/=](#operator_star_div_eq)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="m_cur"></a>COleCurrency::m_cur

Základní struktura [měny](/windows/win32/api/wtypes/ns-wtypes-cy~r1) pro tento `COleCurrency` objekt.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Změna hodnoty ve `CURRENCY` struktuře, k níž se přistupovalo pomocí ukazatele vráceného touto funkcí, změní hodnotu `COleCurrency` tohoto objektu. Nemění stav tohoto `COleCurrency` objektu.

Další informace najdete v tématu o [měně](/windows/win32/api/wtypes/ns-wtypes-cy~r1) v Windows SDK.

##  <a name="m_status"></a>COleCurrency::m_status

Typ tohoto datového členu je výčtový typ `CurrencyStatus`, který je definován `COleCurrency` v rámci třídy.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Poznámky

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid`Označuje, že `COleCurrency` tento objekt je platný.

- `COleCurrency::invalid`Indikuje, že `COleCurrency` tento objekt je neplatný. to znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null`Označuje, že `COleCurrency` tento objekt má hodnotu null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

Stav `COleCurrency` objektu je neplatný v následujících případech:

- Je-li jeho hodnota nastavena z hodnoty typu `COleVariant` variant nebo hodnota, která nemohla být převedena na hodnotu měny.

- V případě, že došlo k přetečení nebo podtečení během operace aritmetického přiřazení, například `+=` nebo **\* =** .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na hodnotu neplatné pomocí funkci [SetStatus](#setstatus).

Další informace o operacích, které můžou nastavit stav na neplatné, najdete v následujících členských funkcích:

- [COleCurrency](#colecurrency)

- [operátor =](#operator_eq)

- [operator +,-](#operator_plus_minus)

- [operator + =,-=](#operator_plus_minus_eq)

- [*/– operátor](#operator_star)

- [operator * =,/=](#operator_star_div_eq)

> [!CAUTION]
>  Tento datový člen slouží k pokročilým programovacím situacím. Měli byste použít funkce [GetStatus](#getstatus) a [SetStatus](#setstatus)vložených členů. Další `SetStatus` upozornění týkající se explicitního nastavení tohoto datového člena najdete v tématu.

##  <a name="operator_eq"></a>COleCurrency:: operator =

Tyto přetížené operátory přiřazení zkopírují hodnotu zdrojové měny do tohoto `COleCurrency` objektu.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Poznámky

Následuje stručný popis každého operátoru:

- **operator = (** `cySrc` `COleCurrency` )`CURRENCY` hodnota je zkopírována do objektu a její stav je nastaven na hodnotu platné.

- **operator = (** `curSrc` **)** hodnota a stav operandu, existující `COleCurrency` objekt je zkopírován do tohoto `COleCurrency` objektu.

- **operator = (** *varSrc* **)** – operátor Je-li `VARIANT` převod hodnoty (nebo objektu [COleVariant](../../mfc/reference/colevariant-class.md) ) na měnu ( `VT_CY`) úspěšný, je převedená hodnota zkopírována do tohoto `COleCurrency` objektu a její stav je nastaven na hodnotu platné. Pokud převod není úspěšný, hodnota `COleCurrency` objektu je nastavena na 0 a jeho stav na neplatné.

Další informace naleznete v části [Měna](/windows/win32/api/wtypes/ns-wtypes-cy~r1) a [varianty](/windows/win32/api/oaidl/ns-oaidl-variant) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="operator_plus_minus"></a>COleCurrency:: operator +,-

Tyto operátory umožňují přidat a odečíst dvě `COleCurrency` hodnoty mezi sebou a a změnit znaménko `COleCurrency` hodnoty.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Poznámky

Pokud je jeden z operandů null, stav výsledné `COleCurrency` hodnoty je null.

Pokud dojde k přetečení aritmetické operace, výsledná `COleCurrency` hodnota je neplatná.

Pokud je operand neplatný a druhý není null, stav výsledné `COleCurrency` hodnoty je neplatný.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v části členské proměnné [m_status](#m_status) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="operator_plus_minus_eq"></a>COleCurrency:: operator + =,-=

Umožňuje přidat a odečíst `COleCurrency` hodnotu z a do tohoto `COleCurrency` objektu.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Poznámky

Pokud je jeden z operandů null, je stav tohoto `COleCurrency` objektu nastaven na hodnotu null.

Pokud dojde k přetečení aritmetické operace, je stav tohoto `COleCurrency` objektu nastaven na hodnotu neplatné.

Pokud je jeden z operandů neplatný a druhý není null, stav tohoto `COleCurrency` objektu je nastaven na neplatné.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v části členské proměnné [m_status](#m_status) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="operator_star"></a>COleCurrency:: operator \* a/

Umožňuje škálovat `COleCurrency` hodnotu celočíselnou hodnotou.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Poznámky

Pokud je `COleCurrency` operand null, stav výsledné hodnoty je null. `COleCurrency`

Pokud aritmetické operace přetečení nebo podtečení, stav výsledné `COleCurrency` hodnoty je neplatný.

Pokud je `COleCurrency` operand neplatný, stav výsledné hodnoty je neplatný. `COleCurrency`

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v části členské proměnné [m_status](#m_status) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="operator_star_div_eq"></a>COleCurrency:: operator \*=,/=

Umožňuje škálovat tuto `COleCurrency` hodnotu celočíselnou hodnotou.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Poznámky

Pokud má `COleCurrency` operand hodnotu null, je stav tohoto objektu nastaven na hodnotu null. `COleCurrency`

Pokud dojde k přetečení aritmetické operace, je stav tohoto `COleCurrency` objektu nastaven na hodnotu neplatné.

Pokud je `COleCurrency` operand neplatný, je stav tohoto objektu nastaven na hodnotu neplatné. `COleCurrency`

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v části členské proměnné [m_status](#m_status) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="operator_stream"></a>COleCurrency:: operator &lt;, &lt;&gt;&gt;

Podporuje diagnostický dumping a ukládání do archivu.

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>Poznámky

Operátor pro extrakci ( **>>** ) podporuje načítání z archivu.

##  <a name="operator_currency"></a>COleCurrency:: operator – měna

Vrátí strukturu, jejíž hodnota je zkopírována z `COleCurrency` tohoto objektu. `CURRENCY`

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Poznámky

##  <a name="parsecurrency"></a>COleCurrency::P arseCurrency

Zavolejte tuto členskou funkci pro analýzu řetězce pro čtení hodnoty měny.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Parametry

*lpszCurrency*<br/>
Ukazatel na řetězec zakončený hodnotou null, který má být analyzován.

*dwFlags*<br/>
Označuje příznaky pro nastavení národního prostředí, možná následující příznak:

- LOCALE_NOUSEROVERRIDE místo vlastního nastavení uživatele použít výchozí nastavení národního prostředí systému.

*lcid*<br/>
Označuje ID národního prostředí, které se má použít pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl řetězec úspěšně převeden na hodnotu měny, jinak 0.

### <a name="remarks"></a>Poznámky

Používá specifikace místních jazyků (ID národního prostředí) pro význam nenumerických znaků ve zdrojovém řetězci.

Diskuzi o hodnotách ID národního prostředí najdete v tématu [Podpora více jazyků](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Pokud byl řetězec úspěšně převeden na hodnotu měny, hodnota tohoto `COleCurrency` objektu je nastavena na tuto hodnotu a její stav na platná.

Pokud řetězec nelze převést na hodnotu měny nebo pokud došlo k numerickému přetečení, je stav tohoto `COleCurrency` objektu neplatný.

Pokud převod řetězce se nezdařil z důvodu chyb přidělení paměti, tato funkce vyvolá výjimku [CMemoryException](../../mfc/reference/cmemoryexception-class.md). V jakémkoli jiném chybovém stavu Tato funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency_relational_operators"></a>Relační operátory COleCurrency

Porovná dvě hodnoty měny a vrátí nenulovou hodnotu, pokud je podmínka pravdivá. v opačném případě 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Návratová hodnota operací řazení **<** (, **\< =** , **>** , **>=** ) není definována, pokud je stav obou operandů null nebo neplatný. Operátory rovnosti ( `==`, `!=`) berou v úvahu stav operandů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="setcurrency"></a>COleCurrency::SetCurrency

Zavolejte tuto členskou funkci pro nastavení jednotek a zlomkové části tohoto `COleCurrency` objektu.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nUnits*, *nFractionalUnits* značí jednotky a zlomkovou část (v 1/10000) hodnoty, která se má zkopírovat do tohoto `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Je-li absolutní hodnota zlomkové části větší než 10 000, je provedena příslušná úprava jednotek, jak je znázorněno ve třetí části následujících příkladů.

Všimněte si, že jednotky a zlomkové součásti jsou určeny pomocí podepsaných dlouhých hodnot. Čtvrtý z následujících příkladů ukazuje, co se stane, když mají parametry jiné znaménko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="setstatus"></a>COleCurrency:: SetStatus

Chcete-li nastavit stav (platnosti) tohoto `COleCurrency` objektu, zavolejte tuto členskou funkci.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*status*<br/>
Nový stav tohoto `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Hodnota parametru *status* je definována `CurrencyStatus` výčtovým typem, který `COleCurrency` je definován v rámci třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid`Označuje, že `COleCurrency` tento objekt je platný.

- `COleCurrency::invalid`Indikuje, že `COleCurrency` tento objekt je neplatný. to znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null`Označuje, že `COleCurrency` tento objekt má hodnotu null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

> [!CAUTION]
>  Tato funkce je určena pro pokročilé programovací situace. Tato funkce nemění data v tomto objektu. Nejčastěji se použije k nastavení stavu na hodnotu null nebo neplatný. Všimněte si, že operátor přiřazení ( [Operator =](#operator_eq)) a [SetCurrency](#setcurrency) nastaví stav na objekt na základě zdrojových hodnot (y).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant – třída](../../mfc/reference/colevariant-class.md)
