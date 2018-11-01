---
title: COleCurrency – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: d831353c72c40ab4f35b64046ab5d5236aa9644a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553488"
---
# <a name="colecurrency-class"></a>COleCurrency – třída

Zapouzdřuje `CURRENCY` datovým typem automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Vytvoří `COleCurrency` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleCurrency::Format](#format)|Generuje formátovaný řetězec představující `COleCurrency` objektu.|
|[COleCurrency::GetStatus](#getstatus)|Získá stav (platnosti) to `COleCurrency` objektu.|
|[COleCurrency::ParseCurrency](#parsecurrency)|Načte hodnotu měny z řetězce a nastaví hodnotu `COleCurrency`.|
|[COleCurrency::SetCurrency](#setcurrency)|Nastaví hodnotu tohoto `COleCurrency` objektu.|
|[COleCurrency::SetStatus](#setstatus)|Nastaví stav (platnosti) pro tuto `COleCurrency` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje `COleCurrency` hodnotu.|
|[operátor +, -](#operator_plus_minus)|Přidá odečte a změní znaménko `COleCurrency` hodnoty.|
|[Operator +=-=](#operator_plus_minus_eq)|Přidá a odečte `COleCurrency` hodnotu z této `COleCurrency` objektu.|
|[Operator * /](#operator_star)|Škálování `COleCurrency` hodnoty celočíselnou hodnotu.|
|[Operator * =, / =](#operator_star_div_eq)|To se škáluje `COleCurrency` hodnoty celočíselnou hodnotu.|
|[operátor <<](#operator_stream)|Výstupy `COleCurrency` hodnota, která se `CArchive` nebo `CDumpContext`.|
|[operátor >>](#operator_stream)|Vstupy `COleCurrency` objektu z `CArchive`.|
|[operátor měny](#operator_currency)|Převede `COleCurrency` hodnotu do měny.|
|[operátor ==, <, < =, atd.](#colecurrency_relational_operators)|Porovná dva `COleCurrency` hodnoty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Obsahuje základní měny pro tuto `COleCurrency` objektu.|
|[COleCurrency::m_status](#m_status)|Obsahuje stav tohoto `COleCurrency` objektu.|

## <a name="remarks"></a>Poznámky

`COleCurrency` nemá základní třídu.

MĚNY je implementovaný jako 8 bajtů, celé číslo dvojkového doplňku měřítkem řídit 10 000. Díky tomu číslo s pevnou desetinnou čárkou s 15 číslic nalevo od desetinné čárky a 4 číslice vpravo. Datový typ MĚNA je velmi užitečné pro peněžních výpočtů nebo pro všechny s pevnou desetinnou čárkou výpočet kdy přesnost je důležité. Je jedním z možných typů `VARIANT` datovým typem automatizace OLE.

`COleCurrency` také implementuje některé základní aritmetické operace u tohoto typu s pevnou desetinnou čárkou. Podporované operace byly vybrány pro řízení zaokrouhlovací chyby, ke kterým dochází při výpočty s pevnou desetinnou čárkou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleCurrency`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="colecurrency"></a>  COleCurrency::COleCurrency

Vytvoří `COleCurrency` objektu.

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
Hodnota měny, které se mají zkopírovat do nové `COleCurrency` objektu.

*curSrc*<br/>
Existující `COleCurrency` objektu, které se mají zkopírovat do nové `COleCurrency` objektu.

*varSrc*<br/>
Existující `VARIANT` datovou strukturu (pravděpodobně `COleVariant` objektu) převést na hodnotu měny (VT_CY) a zkopírovány do nového `COleCurrency` objektu.

*nUnits*, *nFractionalUnits* označení jednotky a zlomkovou část (v 1/10 000's) hodnota, které se mají zkopírovat do nové `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvořit nový `COleCurrency` objekty inicializovány na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů. Pokud není uvedeno jinak, stav nového `COleCurrency` položku nastavena na platný.

- Konstrukce COleCurrency() `COleCurrency` objekt je inicializován na hodnotu 0 (nula).

- COleCurrency (`cySrc`) sestaví `COleCurrency` objektu z [měny](/windows/desktop/api/wtypes/ns-wtypes-tagcy) hodnotu.

- COleCurrency (`curSrc`) sestaví `COleCurrency` objekt z existující `COleCurrency` objektu. Nový objekt je stejného stavu jako zdrojový objekt.

- COleCurrency (`varSrc`) sestaví `COleCurrency` objektu. Se pokusí převést [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) struktury nebo `COleVariant` objektu na hodnotu měny (VT_CY). Pokud tento převod je úspěšný, převedená hodnota zkopírován do nové `COleCurrency` objektu. Pokud ne, je hodnota `COleCurrency` objektu je nastavena na nulu (0) a její stav na neplatný.

- `COleCurrency(`nUnits`, `nFractionalUnits`) Constructs a `COleCurrency "objekt ze zadané číselné součásti. Pokud absolutní hodnota zlomkové části je větší než 10 000 operací, je vhodné úpravy provedené s jednotkami. Všimněte si, že jsou určeny jednotky a desetinná část dlouhé hodnoty se znaménkem.

Další informace najdete v tématu [měny](/windows/desktop/api/wtypes/ns-wtypes-tagcy) a [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) položky v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklady ukazují účinky konstruktory parametr nula a dvěma parametr:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="format"></a>  COleCurrency::Format

Voláním této členské funkce k vytvoření formátovaného reprezentace hodnoty měny.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Určuje příznaky pro nastavení národního prostředí. Pouze následující příznak je relevantní pro měny:

- LOCALE_NOUSEROVERRIDE použijte výchozí nastavení národního prostředí systému, raději vlastní uživatelská nastavení.

*lcid*<br/>
Určuje ID národního prostředí pro převod.

### <a name="return-value"></a>Návratová hodnota

A `CString` , který obsahuje hodnotu ve formátu Měna.

### <a name="remarks"></a>Poznámky

Formátuje hodnoty pomocí specifikace místní jazyka (ID národních prostředí). Vrácená hodnota není součástí symbol měny. Pokud se stav tohoto `COleCurrency` objekt má hodnotu null, vrácená hodnota je prázdný řetězec. Pokud je neplatný stav, vrácený řetězec je určená IDS_INVALID_CURRENCY prostředek řetězce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="getstatus"></a>  COleCurrency::GetStatus

Voláním této členské funkce k získání stavu (platnost) daném `COleCurrency` objektu.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleCurrency` hodnotu.

### <a name="remarks"></a>Poznámky

Návratová hodnota je definována `CurrencyStatus` Výčtový typ, který je definován v rámci `COleCurrency` třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

  - `COleCurrency::valid` Označuje, že tento `COleCurrency` objektu je neplatný.

  - `COleCurrency::invalid` Označuje, že tento `COleCurrency` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

  - `COleCurrency::null` Označuje, že tento `COleCurrency` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

Stav `COleCurrency` objekt není platný v následujících případech:

- Pokud je jeho hodnota v rozsahu od hodnotu typu VARIANT nebo `COleVariant` hodnotu, která nelze převést na hodnotu měny.

- Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, například `+=` nebo **\* =**.

- Pokud na tento objekt byl přiřazen neplatnou hodnotu.

- Pokud se stav tohoto objektu explicitně nastavit na neplatné použití [SetStatus](#setstatus).

Další informace o operacích, které může nastavit stav na neplatné, viz následující členské funkce:

- [COleCurrency](#colecurrency)

- [operátor =](#operator_eq)

- [Operator + –](#operator_plus_minus)

- [Operator += a-=](#operator_plus_minus_eq)

- [Operator * /](#operator_star)

- [Operator * = a / =](#operator_star_div_eq)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="m_cur"></a>  COleCurrency::m_cur

Základní [měny](/windows/desktop/api/wtypes/ns-wtypes-tagcy) strukturu pro to `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Změna hodnoty v `CURRENCY` struktura přistupuje vrácený touto funkcí ukazatel se změní hodnota tohoto `COleCurrency` objektu. Nezmění stav této `COleCurrency` objektu.

Další informace najdete v tématu [měny](/windows/desktop/api/wtypes/ns-wtypes-tagcy) položku v sadě Windows SDK.

##  <a name="m_status"></a>  COleCurrency::m_status

Typ tomuto datovému členu je výčtového typu `CurrencyStatus`, který je definován v rámci `COleCurrency` třídy.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Poznámky

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

- `COleCurrency::valid` Označuje, že tento `COleCurrency` objektu je neplatný.

- `COleCurrency::invalid` Označuje, že tento `COleCurrency` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

- `COleCurrency::null` Označuje, že tento `COleCurrency` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

Stav `COleCurrency` objekt není platný v následujících případech:

- Pokud je jeho hodnota v rozsahu od hodnotu typu VARIANT nebo `COleVariant` hodnotu, která nelze převést na hodnotu měny.

- Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, například `+=` nebo **\* =**.

- Pokud na tento objekt byl přiřazen neplatnou hodnotu.

- Pokud se stav tohoto objektu explicitně nastavit na neplatné použití [SetStatus](#setstatus).

Další informace o operacích, které může nastavit stav na neplatné, viz následující členské funkce:

- [COleCurrency](#colecurrency)

- [operátor =](#operator_eq)

- [operátor +, -](#operator_plus_minus)

- [Operator +=-=](#operator_plus_minus_eq)

- [Operator * /](#operator_star)

- [Operator * =, / =](#operator_star_div_eq)

> [!CAUTION]
>  Pro pokročilé situacích programování je tomuto datovému členu. Používejte vložené členské funkce [GetStatus](#getstatus) a [SetStatus](#setstatus). Zobrazit `SetStatus` pro další upozornění týkající se explicitním nastavením tomuto datovému členu.

##  <a name="operator_eq"></a>  COleCurrency::operator =

Zkopírování těchto přetížených operátorech přiřazení zdrojová hodnota měny do tohoto `COleCurrency` objektu.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
  const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Poznámky

Následuje stručný popis jednotlivých operátorů:

- **Operator = (** `cySrc` **)** `CURRENCY` zkopírování hodnoty do `COleCurrency` objektu a jeho stav je nastaven na platný.

- **operátor = (** `curSrc` **)** hodnotu a stav operandu, existující `COleCurrency` objektu jsou zkopírovány do tohoto `COleCurrency` objektu.

- **operátor = (** *varSrc* **)** Pokud převod `VARIANT` hodnotu (nebo [COleVariant](../../mfc/reference/colevariant-class.md) objekt) do měny ( `VT_CY`) je úspěšné, převedená hodnota se zkopíruje do tohoto `COleCurrency` objektu a jeho stav je nastaven na platný. Pokud neproběhne úspěšně, převod hodnoty `COleCurrency` objektu je nastavena na 0 a její stav na neplatný.

Další informace najdete v tématu [měny](/windows/desktop/api/wtypes/ns-wtypes-tagcy) a [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) položky v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="operator_plus_minus"></a>  COleCurrency::operator +, -

Tyto operátory vám operátorů sčítání a odečítání dvě umožní `COleCurrency` hodnot a od sebe navzájem a ke změně znaménka `COleCurrency` hodnotu.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Poznámky

Pokud platí některá z operandů s hodnotou null, výsledný stav `COleCurrency` hodnotu null.

Pokud aritmetické přetečení, výsledná `COleCurrency` hodnota není platná.

Je-li operand neplatné a druhý není null, výsledný stav `COleCurrency` hodnota není platná.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="operator_plus_minus_eq"></a>  COleCurrency::operator +=-=

Umožňují operátorů sčítání a odečítání `COleCurrency` hodnotu do a z tohoto `COleCurrency` objektu.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Poznámky

Pokud jeden z operandů je null, použije stav této `COleCurrency` objekt je nastaven na hodnotu null.

Pokud aritmetické přetečení, stav této `COleCurrency` objekt je nastaven na neplatný.

Pokud jeden z operandů je neplatný a druhá nemá hodnotu null, stav této `COleCurrency` objekt je nastaven na neplatný.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="operator_star"></a>  COleCurrency::operator \* a /

Umožňují škálování `COleCurrency` hodnoty celočíselnou hodnotu.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Poznámky

Pokud `COleCurrency` operand má hodnotu null, výsledný stav `COleCurrency` hodnotu null.

Pokud aritmetické přetečení nebo podtečení, výsledný stav `COleCurrency` hodnota není platná.

Pokud `COleCurrency` operand je neplatný, výsledný stav `COleCurrency` hodnota není platná.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="operator_star_div_eq"></a>  COleCurrency::operator \*=, / =

Bylo možné kapacitu rozšířit `COleCurrency` hodnoty celočíselnou hodnotu.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Poznámky

Pokud `COleCurrency` operand má hodnotu null, stav této `COleCurrency` objekt je nastaven na hodnotu null.

Pokud aritmetické přetečení, stav této `COleCurrency` objekt je nastaven na neplatný.

Pokud `COleCurrency` operand je neplatný, stav této `COleCurrency` objekt je nastaven na neplatný.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="operator_stream"></a>  COleCurrency::operator &lt; &lt;, &gt;&gt;

Podporuje diagnostiku vypsání a ukládání do archivu.

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

Extrakce ( **>>**) – operátor podporuje načítání z archivu.

##  <a name="operator_currency"></a>  COleCurrency::operator měny

Vrátí `CURRENCY` strukturu, jejíž hodnota je zkopírován z tohoto `COleCurrency` objektu.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Poznámky

##  <a name="parsecurrency"></a>  COleCurrency::ParseCurrency

Zavolejte tuto členskou funkci k analýze řetězce ke čtení hodnoty měny.

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
Určuje příznaky pro nastavení národního prostředí, může být příznak následující:

- LOCALE_NOUSEROVERRIDE použijte výchozí nastavení národního prostředí systému, raději vlastní uživatelská nastavení.

*lcid*<br/>
Určuje ID národního prostředí pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud řetězec byl úspěšně převeden na hodnotu měny, jinak 0.

### <a name="remarks"></a>Poznámky

Specifikace místní jazyka (ID národních prostředí) používá pro význam číselného typu znaků ve zdrojovém řetězci.

Diskuzi o hodnoty ID národního prostředí, najdete v článku [podpora více jazyků](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Pokud řetězec byl úspěšně převeden do měny hodnotu, hodnota tohoto `COleCurrency` objekt je nastaven na tuto hodnotu a její stav na platný.

Pokud řetězec nelze převést na hodnotu měny, nebo pokud byla číselné přetečení, stav této `COleCurrency` objekt je neplatný.

Pokud převod řetězce se nezdařilo z důvodu chyb přidělení paměti, vyvolá tato funkce [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md). V jiných chybový stav, tato funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency_relational_operators"></a>  COleCurrency – relační operátory

Porovnat dvě hodnoty měny a vrátí nenulovou hodnotu, pokud je podmínka true. jinak 0.

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
>  Návratová hodnota pořadí operací ( **<**, **\< =**, **>**, **>=**) není definována, pokud stav některý operand je null nebo je neplatný. Operátory rovnosti ( `==`, `!=`) vezměte v úvahu stav operandy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="setcurrency"></a>  COleCurrency::SetCurrency

Voláním této členské funkce pro nastavení jednotky a zlomkovou část `COleCurrency` objektu.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nUnits*, *nFractionalUnits* označení jednotky a zlomkovou část (v 1/10 000's) hodnota, které se mají zkopírovat do tohoto `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Pokud absolutní hodnota zlomkové části je větší než 10 000 operací, příslušné úpravy provedené v jednotkách, jak je znázorněno v jiných následující příklady.

Všimněte si, že jsou určeny jednotky a desetinná část dlouhé hodnoty se znaménkem. Čtvrtý následující příklady ukazuje, co se stane, když parametry mají odlišná znaménka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="setstatus"></a>  COleCurrency::SetStatus

Voláním této členské funkce pro nastavení stavu (platnost) to `COleCurrency` objektu.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Nový stav `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

*Stav* hodnota parametru je definována `CurrencyStatus` Výčtový typ, který je definován v rámci `COleCurrency` třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

- `COleCurrency::valid` Označuje, že tento `COleCurrency` objektu je neplatný.

- `COleCurrency::invalid` Označuje, že tento `COleCurrency` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

- `COleCurrency::null` Označuje, že tento `COleCurrency` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

> [!CAUTION]
>  Tato funkce je pro pokročilé situacích programování. Tato funkce nezmění data v tomto objektu. Bude se nejčastěji používají k nastavení stavu na null nebo neplatná. Všimněte si, že operátor přiřazení ( [operátoru =](#operator_eq)) a [SetCurrency](#setcurrency) nastavit stav na objektu podle hodnoty, které zdroj.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant – třída](../../mfc/reference/colevariant-class.md)
