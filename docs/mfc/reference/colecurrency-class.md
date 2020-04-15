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
ms.openlocfilehash: 3cb3217e02323f8a0afcd1639e6e24ee7b0f136e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366147"
---
# <a name="colecurrency-class"></a>COleCurrency – třída

Zapouzdřuje `CURRENCY` datový typ automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleCurrency
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleCurrency::ColeCurrency](#colecurrency)|Vytvoří `COleCurrency` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleCurrency::Formát](#format)|Generuje formátovaný řetězec reprezentace `COleCurrency` objektu.|
|[COleCurrency::GetStatus](#getstatus)|Získá stav (platnost) tohoto `COleCurrency` objektu.|
|[COleCurrency::PArseCurrency](#parsecurrency)|Přečte hodnotu MĚDI z `COleCurrency`řetězce a nastaví hodnotu .|
|[COleCurrency::SetCurrency](#setcurrency)|Nastaví hodnotu `COleCurrency` tohoto objektu.|
|[COleCurrency::SetStatus](#setstatus)|Nastaví stav (platnost) `COleCurrency` pro tento objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje `COleCurrency` hodnotu.|
|[operátor +, -](#operator_plus_minus)|Přidá, odečte a změní `COleCurrency` znaménko hodnot.|
|[operátor +=, -=](#operator_plus_minus_eq)|Přidá a odečte `COleCurrency` hodnotu `COleCurrency` z tohoto objektu.|
|[operátor */](#operator_star)|Změní velikost `COleCurrency` hodnoty podle celé hodnoty.|
|[operátor *=, /=](#operator_star_div_eq)|Změní velikost `COleCurrency` této hodnoty o celou hodnotu.|
|[operátor <<](#operator_stream)|Výstupy `COleCurrency` hodnoty `CArchive` do `CDumpContext`nebo .|
|[operátor >>](#operator_stream)|Zadá `COleCurrency` objekt `CArchive`z .|
|[operátor MĚNa](#operator_currency)|Převede `COleCurrency` hodnotu na MĚNU.|
|[operátor ==, <, <=, atd.](#colecurrency_relational_operators)|Porovná dvě `COleCurrency` hodnoty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Obsahuje základní MĚNU `COleCurrency` pro tento objekt.|
|[COleCurrency::m_status](#m_status)|Obsahuje stav tohoto `COleCurrency` objektu.|

## <a name="remarks"></a>Poznámky

`COleCurrency`nemá základní třídu.

MĚNA je implementována jako 8 bajtů, dva komplementární celočíselné hodnoty měřítko o 10 000. To dává číslo s pevnou desetinnou čárkou s 15 číslicemi nalevo od desetinné čárky a 4 číslicemi vpravo. Datový typ MĚNA je velmi užitečný pro výpočty zahrnující peníze nebo pro jakýkoli výpočet s pevnou čárkem, kde je důležitá přesnost. Je jedním z možných `VARIANT` typů pro datový typ automatizace OLE.

`COleCurrency`také implementuje některé základní aritmetické operace pro tento typ pevného bodu. Podporované operace byly vybrány pro řízení chyb zaokrouhlení, ke kterým dochází při výpočtech s pevnými body.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleCurrency`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::ColeCurrency

Vytvoří `COleCurrency` objekt.

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
Hodnota MĚNA, která má `COleCurrency` být zkopírována do nového objektu.

*curSrc*<br/>
Existující `COleCurrency` objekt, který má být `COleCurrency` zkopírován do nového objektu.

*varSrc*<br/>
Existující `VARIANT` datová struktura `COleVariant` (případně objekt), která má být převedena na hodnotu `COleCurrency` měny (VT_CY) a zkopírována do nového objektu.

*nJednotky*, *nFractionalUnits* Uveďte jednotky a zlomkové části (v 1/10 000) hodnoty, `COleCurrency` která má být zkopírována do nového objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory `COleCurrency` vytvořit nové objekty inicializovány na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů. Není-li uvedeno jinak, `COleCurrency` je stav nové položky nastaven na platný.

- COleCurrency() Vytvoří `COleCurrency` objekt inicializován na 0 (nula).

- COleCurrency(`cySrc`) Vytvoří `COleCurrency` objekt z hodnoty [MĚDI.](/windows/win32/api/wtypes/ns-wtypes-cy~r1)

- COleCurrency(`curSrc`) Vytvoří `COleCurrency` objekt z `COleCurrency` existujícího objektu. Nový objekt má stejný stav jako zdrojový objekt.

- COleCurrency(`varSrc`) Vytvoří `COleCurrency` objekt. Pokusí se převést [variantu](/windows/win32/api/oaidl/ns-oaidl-variant) struktury nebo `COleVariant` objektu na hodnotu měny (VT_CY). Pokud je tento převod úspěšný, převedená hodnota `COleCurrency` se zkopíruje do nového objektu. Pokud tomu tak není, `COleCurrency` hodnota objektu je nastavena na nulu (0) a jeho stav neplatný.

- COleCurrency(`nUnits` `nFractionalUnits`, ) `COleCurrency` Vytvoří objekt ze zadaných číselných komponent. Pokud je absolutní hodnota zlomkového dílu větší než 10 000, provede se příslušná úprava jednotek. Všimněte si, že jednotky a zlomkové části jsou určeny podepsané dlouhé hodnoty.

Další informace naleznete v položkách [MĚNA](/windows/win32/api/wtypes/ns-wtypes-cy~r1) a [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklady ukazují účinky konstruktorů s nulovým a dvěma parametry:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency::Formát

Volání této členské funkce k vytvoření formátované reprezentace hodnoty měny.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Označuje příznaky pro nastavení národního prostředí. Pro měnu je relevantní pouze následující příznak:

- LOCALE_NOUSEROVERRIDE Místo vlastního uživatelského nastavení použijte výchozí nastavení národního prostředí systému.

*lcid*<br/>
Označuje ID národního prostředí, které má být pro převod používáno.

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje formátovanou hodnotu měny.

### <a name="remarks"></a>Poznámky

Zformátuje hodnotu pomocí specifikací místního jazyka (ID národního prostředí). Symbol měny není zahrnut ve vrácené hodnotě. Pokud je stav `COleCurrency` tohoto objektu null, vrácená hodnota je prázdný řetězec. Pokud je stav neplatný, je návratový řetězec určen IDS_INVALID_CURRENCY prostředků řetězce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency::GetStatus

Volání této členské funkce získat stav (platnost) `COleCurrency` daného objektu.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleCurrency` hodnoty.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je `CurrencyStatus` definována výčtu typu, `COleCurrency` který je definován v rámci třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid`Označuje, `COleCurrency` že tento objekt je platný.

- `COleCurrency::invalid`Označuje, `COleCurrency` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null`Označuje, `COleCurrency` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

Stav objektu `COleCurrency` je neplatný v následujících případech:

- Pokud je jeho hodnota nastavena z varianty nebo `COleVariant` hodnoty, kterou nelze převést na hodnotu měny.

- Pokud tento objekt došlo k přetečení nebo podtečení během `+=` operace ** \* **aritmetické přiřazení, například nebo .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na neplatný pomocí [funkce SetStatus](#setstatus).

Další informace o operacích, které mohou nastavit stav na neplatný, naleznete v následujících členských funkcích:

- [COleCurrency](#colecurrency)

- [operátor =](#operator_eq)

- [operátor + -](#operator_plus_minus)

- [operátor += a -=](#operator_plus_minus_eq)

- [operátor * /](#operator_star)

- [operátor *= a /=](#operator_star_div_eq)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency::m_cur

Základní [měna](/windows/win32/api/wtypes/ns-wtypes-cy~r1) struktura `COleCurrency` pro tento objekt.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> Změna hodnoty ve `CURRENCY` struktuře, ke které má přístup ukazatel vrácený touto funkcí, změní hodnotu tohoto `COleCurrency` objektu. Nezmění stav tohoto `COleCurrency` objektu.

Další informace naleznete v položce [MĚNA](/windows/win32/api/wtypes/ns-wtypes-cy~r1) v sadě Windows SDK.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency::m_status

Typ tohoto datového člena je výčtový typ `CurrencyStatus`, `COleCurrency` který je definován v rámci třídy.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Poznámky

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid`Označuje, `COleCurrency` že tento objekt je platný.

- `COleCurrency::invalid`Označuje, `COleCurrency` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null`Označuje, `COleCurrency` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

Stav objektu `COleCurrency` je neplatný v následujících případech:

- Pokud je jeho hodnota nastavena z varianty nebo `COleVariant` hodnoty, kterou nelze převést na hodnotu měny.

- Pokud tento objekt došlo k přetečení nebo podtečení během `+=` operace ** \* **aritmetické přiřazení, například nebo .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na neplatný pomocí [funkce SetStatus](#setstatus).

Další informace o operacích, které mohou nastavit stav na neplatný, naleznete v následujících členských funkcích:

- [COleCurrency](#colecurrency)

- [operátor =](#operator_eq)

- [operátor +, -](#operator_plus_minus)

- [operátor +=, -=](#operator_plus_minus_eq)

- [operátor */](#operator_star)

- [operátor *=, /=](#operator_star_div_eq)

> [!CAUTION]
> Tento datový člen je určen pro pokročilé programovací situace. Měli byste použít včleněné členské funkce [GetStatus](#getstatus) a [SetStatus](#setstatus). Viz `SetStatus` další upozornění týkající se explicitní nastavení tohoto datového člena.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency::operátor =

Tyto přetížené operátory přiřazení zkopírují `COleCurrency` hodnotu zdrojové měny do tohoto objektu.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Poznámky

Stručný popis každého operátora je následující:

- **operátor =(** `cySrc` **)** Hodnota `CURRENCY` je zkopírována do objektu `COleCurrency` a její stav je nastaven na platný.

- **operátor =(** `curSrc` **)** Hodnota a stav operandu, `COleCurrency` existující objekt jsou `COleCurrency` zkopírovány do tohoto objektu.

- **operátor =(** *varSrc* **)** Pokud je převod `VARIANT` hodnoty (nebo [cOleVariant](../../mfc/reference/colevariant-class.md) objekt) `VT_CY`na měnu ( ) úspěšný, převedená hodnota je zkopírována do tohoto `COleCurrency` objektu a její stav je nastaven na platný. Pokud převod není úspěšný, hodnota `COleCurrency` objektu je nastavena na hodnotu 0 a jeho stav neplatný.

Další informace naleznete v položkách [MĚNA](/windows/win32/api/wtypes/ns-wtypes-cy~r1) a [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency::operátor +, -

Tyto operátory umožňují přidat a `COleCurrency` odečíst dvě hodnoty do a od `COleCurrency` sebe navzájem a změnit znaménko hodnoty.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Poznámky

Pokud některý z operandů je null, stav `COleCurrency` výsledné hodnoty je null.

Pokud aritmetické operace přetečení, `COleCurrency` výsledná hodnota je neplatná.

Pokud je operand neplatný a druhý nemá hodnotu `COleCurrency` null, je stav výsledné hodnoty neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency::operátor +=, -=

Umožňují přidat a odečíst `COleCurrency` hodnotu do `COleCurrency` a od tohoto objektu.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Poznámky

Pokud je některý z operandů null, `COleCurrency` je stav tohoto objektu nastaven na hodnotu null.

Pokud aritmetické operace přetečení, `COleCurrency` stav tohoto objektu je nastavena na neplatnou.

Pokud je některý z operandů neplatný a druhý není `COleCurrency` null, je stav tohoto objektu nastaven na neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency::operátor \* a /

Umožňují škálovat `COleCurrency` hodnotu podle integrální hodnoty.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Poznámky

Pokud `COleCurrency` operand je null, stav výsledné `COleCurrency` hodnoty je null.

Pokud aritmetické operace přeteče nebo podtečení, `COleCurrency` stav výsledné hodnoty je neplatný.

Pokud `COleCurrency` je operand neplatný, stav `COleCurrency` výsledné hodnoty je neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency::operátor \*=, /=

Umožňují škálovat `COleCurrency` tuto hodnotu podle integrální hodnoty.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Poznámky

Pokud `COleCurrency` je operand null, je `COleCurrency` stav tohoto objektu nastaven na hodnotu null.

Pokud aritmetické operace přetečení, `COleCurrency` stav tohoto objektu je nastavena na neplatnou.

Pokud `COleCurrency` je operand neplatný, `COleCurrency` je stav tohoto objektu nastaven na neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::operátor &lt; &lt;,&gt;&gt;

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

Operátor extrakce ( **>>**) podporuje načítání z archivu.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency::MĚNA operátora

Vrátí `CURRENCY` strukturu, jejíž hodnota `COleCurrency` je zkopírována z tohoto objektu.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Poznámky

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::PArseCurrency

Volání této členské funkce analyzovat řetězec číst hodnotu měny.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Parametry

*lpszMěřidla*<br/>
Ukazatel na řetězec ukončený hodnotou null, který má být analyzován.

*dwFlags*<br/>
Označuje příznaky pro nastavení národního prostředí, případně následující příznak:

- LOCALE_NOUSEROVERRIDE Místo vlastního uživatelského nastavení použijte výchozí nastavení národního prostředí systému.

*lcid*<br/>
Označuje ID národního prostředí, které má být pro převod používáno.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl řetězec úspěšně převeden na hodnotu měny, jinak 0.

### <a name="remarks"></a>Poznámky

Používá specifikace místního jazyka (ID národního prostředí) pro význam nečíselných znaků ve zdrojovém řetězci.

Diskuse o hodnotách ID národního prostředí naleznete [v tématu Podpora více jazyků](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Pokud byl řetězec úspěšně převeden na hodnotu měny, `COleCurrency` hodnota tohoto objektu je nastavena na tuto hodnotu a jeho stav je platný.

Pokud řetězec nelze převést na hodnotu měny nebo pokud došlo k číselnému `COleCurrency` přetečení, je stav tohoto objektu neplatný.

Pokud se převod řetězce nezdařil z důvodu chyb přidělení paměti, tato funkce vyvolá [výjimku CMemoryException](../../mfc/reference/cmemoryexception-class.md). V jakémkoli jiném chybovém stavu tato funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Relační operátory COleCurrency

Porovnejte dvě hodnoty měny a vraťte nenulovou, pokud je podmínka splněna; jinak 0.

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
> Vrácená hodnota operací řazení **<** ** \< **( **>** **>=**, , , ) není definována, pokud je stav operandu null nebo neplatný. Operátory rovnosti `==` `!=`( , ) zvážit stav operandů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency

Volání této členské funkce nastavit jednotky a `COleCurrency` zlomkové části tohoto objektu.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parametry

*nJednotky*, *nFractionalUnits* Uveďte jednotky a zlomkové části (v 1/10 000) hodnoty, která má být zkopírována do tohoto `COleCurrency` objektu.

### <a name="remarks"></a>Poznámky

Pokud je absolutní hodnota zlomkového dílu větší než 10 000, provede se příslušná úprava jednotek, jak je znázorněno ve třetím z následujících příkladů.

Všimněte si, že jednotky a zlomkové části jsou určeny podepsané dlouhé hodnoty. Čtvrtý z následujících příkladů ukazuje, co se stane, když parametry mají různé znaky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency::SetStatus

Volání této členské funkce nastavit stav (platnost) tohoto `COleCurrency` objektu.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Nový stav pro `COleCurrency` tento objekt.

### <a name="remarks"></a>Poznámky

Hodnota *parametru stavu* je `CurrencyStatus` definována ve výčtovém `COleCurrency` typu, který je definován v rámci třídy.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleCurrency::valid`Označuje, `COleCurrency` že tento objekt je platný.

- `COleCurrency::invalid`Označuje, `COleCurrency` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleCurrency::null`Označuje, `COleCurrency` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

> [!CAUTION]
> Tato funkce je určena pro pokročilé programovací situace. Tato funkce nemění data v tomto objektu. Nejčastěji se používá k nastavení stavu null nebo neplatné. Všimněte si, že operátor přiřazení ( [operátor =](#operator_eq)) a [SetCurrency](#setcurrency) nastavit stav objektu na základě zdrojové hodnoty.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant třída](../../mfc/reference/colevariant-class.md)
