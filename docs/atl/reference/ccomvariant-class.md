---
title: CComVariant – třída
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: b4c157435aaffab5f1315fd4636f55f9d4e0d5b4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496863"
---
# <a name="ccomvariant-class"></a>CComVariant – třída

Tato třída zalomí typ VARIANT a poskytne člen označující typ uložených dat.

## <a name="syntax"></a>Syntaxe

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Konstruktor|
|[CComVariant::~CComVariant](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Připojí k `CComVariant` objektu variantu.|
|[CComVariant::ChangeType](#changetype)|`CComVariant` Převede objekt na nový typ.|
|[CComVariant::Clear](#clear)|`CComVariant` Vymaže objekt.|
|[CComVariant:: Copy](#copy)|Zkopíruje do `CComVariant` objektu variant.|
|[CComVariant:: CopyTo](#copyto)|Zkopíruje obsah `CComVariant` objektu.|
|[CComVariant::Detach](#detach)|Odpojí základní variant od `CComVariant` objektu.|
|[CComVariant:: GetSize](#getsize)|Vrátí velikost v počtu bajtů obsahu `CComVariant` objektu.|
|[CComVariant::ReadFromStream](#readfromstream)|Načte typ VARIANT z datového proudu.|
|[CComVariant::SetByRef](#setbyref)|Inicializuje objekt a `vt` nastaví člena na VT_BYREF. `CComVariant`|
|[CComVariant::WriteToStream](#writetostream)|Uloží základní VARIANTu do datového proudu.|

### <a name="public-operators"></a>Veřejné operátory

|||
|-|-|
|[CComVariant:: operator <](#operator_lt)|Označuje, zda `CComVariant` je objekt menší než zadaný typ variant.|
|[CComVariant:: operator >](#operator_gt)|Označuje, zda `CComVariant` je objekt větší než zadaný typ variant.|
|[! = – operátor](#operator_neq)|Určuje, zda `CComVariant` se objekt nerovná zadanému typu variant.|
|[operátor =](#operator_eq)|Přiřadí hodnotu `CComVariant` objektu.|
|[operator = = – operátor](#operator_eq_eq)|Označuje, zda `CComVariant` se objekt rovná zadanému typu variant.|

## <a name="remarks"></a>Poznámky

`CComVariant`zalomí typ VARIANT a VARIANTARG, který se skládá z sjednocení a členu, který označuje typ dat uložených ve sjednocení. Varianty se obvykle používají ve službě Automation.

`CComVariant`je odvozen z typu VARIANT, aby jej bylo možné použít všude, kde lze použít VARIANTu. Můžete například použít makro V_VT k extrakci typu `CComVariant` nebo nebo můžete `vt` přistupovat ke členu přímo stejně jako s variantou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atlcomcli. h

##  <a name="attach"></a>CComVariant:: Attach

Bezpečně vymaže aktuální obsah `CComVariant` objektu, zkopíruje obsah *pSrc* do tohoto objektu a pak nastaví typ variant *pSrc* na VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
pro Odkazuje na [variantu](/windows/win32/api/oaidl/ns-oaidl-variant) , která má být připojena k objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vlastnictví dat uchovávaných v *pSrc* se přenese do `CComVariant` objektu.

##  <a name="ccomvariant"></a>CComVariant::CComVariant

Každý konstruktor zpracovává bezpečnou inicializaci `CComVariant` objektu `VariantInit` voláním funkce Win32 nebo nastavením hodnoty objektu a typu podle předaných parametrů.

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
pro Variantu použitou k `CComVariant` inicializaci objektu. `CComVariant` Obsah zdrojové varianty se zkopíruje do cíle bez převodu.

*lpszSrc*<br/>
pro Řetězec znaků použitý k inicializaci `CComVariant` objektu. Do verze LPCOLESTR konstruktoru nebo řetězce ANSI pro LPCSTR verzi můžete předat řetězec znaků s nulovou zakončenou (Unicode). V obou případech je řetězec převeden na rozhraní Unicode BSTR přidělené pomocí `SysAllocString`. Typ `CComVariant` objektu bude VT_BSTR.

*bSrc*<br/>
pro **Logická** hodnota použitá k inicializaci `CComVariant` objektu. Argument **bool** je před uložením převeden na VARIANT_BOOL. Typ `CComVariant` objektu bude VT_BOOL.

*nSrc*<br/>
pro **Int**, **Byte**, **short**, **Long**, LongLong, ULONGLONG, **unsigned short**, unsigned **Long**nebo **unsigned int** sloužící k inicializaci `CComVariant` objektu. Typ `CComVariant` objektu bude VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 nebo VT_UI4, v uvedeném pořadí.

*vtSrc*<br/>
pro Typ variant. Pokud je první parametr **int**, platné typy jsou VT_I4 a VT_INT. Pokud je první parametr **dlouhý**, platné typy jsou VT_I4 a VT_ERROR. Pokud je první parametr **Double**, platné typy jsou VT_R8 a VT_DATE. Pokud je první parametr **bez znaménka int**, platné typy jsou VT_UI4 a VT_UINT.

*fltSrc*<br/>
pro Typ **float** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objektu bude VT_R4.

*dblSrc*<br/>
pro **Typ Double** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objektu bude VT_R8.

*cySrc*<br/>
pro `CY` Slouží k`CComVariant` inicializaci objektu. Typ `CComVariant` objektu bude VT_CY.

*pSrc*<br/>
pro Ukazatel nebo použitý`IUnknown` k inicializaci objektu.`CComVariant` `IDispatch` `AddRef`bude volána na ukazatel rozhraní. Typ `CComVariant` objektu bude VT_DISPATCH nebo VT_UNKNOWN, v uvedeném pořadí.

Nebo, ukazatel SAFERRAY použitý k inicializaci `CComVariant` objektu. Kopie třídy SAFEARRAY je uložena v `CComVariant` objektu. Typ `CComVariant` objektu bude kombinací původního typu SafeArray a VT_ARRAY.

*cSrc*<br/>
pro **Znak** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objektu bude VT_I1.

*bstrSrc*<br/>
pro `CComVariant` Objekt BSTR použitý k inicializaci objektu. Typ `CComVariant` objektu bude VT_BSTR.

### <a name="remarks"></a>Poznámky

Destruktor spravuje vyčištění voláním [CComVariant:: Clear](#clear).

##  <a name="dtor"></a>CComVariant:: ~ CComVariant

Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda spravuje vyčištění voláním [CComVariant:: Clear](#clear).

##  <a name="changetype"></a>CComVariant:: ChangeType

`CComVariant` Převede objekt na nový typ.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vtNew*<br/>
pro Nový typ pro `CComVariant` objekt.

*pSrc*<br/>
pro Ukazatel na VARIANTu, jehož hodnota bude převedena na nový typ. Výchozí hodnota je null, což znamená, `CComVariant` že se objekt převede na místo.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu pro *pSrc*, `ChangeType` použije tuto variantu jako zdroj pro převod. V opačném případě bude objektzdrojem.`CComVariant`

##  <a name="clear"></a>CComVariant:: Clear

Vymaže objekt vyvoláním funkce `VariantClear`Win32. `CComVariant`

```
HRESULT Clear();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Destruktor automaticky volá `Clear`.

##  <a name="copy"></a>CComVariant:: Copy

`CComVariant` Uvolní objekt a pak mu přiřadí kopii zadané varianty.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
pro Ukazatel na variantu [](/windows/win32/api/oaidl/ns-oaidl-variant) , která se má zkopírovat

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="copyto"></a>CComVariant:: CopyTo

Zkopíruje obsah `CComVariant` objektu.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parametry

*pstrDest*<br/>
Odkazuje na objekt BSTR, který obdrží kopii obsahu `CComVariant` objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`CComVariant` Objekt musí být typu VT_BSTR.

##  <a name="detach"></a>CComVariant::D etach

Odpojí základní variant od `CComVariant` objektu a nastaví typ objektu na VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
mimo Vrátí podkladovou hodnotu VARIANT objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Všimněte si, že obsah variant, na který odkazuje *pDest* , bude automaticky vymazán před přiřazením hodnoty a typu volajícího `CComVariant` objektu.

##  <a name="getsize"></a>CComVariant:: GetSize

V případě jednoduchých velikostí variant vrátí tato metoda **operátor sizeof** základní datový typ plus **sizeof (VARTYPE)** .

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost v bajtech aktuálního obsahu `CComVariant` objektu.

### <a name="remarks"></a>Poznámky

Pokud varianta obsahuje ukazatel rozhraní, `GetSize` dotazy pro `IPersistStream` nebo `IPersistStreamInit`. Je-li to úspěšné, vrácená hodnota je nižší než 32 bitů hodnoty vrácené `GetSizeMax` hodnotou a operátorem **sizeof** a CLSID a **sizeof (VARTYPE)** . Pokud je ukazatel rozhraní null, `GetSize` vrátí hodnotu **sizeof** a identifikátor CLSID plus **sizeof (VARTYPE)** . Pokud je celková velikost větší než ULONG_MAX, vrátí `GetSize` **sizeof (VARTYPE)** , což označuje chybu.

Ve všech ostatních případech je dočasná varianta typu VT_BSTR převedena z aktuální varianty. Délka tohoto BSTR je počítána jako velikost řetězce a délka samotného řetězce plus velikost znaku null plus **sizeof (VARTYPE)** . Pokud variantu nemůže být převedena na variantu typu VT_BSTR, `GetSize` vrátí **sizeof (VARTYPE)** .

Velikost vrácená touto metodou odpovídá počtu bajtů využívaných funkcí [CComVariant:: WriteToStream](#writetostream) za úspěšných podmínek.

##  <a name="operator_eq"></a>CComVariant:: operator =

Přiřadí hodnotu a odpovídající typ `CComVariant` objektu.

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
pro Variantu `CComVariant` nebo, která má být přiřazena objektu. [](/windows/win32/api/oaidl/ns-oaidl-variant) `CComVariant` Obsah zdrojové varianty se zkopíruje do cíle bez převodu.

*bstrSrc*<br/>
pro BSTR, který má být přiřazen `CComVariant` objektu. Typ `CComVariant` objektu bude VT_BSTR.

*lpszSrc*<br/>
pro Řetězec znaků, který má být přiřazen `CComVariant` objektu. Můžete předat řetězec znaků (Unicode) s nulovou šířkou (Unicode) do verze LPCOLESTR operátoru nebo řetězcem ANSI do verze LPCSTR. V obou případech je řetězec převeden na rozhraní Unicode BSTR přidělené pomocí `SysAllocString`. Typ `CComVariant` objektu bude VT_BSTR.

*bSrc*<br/>
pro **Logická** hodnota, která má být přiřazena `CComVariant` objektu. Argument **bool** je před uložením převeden na VARIANT_BOOL. Typ `CComVariant` objektu bude VT_BOOL.

*nSrc*<br/>
pro **Int**, Byte, **short**, **Long**, LongLong, ULONGLONG, **unsigned short**, unsigned **Long**nebo **unsigned int** pro přiřazení k `CComVariant` objektu. Typ `CComVariant` objektu bude VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 nebo VT_UI4, v uvedeném pořadí.

*fltSrc*<br/>
pro Typ **float** , který má být přiřazen `CComVariant` objektu. Typ `CComVariant` objektu bude VT_R4.

*dblSrc*<br/>
pro **Dvojnásobek** , který má být přiřazen `CComVariant` objektu. Typ `CComVariant` objektu bude VT_R8.

*cySrc*<br/>
pro `CComVariant` Objekt, `CY` který má být přiřazen objektu. Typ `CComVariant` objektu bude VT_CY.

*pSrc*<br/>
pro Ukazatel `IDispatch` nebo `IUnknown` ,`CComVariant` který má být přiřazen objektu. `AddRef`bude volána na ukazatel rozhraní. Typ `CComVariant` objektu bude VT_DISPATCH nebo VT_UNKNOWN, v uvedeném pořadí.

Nebo, ukazatel SAFEARRAY, který má být přiřazen `CComVariant` objektu. Kopie třídy SAFEARRAY je uložena v `CComVariant` objektu. Typ `CComVariant` objektu bude kombinací původního typu SafeArray a VT_ARRAY.

*cSrc*<br/>
pro Znak, který má být přiřazen `CComVariant` objektu. Typ `CComVariant` objektu bude VT_I1.

##  <a name="operator_eq_eq"></a>CComVariant:: operator = = – operátor

Označuje, zda `CComVariant` se objekt rovná zadanému typu variant.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu true, `CComVariant` Pokud je hodnota a typ *varSrc* rovna hodnotě a typu v daném pořadí objektu. V opačném případě FALSE. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

Operátor porovná pouze hodnotu typů variant. Porovnává řetězce, celá čísla a plovoucí body, ale ne pole nebo záznamy.

##  <a name="operator_neq"></a>CComVariant:: operator! =

Určuje, zda `CComVariant` se objekt nerovná zadanému typu variant.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu true, `CComVariant` Pokud buď hodnota nebo typ *varSrc* není rovna hodnotě nebo typu v daném objektu. V opačném případě FALSE. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

Operátor porovná pouze hodnotu typů variant. Porovnává řetězce, celá čísla a plovoucí body, ale ne pole nebo záznamy.

##  <a name="operator_lt"></a>CComVariant:: operator&lt;

Označuje, zda `CComVariant` je objekt menší než zadaný typ variant.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu true, pokud je hodnota `CComVariant` objektu menší než hodnota *varSrc*. V opačném případě FALSE. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

##  <a name="operator_gt"></a>CComVariant:: operator&gt;

Označuje, zda `CComVariant` je objekt větší než zadaný typ variant.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu true, pokud je hodnota `CComVariant` objektu větší než hodnota *varSrc*. V opačném případě FALSE. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

##  <a name="readfromstream"></a>CComVariant::ReadFromStream

Nastaví základní VARIANTu na VARIANTu obsaženou v zadaném datovém proudu.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
pro Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) na datovém proudu, který obsahuje data.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`ReadToStream`vyžaduje předchozí volání [WriteToStream](#writetostream).

##  <a name="setbyref"></a>CComVariant::SetByRef

Inicializuje objekt a `vt` nastaví člena na VT_BYREF. `CComVariant`

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ VARIANT, například BSTR, **int**nebo **char**.

*pT*<br/>
Ukazatel použitý k inicializaci `CComVariant` objektu.

### <a name="remarks"></a>Poznámky

`SetByRef`je šablonou funkce, která inicializuje `CComVariant` objekt na ukazatel *PT* a nastaví `vt` člena na VT_BYREF. Příklad:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>CComVariant::WriteToStream

Uloží základní VARIANTu do datového proudu.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
pro Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) v datovém proudu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
