---
title: COleVariant – třída
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
ms.openlocfilehash: 49cd4a8d3db436d5e3c4d29efbb4d80b4741a270
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739779"
---
# <a name="colevariant-class"></a>COleVariant – třída

Zapouzdřuje datový typ [variant](/windows/win32/api/oaidl/ns-oaidl-variant) .

## <a name="syntax"></a>Syntaxe

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleVariant::COleVariant](#colevariant)|`COleVariant` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleVariant::Attach](#attach)|Připojí VARIANTu k `COleVariant`.|
|[COleVariant::ChangeType](#changetype)|Změní typ variant tohoto `COleVariant` objektu.|
|[COleVariant::Clear](#clear)|Vymaže tento `COleVariant` objekt.|
|[COleVariant::Detach](#detach)|Odpojí variantu od `COleVariant` a a vrátí variantu.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Načte pole bajtů z existujícího pole variant.|
|[COleVariant:: SetString](#setstring)|Nastaví řetězec na konkrétní typ, obvykle ANSI.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[COleVariant:: operator LPCVARIANT](#operator_lpcvariant)|`COleVariant` Převede hodnotu`LPCVARIANT`na.|
|[COleVariant:: operator LPVARIANT](#operator_lpvariant)|`COleVariant` Převede objekt`LPVARIANT`na.|
|[COleVariant:: operator =](#operator_eq)|`COleVariant` Zkopíruje hodnotu.|
|[COleVariant:: operator = = – operátor](#operator_eq_eq)|Porovná `COleVariant` dvě hodnoty.|
|[COleVariant:: operator &lt;, &lt;&gt;&gt;](#operator_lt_lt__gt_gt)|`CArchive` `CDumpContext` Vytvoří výstup `COleVariant` `CArchive`hodnoty na nebo a vstup objektu z. `COleVariant`|

## <a name="remarks"></a>Poznámky

Tento typ dat se používá v automatizaci OLE. Konkrétně struktura [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) obsahuje ukazatel na pole variantních struktur. Struktura se používá k předání parametrů rozhraní [IDispatch:: Invoke.](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) `DISPPARAMS`

> [!NOTE]
> Tato třída je odvozena z `VARIANT` struktury. To znamená, že můžete předat `COleVariant` do parametr, který volá `VARIANT` pro a, aby datové členy `VARIANT` struktury byly přístupné datovým členům `COleVariant`.

Dvě související třídy MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) a [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zapouzdřují variantní datové typy Currency ( `VT_CY`) a Date ( `VT_DATE`). Třída se používá rozsáhle v třídách rozhraní DAO; tyto třídy si můžete prohlédnout pro typické použití této třídy, například [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) a [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) `COleVariant`

Další informace naleznete v tématu [variant](/windows/win32/api/oaidl/ns-oaidl-variant), [Currency](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)a [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) v Windows SDK.

Další informace o `COleVariant` třídě a jejím použití v automatizaci OLE naleznete v tématu "předávání parametrů v automatizaci OLE" v článku [Automatizace](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="attach"></a>COleVariant:: Attach

Voláním této funkce připojíte daný objekt [variant](/windows/win32/api/oaidl/ns-oaidl-variant) k aktuálnímu `COleVariant` objektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Existující `VARIANT` objekt, který bude připojen k aktuálnímu `COleVariant` objektu.

### <a name="remarks"></a>Poznámky

Tato funkce nastaví VARTYPE typu *varSrc* na VT_EMPTY.

Další informace naleznete v tématu [variant](/windows/win32/api/oaidl/ns-oaidl-variant) a [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) položky v Windows SDK.

##  <a name="colevariant"></a>COleVariant::COleVariant

`COleVariant` Vytvoří objekt.

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
Existující `COleVariant` objekt nebo `VARIANT` objekt, který má být zkopírován do `COleVariant` nového objektu.

*pSrc*<br/>
Ukazatel na `VARIANT` objekt, který bude zkopírován do nového `COleVariant` objektu.

*lpszSrc*<br/>
Řetězec zakončený hodnotou null, který má být zkopírován do `COleVariant` nového objektu.

*vtSrc*<br/>
`VARTYPE` Pro nový`COleVariant` objekt.

*strSrc*<br/>
Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který bude zkopírován do nového `COleVariant` objektu.

*nSrc*, *lSrc* číselnou hodnotu, která se má zkopírovat do nového `COleVariant` objektu.

*vtSrc*<br/>
`VARTYPE` Pro nový`COleVariant` objekt.

*curSrc*<br/>
Objekt [COleCurrency](../../mfc/reference/colecurrency-class.md) , který se má zkopírovat do nového `COleVariant` objektu.

*fltSrc*, *dblSrc*<br/>
Číselná hodnota, která se má zkopírovat do nového `COleVariant` objektu.

*timeSrc*<br/>
Objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , který se má zkopírovat do nového `COleVariant` objektu.

*arrSrc*<br/>
Objekt [CByteArray](../../mfc/reference/cbytearray-class.md) , který se má zkopírovat do nového `COleVariant` objektu.

*lbSrc*<br/>
Objekt [CLongBinary –](../../mfc/reference/clongbinary-class.md) , který se má zkopírovat do nového `COleVariant` objektu.

*pidl*<br/>
Ukazatel na strukturu [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) , která se má zkopírovat do nového `COleVariant` objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvoří nové `COleVariant` objekty inicializované na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů.

- **COleVariant ()** Vytvoří prázdný `COleVariant` objekt VT_EMPTY.

- **COleVariant (** *varSrc* **)** Zkopíruje existující `VARIANT` objekt nebo `COleVariant` . Typ variant je zachován.

- **COleVariant (** *pSrc* **)** Zkopíruje existující `VARIANT` objekt nebo `COleVariant` . Typ variant je zachován.

- **COleVariant (** *lpszSrc* **)** Zkopíruje řetězec do nového objektu VT_BSTR (UNICODE).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** Zkopíruje řetězec do nového objektu. Parametr *vtSrc* musí být VT_BSTR (Unicode) nebo VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** Zkopíruje řetězec do nového objektu VT_BSTR (UNICODE).

- **COleVariant (** *nSrc* **)** Zkopíruje 8bitové celé číslo do nového objektu VT_UI1.

- **COleVariant (** *nSrc* **,** *vtSrc* **)** Zkopíruje 16bitové celé číslo (nebo logickou hodnotu) do nového objektu. Parametr *vtSrc* musí být VT_I2 nebo VT_BOOL.

- **COleVariant (** *lSrc* **,** *vtSrc* **)** Zkopíruje do nového objektu 32 celé číslo (nebo hodnotu Code). Parametr *vtSrc* musí být VT_I4, VT_ERROR nebo VT_BOOL.

- **COleVariant (** *curSrc* **)** `COleCurrency` Zkopíruje hodnotu do nového objektu VT_CY.

- **COleVariant (** *fltSrc* **)** Zkopíruje hodnotu 32-bit s plovoucí desetinnou čárkou do nového objektu VT_R4.

- **COleVariant (** *dblSrc* **)** Zkopíruje hodnotu 64-bit s plovoucí desetinnou čárkou do nového objektu VT_R8.

- **COleVariant (** *timeSrc* **)** `COleDateTime` Zkopíruje hodnotu do nového objektu VT_DATE.

- **COleVariant (** *arrSrc* **)** `CByteArray` Zkopíruje objekt do nového objektu VT_EMPTY.

- **COleVariant (** *lbSrc* **)** `CLongBinary` Zkopíruje objekt do nového objektu VT_EMPTY.

Další informace o Code naleznete v tématu [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

##  <a name="changetype"></a>COleVariant:: ChangeType

Převede typ hodnoty variant v tomto `COleVariant` objektu.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*VARTYPE*<br/>
VARTYPE pro tento `COleVariant` objekt.

*pSrc*<br/>
Ukazatel na objekt [variant](/windows/win32/api/oaidl/ns-oaidl-variant) , který má být převeden. Pokud je tato hodnota null, je `COleVariant` tento objekt použit jako zdroj pro převod.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [variant](/windows/win32/api/oaidl/ns-oaidl-variant), [VarEnum](/windows/win32/api/wtypes/ne-wtypes-varenum)a [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) položky v Windows SDK.

##  <a name="clear"></a>COleVariant:: Clear

`VARIANT`Vymaže.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Tím se nastaví VARTYPE pro tento objekt na VT_EMPTY. `COleVariant` Destruktor volá tuto funkci.

Další informace naleznete v tématu `VARIANT`, VARTYPE a `VariantClear` záznamech v Windows SDK.

##  <a name="detach"></a>COleVariant::D etach

Odpojí základní objekt [variant](/windows/win32/api/oaidl/ns-oaidl-variant) od tohoto `COleVariant` objektu.

```
VARIANT Detach();
```

### <a name="remarks"></a>Poznámky

Tato funkce nastaví VARTYPE pro tento `COleVariant` objekt na VT_EMPTY.

> [!NOTE]
>  Po volání `Detach`je úkolem volajícího volat `VariantClear` výslednou `VARIANT` strukturu.

Další informace naleznete v tématu [variant](/windows/win32/api/oaidl/ns-oaidl-variant), [VarEnum](/windows/win32/api/wtypes/ne-wtypes-varenum)a [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) položky v Windows SDK.

##  <a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray

Načte bajtové pole z existujícího pole variant.

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*psaný*<br/>
Odkaz na existující objekt [CByteArray](../../mfc/reference/cbytearray-class.md) .

##  <a name="operator_lpcvariant"></a>COleVariant:: operator LPCVARIANT

Tento operátor přetypování vrací `VARIANT` strukturu, jejíž hodnota je zkopírována `COleVariant` z tohoto objektu.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Poznámky

##  <a name="operator_lpvariant"></a>COleVariant:: operator LPVARIANT

Zavolejte Tento operátor přetypování pro přístup k `VARIANT` podkladové `COleVariant` struktuře pro tento objekt.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> Změna hodnoty ve `VARIANT` struktuře, k níž se přistupovalo pomocí ukazatele vráceného touto funkcí, změní hodnotu `COleVariant` tohoto objektu.

##  <a name="operator_eq"></a>COleVariant:: operator =

Tyto přetížené operátory přiřazení zkopírují zdrojové hodnoty do tohoto `COleVariant` objektu.

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

Následuje stručný popis každého operátoru:

- **operator = (** *varSrc* **)** – operátor Zkopíruje existující variantu nebo `COleVariant` objekt do tohoto objektu.

- **operator = (** *pSrc* **)** – operátor Zkopíruje objekt VARIANT, k němuž přistupoval *pSrc* , do tohoto objektu.

- **operator = (** *lpszSrc* **)** – operátor Zkopíruje řetězec zakončený hodnotou null do tohoto objektu a nastaví VARTYPE na VT_BSTR.

- **operator = (** *strSrc* **)** – operátor Zkopíruje objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) do tohoto objektu a nastaví VARTYPE na VT_BSTR.

- **operator = (** *nSrc* **)** – operátor Zkopíruje do tohoto objektu 8bitové celé číslo o hodnotě 8 nebo 16 bitů. Pokud je *nSrc* 8bitové hodnoty, je objekt VARTYPE v této hodnotě nastaven na VT_UI1. Pokud je *nSrc* 16bitová hodnota a jako VARTYPE je to VT_BOOL, je zachovaná; v opačném případě je nastavená na VT_I2.

- **operator = (** *lSrc* **)** – operátor Zkopíruje do tohoto objektu hodnotu 32 celé číslo. Pokud je VARTYPE typu VT_ERROR, je udržována; v opačném případě je nastavená na VT_I4.

- **operator = (** *curSrc* **)** – operátor Zkopíruje objekt [COleCurrency](../../mfc/reference/colecurrency-class.md) do tohoto objektu a nastaví VARTYPE na VT_CY.

- **operator = (** *fltSrc* **)** – operátor Zkopíruje do tohoto objektu hodnotu 32 s plovoucí desetinnou čárkou a nastaví ukazatel VARTYPE na VT_R4.

- **operator = (** *dblSrc* **)** – operátor Zkopíruje do tohoto objektu hodnotu 64 s plovoucí desetinnou čárkou a nastaví ukazatel VARTYPE na VT_R8.

- **operator = (** *dateSrc* **)** – operátor Zkopíruje objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) do tohoto objektu a nastaví VARTYPE na VT_DATE.

- **operator = (** *arrSrc* **)** – operátor Zkopíruje objekt [CByteArray](../../mfc/reference/cbytearray-class.md) do tohoto `COleVariant` objektu.

- **operator = (** *lbSrc* **)** – operátor Zkopíruje objekt [CLongBinary –](../../mfc/reference/clongbinary-class.md) do tohoto `COleVariant` objektu.

Další informace naleznete v tématu [variant](/windows/win32/api/oaidl/ns-oaidl-variant) a [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) položky v Windows SDK.

##  <a name="operator_eq_eq"></a>COleVariant:: operator = = – operátor

Tento operátor porovná dvě hodnoty variant a vrátí nenulovou hodnotu, pokud jsou stejné. v opačném případě 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>COleVariant:: operator &lt;, &lt;&gt;&gt;

`CArchive` `CdumpContext` Vytvoří výstup `COleVariant` `CArchive`hodnoty na nebo a vstup objektu z. `COleVariant`

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

Operátor `COleVariant` vložení ( **\<)podporujediagnostickývýpisa\<** ukládání do archivu. Operátor pro extrakci ( **>>** ) podporuje načítání z archivu.

##  <a name="setstring"></a>COleVariant:: SetString

Nastaví řetězec na konkrétní typ.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parametry

*lpszSrc*<br/>
Řetězec zakončený hodnotou null, který má být zkopírován do `COleVariant` nového objektu.

*VtSrc*<br/>
VARTYPE pro nový `COleVariant` objekt.

### <a name="remarks"></a>Poznámky

Parametr *vtSrc* musí být VT_BSTR (Unicode) nebo VT_BSTRT (ANSI). `SetString`se obvykle používá k nastavení řetězců na ANSI, protože výchozí hodnota pro konstruktor [COleVariant:: COleVariant](#colevariant) s parametrem String nebo String a bez VARTYPE je Unicode.

Sada záznamů DAO v sestavení bez kódování UNICODE očekává, že řetězce budou ANSI. Proto pro funkce DAO, které používají `COleVariant` objekty, pokud nevytváříte sadu záznamů Unicode, je nutné použít formu konstruktoru **COleVariant:: COleVariant (** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavenou na hodnotu VT _BSTRT (ANSI) nebo použít `SetString` s *vtSrc* nastavenou na VT_BSTRT k vytváření řetězců ANSI. Například `CDaoRecordset` funkce [CDaoRecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek) a [CDaoRecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) používají `COleVariant` objekty jako parametry. Tyto objekty musí být ANSI, pokud sada záznamů DAO není UNICODE.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
