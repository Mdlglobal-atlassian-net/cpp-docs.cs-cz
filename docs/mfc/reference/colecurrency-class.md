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
ms.openlocfilehash: 1e32d75599f51ba277180341df60762a02a82fe5
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150925"
---
# <a name="colecurrency-class"></a>COleCurrency – třída

Zapouzdřuje `CURRENCY` datový typ automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Vytvoří objekt `COleCurrency`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleCurrency:: Format](#format)|Generuje naformátovanou řetězcovou reprezentaci objektu `COleCurrency`.|
|[COleCurrency:: GetStatus](#getstatus)|Získá stav (platnost) tohoto objektu `COleCurrency`.|
|[COleCurrency::P arseCurrency](#parsecurrency)|Přečte hodnotu měny z řetězce a nastaví hodnotu `COleCurrency`.|
|[COleCurrency::SetCurrency](#setcurrency)|Nastaví hodnotu tohoto objektu `COleCurrency`.|
|[COleCurrency:: SetStatus](#setstatus)|Nastaví stav (platnost) pro tento objekt `COleCurrency`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje `COleCurrency`ou hodnotu.|
|[operator +,-](#operator_plus_minus)|Přidá, odečte a změní znaménka `COleCurrency` hodnot.|
|[operator + =,-=](#operator_plus_minus_eq)|Přidá a odečte `COleCurrency` hodnotu z tohoto objektu `COleCurrency`.|
|[*/– operátor](#operator_star)|Škáluje `COleCurrency` hodnotu podle celočíselné hodnoty.|
|[operator * =,/=](#operator_star_div_eq)|Škáluje tuto `COleCurrency` hodnotu pomocí celočíselné hodnoty.|
|[operátor < <](#operator_stream)|Vytvoří výstup `COleCurrency` hodnoty pro `CArchive` nebo `CDumpContext`.|
|[operátor > >](#operator_stream)|Vstupní objekt `COleCurrency` z `CArchive`.|
|[operátor CURRENCY](#operator_currency)|Převede hodnotu `COleCurrency` na měnu.|
|[operator = =, <, < = atd.](#colecurrency_relational_operators)|Porovná dvě `COleCurrency` hodnoty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleCurrency:: m_cur](#m_cur)|Obsahuje základní měnu pro tento objekt `COleCurrency`.|
|[COleCurrency:: m_status](#m_status)|Obsahuje stav tohoto objektu `COleCurrency`.|

## <a name="remarks"></a>Poznámky

`COleCurrency` nemá základní třídu.

MĚNA je implementována jako 8 bajtů, celočíselná hodnota 2 doplňku škálovaná hodnotou 10 000. To poskytuje číslo s pevnou desetinnou čárkou s 15 číslicemi nalevo od desetinné čárky a 4 číslicemi vpravo. Datový typ měna je velmi užitečný pro výpočty zahrnující peníze nebo pro výpočty s pevnou desetinnou čárkou, kde je přesnost důležitá. Je jedním z možných typů pro `VARIANT` datový typ pro automatizaci OLE.

`COleCurrency` také implementuje některé základní aritmetické operace typu s pevnou desetinnou čárkou. Byly vybrány podporované operace pro řízení chyb zaokrouhlení, ke kterým dochází při výpočtech s pevnou desetinnou čárkou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleCurrency`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency

Vytvoří objekt `COleCurrency`.

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
Hodnota měny, která se má zkopírovat do nového objektu `COleCurrency`

*curSrc*<br/>
Existující objekt `COleCurrency`, který se má zkopírovat do nového objektu `COleCurrency`

*varSrc*<br/>
Existující datová struktura `VARIANT` (případně objekt `COleVariant`), která má být převedena na hodnotu měny (VT_CY) a zkopírována do nového objektu `COleCurrency`.

*nUnits*, *nFractionalUnits* značí jednotky a zlomkovou část (v 1/10000) hodnoty, které mají být zkopírovány do nového objektu `COleCurrency`.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvoří nové objekty `COleCurrency` inicializované do zadané hodnoty. Následuje stručný popis každého z těchto konstruktorů. Není-li uvedeno jinak, je stav nové `COleCurrency` položky nastaven na hodnotu platný.

- COleCurrency () vytvoří objekt `COleCurrency` inicializovaný na hodnotu 0 (nula).

- COleCurrency (`cySrc`) vytvoří objekt `COleCurrency` z hodnoty [měny](/windows/win32/api/wtypes/ns-wtypes-cy~r1) .

- COleCurrency (`curSrc`) vytvoří objekt `COleCurrency` z existujícího objektu `COleCurrency`. Nový objekt má stejný stav jako zdrojový objekt.

- COleCurrency (`varSrc`) vytvoří objekt `COleCurrency`. Pokusí se převést strukturu [variant](/windows/win32/api/oaidl/ns-oaidl-variant) nebo objekt `COleVariant` na hodnotu měny (VT_CY). Je-li tento převod úspěšný, je převedená hodnota zkopírována do nového objektu `COleCurrency`. Pokud není, hodnota objektu `COleCurrency` je nastavena na hodnotu nula (0) a jeho stav na neplatné.

- COleCurrency (`nUnits`, `nFractionalUnits`) vytvoří objekt `COleCurrency` ze zadaných číselných komponent. Pokud je absolutní hodnota zlomkové části větší než 10 000, provede se příslušná úprava jednotek. Všimněte si, že jednotky a zlomkové součásti jsou určeny pomocí podepsaných dlouhých hodnot.

Další informace naleznete v části [Měna](/windows/win32/api/wtypes/ns-wtypes-cy~r1) a [varianty](/windows/win32/api/oaidl/ns-oaidl-variant) v Windows SDK.

### <a name="example"></a>Příklad

Následující příklady znázorňují účinky nulového parametru a konstruktorů dvou parametrů:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency:: Format

Zavolejte tuto členskou funkci pro vytvoření formátované reprezentace hodnoty měny.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Označuje příznaky pro nastavení národního prostředí. Pro měnu je relevantní jenom tento příznak:

- Místo vlastního nastavení uživatele LOCALE_NOUSEROVERRIDE použít výchozí nastavení národního prostředí systému.

*lcid*<br/>
Označuje ID národního prostředí, které se má použít pro převod.

### <a name="return-value"></a>Návratová hodnota

`CString`, který obsahuje formátovanou hodnotu měny.

### <a name="remarks"></a>Poznámky

Formátuje hodnotu pomocí specifikací místního jazyka (ID národního prostředí). V vrácené hodnotě není zahrnutý symbol měny. Pokud je stav tohoto objektu `COleCurrency` null, vrácená hodnota je prázdný řetězec. Pokud je stav neplatný, vrácený řetězec je určen řetězcovým prostředkem IDS_INVALID_CURRENCY.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency:: GetStatus

Chcete-li získat stav (platnost) daného objektu `COleCurrency`, zavolejte tuto členskou funkci.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleCurrency` hodnoty.

### <a name="remarks"></a>Poznámky

Návratová hodnota je definována výčtovým typem `CurrencyStatus`, který je definován v rámci `COleCurrency` třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

  - `COleCurrency::valid` označuje, že je tento objekt `COleCurrency` platný.

  - `COleCurrency::invalid` označuje, že tento objekt `COleCurrency` je neplatný. To znamená, že jeho hodnota může být nesprávná.

  - `COleCurrency::null` značí, že je tento objekt `COleCurrency` null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

Stav objektu `COleCurrency` je neplatný v následujících případech:

- Je-li jeho hodnota nastavena z hodnoty typu VARIANT nebo `COleVariant`, kterou nebylo možné převést na hodnotu měny.

- V případě, že se v tomto objektu vyskytla přetečení nebo podtečení během operace aritmetického přiřazování, například `+=` nebo **\*=** .

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

##  <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency:: m_cur

Základní struktura [měny](/windows/win32/api/wtypes/ns-wtypes-cy~r1) pro tento objekt `COleCurrency`.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Změna hodnoty ve struktuře `CURRENCY`, k níž přistupovalo ukazatelem vráceným touto funkcí, změní hodnotu tohoto objektu `COleCurrency`. Nemění stav tohoto objektu `COleCurrency`.

Další informace najdete v tématu o [měně](/windows/win32/api/wtypes/ns-wtypes-cy~r1) v Windows SDK.

##  <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency:: m_status

Typ tohoto datového členu je výčtový typ `CurrencyStatus`, který je definován v rámci `COleCurrency` třídy.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Poznámky

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid` označuje, že je tento objekt `COleCurrency` platný.

- `COleCurrency::invalid` označuje, že tento objekt `COleCurrency` je neplatný. To znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null` značí, že je tento objekt `COleCurrency` null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

Stav objektu `COleCurrency` je neplatný v následujících případech:

- Je-li jeho hodnota nastavena z hodnoty typu VARIANT nebo `COleVariant`, kterou nebylo možné převést na hodnotu měny.

- V případě, že se v tomto objektu vyskytla přetečení nebo podtečení během operace aritmetického přiřazování, například `+=` nebo **\*=** .

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
>  Tento datový člen slouží k pokročilým programovacím situacím. Měli byste použít funkce [GetStatus](#getstatus) a [SetStatus](#setstatus)vložených členů. Další upozornění týkající se explicitního nastavení tohoto datového členu najdete v tématu `SetStatus`.

##  <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency:: operator =

Tyto přetížené operátory přiřazení kopírují hodnotu zdrojové měny do tohoto objektu `COleCurrency`.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Poznámky

Následuje stručný popis každého operátoru:

- **operator = (** `cySrc` **)** – operátor Hodnota `CURRENCY` je zkopírována do objektu `COleCurrency` a její stav je nastaven na hodnotu platné.

- **operator = (** `curSrc` **)** – operátor Hodnota a stav operandu, existující objekt `COleCurrency`, je zkopírován do tohoto objektu `COleCurrency`.

- **operator = (** *varSrc* **)** – operátor Pokud je konverze `VARIANT` hodnoty (nebo objektu [COleVariant](../../mfc/reference/colevariant-class.md) ) na měnu (`VT_CY`) úspěšná, převedená hodnota se zkopíruje do tohoto objektu `COleCurrency` a jeho stav je nastaven na hodnotu platné. Pokud převod není úspěšný, hodnota objektu `COleCurrency` je nastavena na hodnotu 0 a jeho stav na neplatné.

Další informace naleznete v části [Měna](/windows/win32/api/wtypes/ns-wtypes-cy~r1) a [varianty](/windows/win32/api/oaidl/ns-oaidl-variant) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency:: operator +,-

Tyto operátory umožňují přidat a odečíst dvě `COleCurrency` hodnoty mezi sebou a změnit znaménko `COleCurrency` hodnoty.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Poznámky

Pokud je jeden z operandů null, stav výsledné `COleCurrency` hodnoty je null.

Pokud dojde k přetečení aritmetické operace, výsledná `COleCurrency` hodnota je neplatná.

Pokud je operand neplatný a druhý nemá hodnotu null, je stav výsledné `COleCurrency` hodnotu neplatný.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v tématu [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency:: operator + =,-=

Umožňuje přidat a odečíst `COleCurrency` hodnotu do a z tohoto objektu `COleCurrency`.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Poznámky

Pokud je jeden z operandů null, je stav objektu `COleCurrency` nastaven na hodnotu null.

Pokud dojde k přetečení aritmetické operace, stav objektu `COleCurrency` je nastaven na neplatné.

Pokud je jeden z operandů neplatný a druhý není null, stav tohoto objektu `COleCurrency` je nastaven na neplatné.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v tématu [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency:: operator \* a/

Umožňuje škálovat `COleCurrency` hodnoty celočíselnou hodnotou.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Poznámky

Pokud je operand `COleCurrency` null, stav výsledné `COleCurrency` hodnoty je null.

Pokud dojde k přetečení aritmetické operace nebo podtečení, stav výsledné `COleCurrency` hodnoty je neplatný.

Pokud je operand `COleCurrency` neplatný, stav výsledné `COleCurrency` hodnoty je neplatný.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v tématu [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency:: operator \*=,/=

Umožňuje škálovat tuto `COleCurrency`ou hodnotu celočíselnou hodnotou.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Poznámky

Pokud je operand `COleCurrency` null, je stav tohoto objektu `COleCurrency` nastaven na hodnotu null.

Pokud dojde k přetečení aritmetické operace, stav objektu `COleCurrency` je nastaven na neplatné.

Pokud je operand `COleCurrency` neplatný, je stav tohoto objektu `COleCurrency` nastaven na hodnotu neplatné.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v tématu [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency:: operator &lt;&lt;&gt;&gt;

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

##  <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency:: operator – měna

Vrací strukturu `CURRENCY`, jejíž hodnota je zkopírována z tohoto objektu `COleCurrency`.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Poznámky

##  <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::P arseCurrency

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

- Místo vlastního nastavení uživatele LOCALE_NOUSEROVERRIDE použít výchozí nastavení národního prostředí systému.

*lcid*<br/>
Označuje ID národního prostředí, které se má použít pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl řetězec úspěšně převeden na hodnotu měny, jinak 0.

### <a name="remarks"></a>Poznámky

Používá specifikace místních jazyků (ID národního prostředí) pro význam nenumerických znaků ve zdrojovém řetězci.

Diskuzi o hodnotách ID národního prostředí najdete v tématu [Podpora více jazyků](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Pokud byl řetězec úspěšně převeden na hodnotu měny, hodnota tohoto objektu `COleCurrency` je nastavena na tuto hodnotu a její stav na platná.

Pokud řetězec nelze převést na hodnotu měny nebo pokud došlo k numerickému přetečení, je stav objektu `COleCurrency` neplatný.

Pokud převod řetězce se nezdařil z důvodu chyb přidělení paměti, tato funkce vyvolá výjimku [CMemoryException](../../mfc/reference/cmemoryexception-class.md). V jakémkoli jiném chybovém stavu Tato funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Relační operátory COleCurrency

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
>  Návratová hodnota operací řazení ( **<** , **\<=** , **>** , **>=** ) není definována, pokud je stav obou operandů null nebo neplatný. Operátory rovnosti (`==`, `!=`) berou v úvahu stav operandů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency

Chcete-li nastavit jednotky a zlomkovou část tohoto objektu `COleCurrency`, zavolejte tuto členskou funkci.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nUnits*, *nFractionalUnits* značí jednotky a zlomkovou část (v 1/10000) hodnoty, které mají být zkopírovány do tohoto `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Je-li absolutní hodnota zlomkové části větší než 10 000, je provedena příslušná úprava jednotek, jak je znázorněno ve třetí části následujících příkladů.

Všimněte si, že jednotky a zlomkové součásti jsou určeny pomocí podepsaných dlouhých hodnot. Čtvrtý z následujících příkladů ukazuje, co se stane, když mají parametry jiné znaménko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency:: SetStatus

Chcete-li nastavit stav (platnost) tohoto objektu `COleCurrency`, zavolejte tuto členskou funkci.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*stav*<br/>
Nový stav tohoto objektu `COleCurrency`.

### <a name="remarks"></a>Poznámky

Hodnota parametru *status* je definována výčtovým typem `CurrencyStatus`, který je definován v rámci `COleCurrency` třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid` označuje, že je tento objekt `COleCurrency` platný.

- `COleCurrency::invalid` označuje, že tento objekt `COleCurrency` je neplatný. To znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null` značí, že je tento objekt `COleCurrency` null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

> [!CAUTION]
>  Tato funkce je určena pro pokročilé programovací situace. Tato funkce nemění data v tomto objektu. Nejčastěji se použije k nastavení stavu na hodnotu null nebo neplatný. Všimněte si, že operátor přiřazení ( [Operator =](#operator_eq)) a [SetCurrency](#setcurrency) nastaví stav na objekt na základě zdrojových hodnot (y).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant – třída](../../mfc/reference/colevariant-class.md)
