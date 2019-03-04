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
ms.openlocfilehash: 6be05b52b96ada7871f955c687036a83b4e0b493
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281093"
---
# <a name="ccomvariant-class"></a>CComVariant – třída

Tato třída zabalí typ VARIANT, poskytování člen označující typ dat uložených.

## <a name="syntax"></a>Syntaxe

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Konstruktor|
|[CComVariant::~CComVariant](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Připojí hodnotu typu VARIANT pro `CComVariant` objektu.|
|[CComVariant::ChangeType](#changetype)|Převede `CComVariant` na nový typ objektu.|
|[CComVariant::Clear](#clear)|Vymaže `CComVariant` objektu.|
|[CComVariant::Copy](#copy)|Kopíruje hodnotu typu VARIANT pro `CComVariant` objektu.|
|[CComVariant::CopyTo](#copyto)|Zkopíruje obsah `CComVariant` objektu.|
|[CComVariant::Detach](#detach)|Odpojí základní typ VARIANT z `CComVariant` objektu.|
|[CComVariant::GetSize](#getsize)|Vrátí velikost v bajtech obsah `CComVariant` objektu.|
|[CComVariant::ReadFromStream](#readfromstream)|Načte hodnotu typu VARIANT z datového proudu.|
|[CComVariant::SetByRef](#setbyref)|Inicializuje `CComVariant` objekt a nastaví `vt` člen VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Základní typ VARIANT uloží do datového proudu.|

### <a name="public-operators"></a>Veřejné operátory

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|Určuje, zda `CComVariant` je objekt menší než zadaný typ VARIANT.|
|[CComVariant::operator >](#operator_gt)|Určuje, zda `CComVariant` objekt je větší než zadaný typ VARIANT.|
|[Operator! =](#operator_neq)|Určuje, zda `CComVariant` objektu se nerovná zadaný typ VARIANT.|
|[operátor =](#operator_eq)|Přiřadí hodnotu k `CComVariant` objektu.|
|[Operator ==](#operator_eq_eq)|Určuje, zda `CComVariant` objekt rovná zadaný typ VARIANT.|

## <a name="remarks"></a>Poznámky

`CComVariant` zabalí VARIANT a VARIANTARG typ, který se skládá z sjednocení a člen určující typ dat uložených ve sjednocení. Varianty se obvykle používají ve službě Automation.

`CComVariant` je odvozen z typu VARIANT, dá se použít bez ohledu na to je možné hodnotu typu VARIANT. Makra V_VT můžete použít například k extrakci typu `CComVariant` lze získat přístup `vt` člen přímo stejně jako u hodnotu typu VARIANT.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

##  <a name="attach"></a>  CComVariant::Attach

Bezpečně vymaže aktuální obsah `CComVariant` objektu, zkopíruje obsah *pSrc* do tohoto objektu, pak nastaví typ variant *pSrc* VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[in] Odkazuje [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) bude připojený k objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Vlastnictví data ukládaná společností *pSrc* je předána `CComVariant` objektu.

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

Bezpečná inicializace zpracovává každý konstruktoru `CComVariant` objektu voláním `VariantInit` funkci Win32 nebo tak, že nastavíte hodnotu a typ podle parametrů předaných objektu.

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
[in] `CComVariant` Nebo VARIANTU použít k inicializaci `CComVariant` objektu. Obsah objektu variant zdroje se zkopíruje do cíle bez převodu.

*lpszSrc*<br/>
[in] Znakový řetězec používaný k inicializaci `CComVariant` objektu. Ukončit nulou široké (Unicode) řetězec znaků můžete předat LPCOLESTR verzi konstruktoru nebo řetězce ANSI na LPCSTR verzi. V obou případech je daný řetězec převést na Unicode BSTR přidělena pomocí `SysAllocString`. Typ `CComVariant` objekt se bude VT_BSTR.

*bSrc*<br/>
[in] **Bool** použitý k inicializaci `CComVariant` objektu. **Bool** argument je převeden na VARIANT_BOOL před uložené. Typ `CComVariant` objekt se bude VT_BOOL.

*nSrc*<br/>
[in] **Int**, **BAJTŮ**, **krátký**, **dlouhé**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**, nebo **unsigned int** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objektu bude VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 nebo VT_UI4, v uvedeném pořadí.

*vtSrc*<br/>
[in] Typ objektu variant. Pokud je první parametr **int**, platné typy jsou VT_I4 a VT_INT. Pokud je první parametr **dlouhé**, platné typy jsou VT_I4 a VT_ERROR. Pokud je první parametr **double**, platné typy jsou VT_R8 a VT_DATE. Pokud je první parametr **unsigned int**, platné typy jsou VT_UI4 a VT_UINT.

*fltSrc*<br/>
[in] **Float** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_R4.

*dblSrc*<br/>
[in] **Double** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_R8.

*cySrc*<br/>
[in] `CY` Použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_CY.

*pSrc*<br/>
[in] `IDispatch` Nebo `IUnknown` použitý k inicializaci ukazatele `CComVariant` objektu. `AddRef` bude volána na ukazatel rozhraní. Typ `CComVariant` objekt se bude VT_DISPATCH nebo VT_UNKNOWN, v uvedeném pořadí.

Nebo použít k inicializaci ukazatele SAFERRAY `CComVariant` objektu. Kopie třídy SAFEARRAY je uložena v `CComVariant` objektu. Typ `CComVariant` objekt se bude kombinací původní typ SAFEARRAY a VT_ARRAY.

*cSrc*<br/>
[in] **Char** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_I1.

*bstrSrc*<br/>
[in] BSTR použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_BSTR.

### <a name="remarks"></a>Poznámky

Destruktor spravuje vyčištění voláním [CComVariant::Clear](#clear).

##  <a name="dtor"></a>  CComVariant:: ~ CComVariant

Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda spravuje vyčištění voláním [CComVariant::Clear](#clear).

##  <a name="changetype"></a>  CComVariant::ChangeType

Převede `CComVariant` na nový typ objektu.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vtNew*<br/>
[in] Nový typ pro `CComVariant` objektu.

*pSrc*<br/>
[in] Ukazatel na typ VARIANT, jejichž hodnoty se převedou na nový typ. Výchozí hodnota je NULL, tj. `CComVariant` objektu se převedou na místě.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu *pSrc*, `ChangeType` použije tato varianta jako zdroj pro převod. V opačném případě `CComVariant` objektu bude sloužit jako zdroj.

##  <a name="clear"></a>  CComVariant::Clear

Vymaže `CComVariant` objektu voláním `VariantClear` funkci Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Destruktor automaticky volá `Clear`.

##  <a name="copy"></a>  CComVariant::Copy

Uvolňuje `CComVariant` objektu a přiřadí ji kopii zadaný typ VARIANT.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[in] Ukazatel [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) ke zkopírování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="copyto"></a>  CComVariant::CopyTo

Zkopíruje obsah `CComVariant` objektu.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parametry

*pstrDest*<br/>
Odkazuje na BSTR, který obdrží kopii obsah `CComVariant` objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`CComVariant` Objekt musí být typu VT_BSTR.

##  <a name="detach"></a>  CComVariant::Detach

Odpojí základní typ VARIANT z `CComVariant` objekt a nastaví typ objektu VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
[out] Vrátí zdrojovou hodnotu typu VARIANT objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Všimněte si, že obsah objektu VARIANT odkazuje *pDest* bude automaticky vymazán před přiřazením hodnotu a typ volající `CComVariant` objektu.

##  <a name="getsize"></a>  CComVariant::GetSize

Pro varianty jednoduchý pevnou velikost, vrátí tato metoda **sizeof** příslušný datový typ plus **sizeof(VARTYPE)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost v bajtech aktuální obsah `CComVariant` objektu.

### <a name="remarks"></a>Poznámky

Pokud varianty obsahuje ukazatel rozhraní, `GetSize` dotazuje `IPersistStream` nebo `IPersistStreamInit`. Pokud úspěšná, vrácená hodnota je 32 bity nižšího řádu hodnoty vrácené `GetSizeMax` plus **sizeof** CLSID a **sizeof(VARTYPE)**. Pokud má hodnotu NULL, je ukazatel rozhraní `GetSize` vrátí **sizeof** identifikátor CLSID plus **sizeof(VARTYPE)**. Pokud celková velikost je větší než ULONG_MAX, `GetSize` vrátí **sizeof(VARTYPE)** což znamená chybu.

Ve všech ostatních případech je dočasný VARIANT typu VT_BSTR převést z aktuálního typu VARIANT. Délka tohoto BSTR se počítá jako velikost délku řetězce včetně délky samotný řetězec plus velikost znak null, plus **sizeof(VARTYPE)**. Pokud varianty nelze převést na hodnotu typu VARIANT typu VT_BSTR, `GetSize` vrátí **sizeof(VARTYPE)**.

Velikost vrácený touto metodou shoduje s počtem bajtů používané [CComVariant::WriteToStream](#writetostream) úspěšné podmínek.

##  <a name="operator_eq"></a>  CComVariant::operator =

Přiřadí hodnotu a odpovídající typ, který má `CComVariant` objektu.

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
[in] `CComVariant` Nebo [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) přiřazení `CComVariant` objektu. Obsah objektu variant zdroje se zkopíruje do cíle bez převodu.

*bstrSrc*<br/>
[in] BSTR má být přiřazena k `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_BSTR.

*lpszSrc*<br/>
[in] Řetězec znaků, který má být přiřazena k `CComVariant` objektu. Ukončit nulou široké (Unicode) řetězec znaků můžete předat LPCOLESTR verzi operátor nebo řetězce ANSI na LPCSTR verzi. V obou případech se daný řetězec převést na Unicode BSTR přidělena pomocí `SysAllocString`. Typ `CComVariant` objekt se bude VT_BSTR.

*bSrc*<br/>
[in] **Bool** přiřazení `CComVariant` objektu. **Bool** argument je převeden na VARIANT_BOOL před uložené. Typ `CComVariant` objekt se bude VT_BOOL.

*nSrc*<br/>
[in] **Int**, BYTE, **krátký**, **dlouhé**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**, nebo **unsigned int** přiřazení `CComVariant` objektu. Typ `CComVariant` objektu bude VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 nebo VT_UI4, v uvedeném pořadí.

*fltSrc*<br/>
[in] **Float** přiřazení `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_R4.

*dblSrc*<br/>
[in] **Double** přiřazení `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_R8.

*cySrc*<br/>
[in] `CY` Přiřazení `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_CY.

*pSrc*<br/>
[in] `IDispatch` Nebo `IUnknown` ukazatele pro přiřazení `CComVariant` objektu. `AddRef` bude volána na ukazatel rozhraní. Typ `CComVariant` objekt se bude VT_DISPATCH nebo VT_UNKNOWN, v uvedeném pořadí.

Nebo ukazatel SAFEARRAY pro přiřazení `CComVariant` objektu. Kopie třídy SAFEARRAY je uložena v `CComVariant` objektu. Typ `CComVariant` objekt se bude kombinací původní typ SAFEARRAY a VT_ARRAY.

*cSrc*<br/>
[in] Znak, který má být přiřazena k `CComVariant` objektu. Typ `CComVariant` objekt se bude VT_I1.

##  <a name="operator_eq_eq"></a>  CComVariant::operator ==

Určuje, zda `CComVariant` objekt rovná zadaný typ VARIANT.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí TRUE, pokud hodnotu a typ *varSrc* rovnají hodnotu a typ, v uvedeném pořadí, `CComVariant` objektu. V opačném případě hodnota FALSE. Operátor, který se používá k provádění porovnání výchozí národní prostředí uživatele.

Operátor, který se porovnává pouze hodnotu typu variant. Porovná řetězce, celých čísel a s plovoucí desetinnou čárkou body, ale není pole nebo záznamy.

##  <a name="operator_neq"></a>  CComVariant::operator! =

Určuje, zda `CComVariant` objektu se nerovná zadaný typ VARIANT.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí TRUE, pokud hodnota nebo typ *varSrc* není shodný s hodnotou nebo typu, v uvedeném pořadí, `CComVariant` objektu. V opačném případě hodnota FALSE. Operátor, který se používá k provádění porovnání výchozí národní prostředí uživatele.

Operátor, který se porovnává pouze hodnotu typu variant. Porovná řetězce, celých čísel a s plovoucí desetinnou čárkou body, ale není pole nebo záznamy.

##  <a name="operator_lt"></a>  CComVariant::operator &lt;

Určuje, zda `CComVariant` je objekt menší než zadaný typ VARIANT.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí TRUE, pokud hodnota `CComVariant` je objekt menší než hodnota *varSrc*. V opačném případě hodnota FALSE. Operátor, který se používá k provádění porovnání výchozí národní prostředí uživatele.

##  <a name="operator_gt"></a>  CComVariant::operator &gt;

Určuje, zda `CComVariant` objekt je větší než zadaný typ VARIANT.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí TRUE, pokud hodnota `CComVariant` objekt je větší než hodnota *varSrc*. V opačném případě hodnota FALSE. Operátor, který se používá k provádění porovnání výchozí národní prostředí uživatele.

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

Nastaví základní typ VARIANT varianty, které jsou obsaženy v určený datový proud.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) rozhraní v datovém proudu, který obsahuje data.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`ReadToStream` vyžaduje, aby předchozí volání [WriteToStream](#writetostream).

##  <a name="setbyref"></a>  CComVariant::SetByRef

Inicializuje `CComVariant` objekt a nastaví `vt` člen VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ VARIANT, například BSTR **int**, nebo **char**.

*pT*<br/>
Použitý k inicializaci ukazatele `CComVariant` objektu.

### <a name="remarks"></a>Poznámky

`SetByRef` je šablona funkce, která inicializuje `CComVariant` objekt ukazatele *pT* a nastaví `vt` člen VT_BYREF. Příklad:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant::WriteToStream

Základní typ VARIANT uloží do datového proudu.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) rozhraní na datovém proudu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
