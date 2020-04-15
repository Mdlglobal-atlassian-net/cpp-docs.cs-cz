---
title: COleVariant třída
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: f907ed7c058f87cf03530411bc8fa4a3c108a4f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374827"
---
# <a name="colevariant-class"></a>COleVariant třída

Zapouzdřuje datový typ [VARIANT.](/windows/win32/api/oaidl/ns-oaidl-variant)

## <a name="syntax"></a>Syntaxe

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleVariant::ColeVariant](#colevariant)|Vytvoří `COleVariant` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleVariant::Připojit](#attach)|Připojí variantu k `COleVariant`.|
|[COleVariant::ChangeType](#changetype)|Změní typ varianty `COleVariant` tohoto objektu.|
|[COleVariant::Vymazat](#clear)|Vymaže tento `COleVariant` objekt.|
|[COleVariant::Detach](#detach)|Odpojí variantu od `COleVariant` a vrátí variantu.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Načte bajtové pole z existujícího pole varianty.|
|[COleVariant::SetString](#setstring)|Nastaví řetězec na určitý typ, obvykle ANSI.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[COleVariant::operátor LPCVARIANT](#operator_lpcvariant)|Převede `COleVariant` hodnotu `LPCVARIANT`na .|
|[COleVariant::operátor LPVARIANT](#operator_lpvariant)|Převede `COleVariant` objekt na `LPVARIANT`.|
|[COleVariant::operátor =](#operator_eq)|Zkopíruje `COleVariant` hodnotu.|
|[COleVariant::operátor ==](#operator_eq_eq)|Porovná dvě `COleVariant` hodnoty.|
|[COleVariant::operátor &lt; &lt;,&gt;&gt;](#operator_lt_lt__gt_gt)|Výstupy `COleVariant` hodnoty `CArchive` nebo `CDumpContext` a zadává `COleVariant` `CArchive`objekt z .|

## <a name="remarks"></a>Poznámky

Tento datový typ se používá v automatizaci OLE. Konkrétně [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) struktura obsahuje ukazatel na pole variant struktur. Struktura `DISPPARAMS` se používá k předání parametrů [iDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Tato třída je odvozena od `VARIANT` struktury. To znamená, že `COleVariant` můžete předat v `VARIANT` parametr, který volá `VARIANT` pro a, že `COleVariant`datové členy struktury jsou přístupné datové členy .

Dvě související třídy knihovny MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) a [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) `VT_CY`zapouzdřují variantní datové typy CURRENCY ( ) a DATE ( `VT_DATE`). Třída `COleVariant` se používá značně ve třídách DAO; viz tyto třídy pro typické použití této třídy, například [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Další informace naleznete [v položkách VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)a [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) v sadě Windows SDK.

Další informace o `COleVariant` třídě a jeho použití v automatizaci OLE naleznete v části předávání parametrů v automatizaci OLE v článku [Automatizace](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant::Připojit

Volání této funkce připojit daný [objekt](/windows/win32/api/oaidl/ns-oaidl-variant) `COleVariant` VARIANT k aktuálnímu objektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Existující `VARIANT` objekt, který má být `COleVariant` připojen k aktuálnímu objektu.

### <a name="remarks"></a>Poznámky

Tato funkce nastaví VARTYPE *varSrc* na VT_EMPTY.

Další informace naleznete [v](/windows/win32/api/oaidl/ns-oaidl-variant) položkách VARIANT a [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) v sadě Windows SDK.

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant::ColeVariant

Vytvoří `COleVariant` objekt.

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Existující `COleVariant` nebo `VARIANT` objekt, který má `COleVariant` být zkopírován do nového objektu.

*pSrc*<br/>
Ukazatel na `VARIANT` objekt, který bude zkopírován do nového `COleVariant` objektu.

*lpszSrc*<br/>
Řetězec s ukončeným hodnotou null, `COleVariant` který má být zkopírován do nového objektu.

*vtSrc řekl:*<br/>
Pro `VARTYPE` nový `COleVariant` objekt.

*strSrc*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který má být `COleVariant` zkopírován do nového objektu.

*nSrc*, *lSrc* Číselná hodnota, která `COleVariant` má být zkopírována do nového objektu.

*vtSrc řekl:*<br/>
Pro `VARTYPE` nový `COleVariant` objekt.

*curSrc*<br/>
[COleCurrency](../../mfc/reference/colecurrency-class.md) objekt, který má být `COleVariant` zkopírován do nového objektu.

*fltSrc*, *dblSrc*<br/>
Číselná hodnota, která má být `COleVariant` zkopírována do nového objektu.

*timeSrc*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který má být `COleVariant` zkopírován do nového objektu.

*arrSrc*<br/>
[CByteArray](../../mfc/reference/cbytearray-class.md) objekt, který má být `COleVariant` zkopírován do nového objektu.

*lbSrc*<br/>
[CLongBinary](../../mfc/reference/clongbinary-class.md) objekt, který má být `COleVariant` zkopírován do nového objektu.

*pidl*<br/>
Ukazatel na [itemidlist](/windows/win32/api/shtypes/ns-shtypes-itemidlist) struktury, které mají `COleVariant` být zkopírovány do nového objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory `COleVariant` vytvořit nové objekty inicializovány na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů.

- **COleVariant( )** Vytvoří prázdný `COleVariant` objekt, VT_EMPTY.

- **COleVariant(** *varSrc* **)** Zkopíruje `VARIANT` existující `COleVariant` nebo objekt. Typ varianty je zachován.

- **COleVariant(** *pSrc* **)** Zkopíruje `VARIANT` existující `COleVariant` nebo objekt. Typ varianty je zachován.

- **COleVariant(** *lpszSrc* **)** Zkopíruje řetězec do nového objektu, VT_BSTR (UNICODE).

- **COleVariant(** *lpszSrc* **,** *vtSrc* **)** Zkopíruje řetězec do nového objektu. Parametr *vtSrc* musí být VT_BSTR (UNICODE) nebo VT_BSTRT (ANSI).

- **COleVariant(** *strSrc* **)** Zkopíruje řetězec do nového objektu, VT_BSTR (UNICODE).

- **COleVariant(** *nSrc* **)** Zkopíruje 8bitové celé číslo do nového objektu, VT_UI1.

- **COleVariant(** *nSrc* **,** *vtSrc* **)** Zkopíruje do nového objektu 16bitové celé číslo (nebo logickou hodnotu). Parametr *vtSrc* musí být VT_I2 nebo VT_BOOL.

- **COleVariant(** *lSrc* **,** *vtSrc* **)** Zkopíruje do nového objektu 32bitové celé číslo (nebo hodnotu SCODE). Parametr *vtSrc* musí být VT_I4, VT_ERROR nebo VT_BOOL.

- **COleVariant(** *curSrc* **)** Zkopíruje `COleCurrency` hodnotu do nového objektu, VT_CY.

- **COleVariant(** *fltSrc* **)** Zkopíruje 32bitovou hodnotu s plovoucí desetinnou hodnotou do nového objektu, VT_R4.

- **COleVariant(** *dblSrc* **)** Zkopíruje 64bitovou hodnotu s plovoucí desetinnou hodnotou do nového objektu, VT_R8.

- **COleVariant(** *timeSrc* **)** Zkopíruje `COleDateTime` hodnotu do nového objektu, VT_DATE.

- **COleVariant(** *arrSrc* **)** Zkopíruje `CByteArray` objekt do nového objektu, VT_EMPTY.

- **COleVariant(** *lbSrc* **)** Zkopíruje `CLongBinary` objekt do nového objektu, VT_EMPTY.

Další informace o kódu SCODE naleznete [v tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant::ChangeType

Převede typ hodnoty varianty `COleVariant` v tomto objektu.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vartyp*<br/>
VARTYPE pro `COleVariant` tento objekt.

*pSrc*<br/>
Ukazatel na [objekt VARIANT,](/windows/win32/api/oaidl/ns-oaidl-variant) který má být převeden. Pokud je tato hodnota `COleVariant` null, tento objekt se používá jako zdroj pro převod.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v](/windows/win32/api/oaidl/ns-oaidl-variant)položkách VARIANT , [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)a [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) v sadách Windows SDK.

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant::Vymazat

Vymaže `VARIANT`.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Tím nastavíte VARTYPE pro tento objekt VT_EMPTY. Destruktor `COleVariant` volá tuto funkci.

Další informace naleznete `VARIANT`v souboru `VariantClear` , VARTYPE a položkách v sadě Windows SDK.

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::Detach

Odpojí základní objekt [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) `COleVariant` od tohoto objektu.

```
VARIANT Detach();
```

### <a name="remarks"></a>Poznámky

Tato funkce nastaví vartype pro tento `COleVariant` objekt VT_EMPTY.

> [!NOTE]
> Po `Detach`volání je odpovědností volajícího volat `VariantClear` na výslednou `VARIANT` strukturu.

Další informace naleznete [v](/windows/win32/api/oaidl/ns-oaidl-variant)položkách VARIANT , [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)a [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) v sadách Windows SDK.

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray

Načte bajtové pole z existujícího pole variant.

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*Bajtů*<br/>
Odkaz na existující objekt [CByteArray.](../../mfc/reference/cbytearray-class.md)

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant::operátor LPCVARIANT

Tento operátor přetypování vrátí strukturu, `VARIANT` `COleVariant` jejíž hodnota je zkopírována z tohoto objektu.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Poznámky

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant::operátor LPVARIANT

Volání tohoto operátoru přetypování pro přístup k základní `VARIANT` struktuře pro tento `COleVariant` objekt.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> Změna hodnoty ve `VARIANT` struktuře, ke které má přístup ukazatel vrácený touto funkcí, změní hodnotu tohoto `COleVariant` objektu.

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant::operátor =

Tyto přetížené operátory přiřazení zkopírují zdrojovou hodnotu do tohoto `COleVariant` objektu.

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>Poznámky

Stručný popis každého operátora je následující:

- **operátor =(** *varSrc* **)** Zkopíruje existující `COleVariant` VARIANT nebo objekt do tohoto objektu.

- **operátor =(** *pSrc* **)** Zkopíruje objekt VARIANT, ke kterého *pSrc* přistupuje, do tohoto objektu.

- **operátor =(** *lpszSrc* **)** Zkopíruje řetězec s ukončeným hodnotou null do tohoto objektu a nastaví typ VARTYPE na VT_BSTR.

- **operátor =(** *strSrc* **)** Zkopíruje [cstring](../../atl-mfc-shared/reference/cstringt-class.md) objekt do tohoto objektu a nastaví VARTYPE na VT_BSTR.

- **operátor =(** *nSrc* **)** Zkopíruje do tohoto objektu osmibitovou nebo 16bitovou celočíselnou hodnotu. Pokud *nSrc* je 8bitová hodnota, VARTYPE to je nastavena na VT_UI1. Pokud *nSrc* je 16bitová hodnota a VARTYPE to je VT_BOOL, je zachována; v opačném případě je nastavena na VT_I2.

- **operátor =(** *lSrc* **)** Zkopíruje do tohoto objektu 32bitovou celočíselnou hodnotu. Pokud vartype to je VT_ERROR, je zachována; v opačném případě je nastavena na VT_I4.

- **operátor =(** *curSrc* **)** Zkopíruje [cOleCurrency](../../mfc/reference/colecurrency-class.md) objekt do tohoto objektu a nastaví VARTYPE na VT_CY.

- **operátor =(** *fltSrc* **)** Zkopíruje 32bitovou hodnotu s plovoucí desetinnou tácem do tohoto objektu a nastaví typ VARTYPE na VT_R4.

- **operátor =(** *dblSrc* **)** Zkopíruje 64bitovou hodnotu s plovoucí desetinnou tácem do tohoto objektu a nastaví typ VARTYPE na VT_R8.

- **operátor =(** *dateSrc* **)** Zkopíruje [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt do tohoto objektu a nastaví VARTYPE na VT_DATE.

- **operátor =(** *arrSrc* **)** Zkopíruje objekt [CByteArray](../../mfc/reference/cbytearray-class.md) do tohoto `COleVariant` objektu.

- **operátor =(** *lbSrc* **)** Zkopíruje [clongbinary](../../mfc/reference/clongbinary-class.md) objekt `COleVariant` do tohoto objektu.

Další informace naleznete [v](/windows/win32/api/oaidl/ns-oaidl-variant) položkách VARIANT a [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) v sadě Windows SDK.

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant::operátor ==

Tento operátor porovná dvě hodnoty varianta a vrátí nenulovou, pokud jsou stejné; jinak 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant::operátor &lt; &lt;,&gt;&gt;

Výstupy `COleVariant` hodnoty `CArchive` nebo `CdumpContext` a zadává `COleVariant` `CArchive`objekt z .

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>Poznámky

Operátor `COleVariant` vložení (**\<**) podporuje diagnostický dumping a ukládání do archivu. Operátor extrakce (**>>**) podporuje načítání z archivu.

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant::SetString

Nastaví řetězec na určitý typ.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parametry

*lpszSrc*<br/>
Řetězec s ukončeným hodnotou null, `COleVariant` který má být zkopírován do nového objektu.

*VtSrc řekl:*<br/>
VARTYPE pro nový `COleVariant` objekt.

### <a name="remarks"></a>Poznámky

Parametr *vtSrc* musí být VT_BSTR (UNICODE) nebo VT_BSTRT (ANSI). `SetString`Obvykle se používá k nastavení řetězců na ANSI, protože výchozí hodnota konstruktoru [COleVariant::COleVariant](#colevariant) s parametrem string nebo string pointer a žádný VARTYPE není UNICODE.

Sada záznamů DAO v sestavení bez UNICODE očekává, že řetězce budou ANSI. `COleVariant` Proto pro funkce DAO, které používají objekty, pokud nevytváříte sadu záznamů UNICODE, musíte použít **cOleVariant::COleVariant(** *lpszSrc* **,** *vtSrc* **)** forma konstruktoru s *vtSrc* nastavena na VT_BSTRT (ANSI) nebo použít `SetString` s *vtSrc* nastavena na VT_BSTRT k vytvoření ansi řetězců. Například `CDaoRecordset` funkce [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) a [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) používají `COleVariant` objekty jako parametry. Tyto objekty musí být ANSI, pokud sada záznamů DAO není UNICODE.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
