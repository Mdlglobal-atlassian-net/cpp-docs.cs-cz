---
title: Ccomvariantní třída
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
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327229"
---
# <a name="ccomvariant-class"></a>Ccomvariantní třída

Tato třída zabalí typ VARIANT a poskytuje člen označující typ uložených dat.

## <a name="syntax"></a>Syntaxe

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomVariant::CcomVariant](#ccomvariant)|Konstruktor|
|[CcomVariant::~CcomVariant](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CcomVariant::Připojit](#attach)|Připojí variantu k `CComVariant` objektu.|
|[CcomVariant::ChangeType](#changetype)|Převede `CComVariant` objekt na nový typ.|
|[CcomVariant::Vymazat](#clear)|Vymaže `CComVariant` objekt.|
|[CcomVariant::Kopírovat](#copy)|Zkopíruje variantu `CComVariant` objektu.|
|[CcomVariant::CopyTo](#copyto)|Zkopíruje obsah `CComVariant` objektu.|
|[CComVariant::Detach](#detach)|Odpojí podkladovou variantu `CComVariant` od objektu.|
|[CcomVariant::GetSize](#getsize)|Vrátí velikost v počtu bajtů obsahu `CComVariant` objektu.|
|[CcomVariant::ReadFromStream](#readfromstream)|Načte variantu z datového proudu.|
|[CcomVariant::Setbyref](#setbyref)|Inicializuje `CComVariant` objekt a `vt` nastaví člen na VT_BYREF.|
|[CcomVariant::WriteToStream](#writetostream)|Uloží základní VARIANT do datového proudu.|

### <a name="public-operators"></a>Veřejné operátory

|||
|-|-|
|[CComVariant::operátor <](#operator_lt)|Označuje, `CComVariant` zda je objekt menší než zadaná varianta.|
|[CComVariant::operátor >](#operator_gt)|Označuje, `CComVariant` zda je objekt větší než zadaná varianta.|
|[operátor !=](#operator_neq)|Označuje, `CComVariant` zda se objekt nerovná zadané variantě.|
|[operátor =](#operator_eq)|Přiřadí objektu `CComVariant` hodnotu.|
|[operátor ==](#operator_eq_eq)|Označuje, `CComVariant` zda se objekt rovná zadané variantě.|

## <a name="remarks"></a>Poznámky

`CComVariant`zabalí typ VARIANT a VARIANTARG, který se skládá z unie a člena označujícího typ dat uložených v unii. Variants se obvykle používají v automatizaci.

`CComVariant`od typ varianty, takže jej lze použít všude tam, kde lze variantu použít. Můžete například použít makro V_VT extrahovat typ `CComVariant` nebo můžete `vt` přistupovat k členu přímo stejně jako u varianty.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CcomVariant::Připojit

Bezpečně vymaže `CComVariant` aktuální obsah objektu, zkopíruje obsah *pSrc* do tohoto objektu, pak nastaví typ varianty *pSrc* na VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[v] Odkazuje na [variantu,](/windows/win32/api/oaidl/ns-oaidl-variant) která má být připojena k objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vlastnictví dat v držení *pSrc* se `CComVariant` přenáší na objekt.

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CcomVariant::CcomVariant

Každý konstruktor zpracovává bezpečnou inicializaci `CComVariant` `VariantInit` objektu voláním funkce Win32 nebo nastavením hodnoty a typu objektu podle předaných parametrů.

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
[v] Nebo `CComVariant` VARIANT slouží k inicializaci objektu. `CComVariant` Obsah zdrojové varianty se zkopíruje do cíle bez převodu.

*lpszSrc*<br/>
[v] Řetězec znaků použitý k inicializaci objektu. `CComVariant` Řetězec znaků s nulovým ukončením (Unicode) můžete předat verzi konstruktoru LPCOLESTR nebo řetězec ANSI do verze LPCSTR. V obou případech je řetězec převeden na Unicode `SysAllocString`BSTR přidělené pomocí . Typ objektu `CComVariant` bude VT_BSTR.

*bSrc*<br/>
[v] **Bool** slouží k inicializaci objektu. `CComVariant` Argument **bool** je před uložením převeden na VARIANT_BOOL. Typ objektu `CComVariant` bude VT_BOOL.

*nSrc*<br/>
[v] **Int**, **BYTE**, **short**, **long**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**nebo **unsigned int** used to initialize the `CComVariant` object. Typ objektu `CComVariant` bude VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 nebo VT_UI4.

*vtSrc řekl:*<br/>
[v] Typ varianty. Pokud je první parametr **int**, platné typy jsou VT_I4 a VT_INT. Pokud je první parametr **dlouhý**, jsou VT_I4 a VT_ERROR platné typy. Pokud je první parametr **double**, platné typy jsou VT_R8 a VT_DATE. Pokud je první parametr **nepodepsaný int**, platné typy jsou VT_UI4 a VT_UINT.

*fltSrc řekl:*<br/>
[v] **Float** slouží k inicializaci objektu. `CComVariant` Typ objektu `CComVariant` bude VT_R4.

*dblSrc*<br/>
[v] **Double** slouží k inicializaci objektu. `CComVariant` Typ objektu `CComVariant` bude VT_R8.

*cySrc*<br/>
[v] Slouží `CY` k inicializaci objektu. `CComVariant` Typ objektu `CComVariant` bude VT_CY.

*pSrc*<br/>
[v] Ukazatel `IDispatch` `IUnknown` nebo použitý k inicializaci objektu. `CComVariant` `AddRef`bude volána na ukazatel rozhraní. Typ objektu `CComVariant` bude VT_DISPATCH nebo VT_UNKNOWN.

Nebo ukazatel SAFERRAY slouží k inicializaci objektu. `CComVariant` Kopie SAFEARRAY je uložena `CComVariant` v objektu. Typ objektu `CComVariant` bude kombinací původního typu SAFEARRAY a VT_ARRAY.

*Csrc*<br/>
[v] **Znak** použitý k inicializaci objektu. `CComVariant` Typ objektu `CComVariant` bude VT_I1.

*bstrSrc řekl:*<br/>
[v] BSTR slouží k inicializaci objektu. `CComVariant` Typ objektu `CComVariant` bude VT_BSTR.

### <a name="remarks"></a>Poznámky

Destruktor spravuje vyčištění voláním [CComVariant::Clear](#clear).

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CcomVariant::~CcomVariant

Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda spravuje vyčištění voláním [CComVariant::Clear](#clear).

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CcomVariant::ChangeType

Převede `CComVariant` objekt na nový typ.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vtNew*<br/>
[v] Nový typ pro `CComVariant` objekt.

*pSrc*<br/>
[v] Ukazatel na VARIANT, jehož hodnota bude převedena na nový typ. Výchozí hodnota je NULL, `CComVariant` což znamená, že objekt bude převeden na místě.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu pro `ChangeType` *pSrc*, použije tuto VARIANTu jako zdroj pro převod. V opačném `CComVariant` případě bude objekt zdrojem.

## <a name="ccomvariantclear"></a><a name="clear"></a>CcomVariant::Vymazat

Vymaže `CComVariant` objekt `VariantClear` voláním funkce Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Destruktor automaticky `Clear`volá .

## <a name="ccomvariantcopy"></a><a name="copy"></a>CcomVariant::Kopírovat

Uvolní `CComVariant` objekt a pak mu přiřadí kopii zadané varianty.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[v] Ukazatel na [variantu,](/windows/win32/api/oaidl/ns-oaidl-variant) která má být zkopírována.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>CcomVariant::CopyTo

Zkopíruje obsah `CComVariant` objektu.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parametry

*pstrDest*<br/>
Odkazuje na BSTR, který obdrží kopii `CComVariant` obsahu objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Objekt `CComVariant` musí být typu VT_BSTR.

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant::Detach

Odpojí podkladovou variantu `CComVariant` od objektu a nastaví typ objektu na VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
[out] Vrátí podkladovou hodnotu VARIANT objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Všimněte si, že obsah VARIANT odkazuje *pDest* bude automaticky vymazány před přiřazenhodnotu a typ volajícího `CComVariant` objektu.

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CcomVariant::GetSize

Pro jednoduché pevné velikosti VARIANTs tato metoda vrátí **velikost** základní datový typ plus **sizeof(VARTYPE)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost aktuálního obsahu `CComVariant` objektu v bajtech.

### <a name="remarks"></a>Poznámky

Pokud varianta obsahuje ukazatel `GetSize` rozhraní, `IPersistStream` `IPersistStreamInit`dotazy pro nebo . Pokud je úspěšná, vrácená hodnota je nižší pořadí 32 bitů hodnoty vrácené plus `GetSizeMax` **velikost** CLSID a **sizeof(VARTYPE)**. Pokud je ukazatel rozhraní `GetSize` NULL, vrátí **velikost** CLSID plus **sizeof (VARTYPE)**. Pokud je celková velikost `GetSize` větší než ULONG_MAX, vrátí **sizeof(VARTYPE),** což znamená chybu.

Ve všech ostatních případech je z aktuální varianty vytanována dočasná varianta typu VT_BSTR. Délka tohoto BSTR se vypočítá jako velikost délky řetězce plus délka samotného řetězce plus velikost znaku null plus **sizeof(VARTYPE)**. Pokud varianta nelze dotáhovat na VARIANT `GetSize` typu VT_BSTR, vrátí **sizeof(VARTYPE)**.

Velikost vrácená touto metodou odpovídá počtu bajtů používaných [CComVariant::WriteToStream](#writetostream) za úspěšných podmínek.

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant::operátor =

Přiřadí `CComVariant` objektu hodnotu a odpovídající typ.

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
[v] Nebo `CComVariant` [VARIANTa,](/windows/win32/api/oaidl/ns-oaidl-variant) která `CComVariant` má být přiřazena k objektu. Obsah zdrojové varianty se zkopíruje do cíle bez převodu.

*bstrSrc řekl:*<br/>
[v] BSTR, které mají `CComVariant` být přiřazeny k objektu. Typ objektu `CComVariant` bude VT_BSTR.

*lpszSrc*<br/>
[v] Řetězec znaků, který má `CComVariant` být přiřazen k objektu. Řetězec znaků s nulovým ukončením (Unicode) můžete předat lpcolestr verzi operátoru nebo ansi řetězec na verzi LPCSTR. V obou případech je řetězec převeden na Unicode BSTR přidělené pomocí `SysAllocString`. Typ objektu `CComVariant` bude VT_BSTR.

*bSrc*<br/>
[v] **Bool,** který má `CComVariant` být přiřazen k objektu. Argument **bool** je před uložením převeden na VARIANT_BOOL. Typ objektu `CComVariant` bude VT_BOOL.

*nSrc*<br/>
[v] **Int**, BYTE, **short**, **long**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**nebo **unsigned int,** které mají být přiřazeny k objektu. `CComVariant` Typ objektu `CComVariant` bude VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 nebo VT_UI4.

*fltSrc řekl:*<br/>
[v] **Plovoucí,** které mají `CComVariant` být přiřazeny k objektu. Typ objektu `CComVariant` bude VT_R4.

*dblSrc*<br/>
[v] **Double,** které mají `CComVariant` být přiřazeny k objektu. Typ objektu `CComVariant` bude VT_R8.

*cySrc*<br/>
[v] Chcete-li `CY` přiřadit `CComVariant` k objektu. Typ objektu `CComVariant` bude VT_CY.

*pSrc*<br/>
[v] Ukazatel `IDispatch` `IUnknown` nebo ukazatel, který `CComVariant` má být přiřazen k objektu. `AddRef`bude volána na ukazatel rozhraní. Typ objektu `CComVariant` bude VT_DISPATCH nebo VT_UNKNOWN.

Nebo ukazatel SAFEARRAY, který má `CComVariant` být přiřazen k objektu. Kopie SAFEARRAY je uložena `CComVariant` v objektu. Typ objektu `CComVariant` bude kombinací původního typu SAFEARRAY a VT_ARRAY.

*Csrc*<br/>
[v] Znak, který má `CComVariant` být přiřazen k objektu. Typ objektu `CComVariant` bude VT_I1.

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant::operátor ==

Označuje, `CComVariant` zda se objekt rovná zadané variantě.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu PRAVDA, pokud se hodnota a typ *varSrc* rovná `CComVariant` hodnotě a typu objektu. V opačném případě NEPRAVDA. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

Operátor porovná pouze hodnotu typů variant. Porovnává řetězce, celá čísla a plovoucí body, ale ne pole nebo záznamy.

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant::operátor !=

Označuje, `CComVariant` zda se objekt nerovná zadané variantě.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu PRAVDA, pokud se hodnota nebo typ *varSrc* nerovná hodnotě nebo typu objektu. `CComVariant` V opačném případě NEPRAVDA. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

Operátor porovná pouze hodnotu typů variant. Porovnává řetězce, celá čísla a plovoucí body, ale ne pole nebo záznamy.

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CComVariant::operátor&lt;

Označuje, `CComVariant` zda je objekt menší než zadaná varianta.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu PRAVDA, `CComVariant` pokud je hodnota objektu menší než hodnota *varSrc*. V opačném případě NEPRAVDA. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CComVariant::operátor&gt;

Označuje, `CComVariant` zda je objekt větší než zadaná varianta.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu PRAVDA, `CComVariant` pokud je hodnota objektu větší než hodnota *varSrc*. V opačném případě NEPRAVDA. Operátor používá výchozí národní prostředí uživatele k provedení porovnání.

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>CcomVariant::ReadFromStream

Nastaví základní VARIANTa varianta obsažené v zadaném datovém proudu.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[v] Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) na datovém proudu obsahující data.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`ReadToStream`vyžaduje předchozí volání [WriteToStream](#writetostream).

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>CcomVariant::Setbyref

Inicializuje `CComVariant` objekt a `vt` nastaví člen na VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ VARIANT, například BSTR, **int**nebo **char**.

*Pt*<br/>
Ukazatel použitý k inicializaci objektu. `CComVariant`

### <a name="remarks"></a>Poznámky

`SetByRef`je šablona funkce, která `CComVariant` inicializuje objekt na `vt` ukazatel *pT* a nastaví člen na VT_BYREF. Příklad:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>CcomVariant::WriteToStream

Uloží základní VARIANT do datového proudu.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[v] Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) v datovém proudu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
