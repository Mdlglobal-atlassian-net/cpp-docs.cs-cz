---
title: Třída CComVariant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2ebef74f6da48d2124d69f002a85c467db73406
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ccomvariant-class"></a>CComVariant – třída
Tato třída zabalí `VARIANT` typu, poskytuje členem označující typ data uložená.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cpp
class CComVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComVariant::CComVariant](#ccomvariant)|Konstruktor|  
|[CComVariant:: ~ CComVariant](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComVariant::Attach](#attach)|Připojí **VARIANT** k `CComVariant` objektu.|  
|[CComVariant::ChangeType](#changetype)|Převede `CComVariant` na nový typ objektu.|  
|[CComVariant::Clear](#clear)|Vymaže `CComVariant` objektu.|  
|[CComVariant::Copy](#copy)|Kopie **VARIANT** k `CComVariant` objektu.|  
|[CComVariant::CopyTo](#copyto)|Zkopíruje obsah `CComVariant` objektu.|  
|[CComVariant::Detach](#detach)|Umožňuje odpojit základní **VARIANT** z `CComVariant` objektu.|  
|[CComVariant::GetSize](#getsize)|Vrátí velikost v bajtech obsahu `CComVariant` objektu.|  
|[CComVariant::ReadFromStream](#readfromstream)|Načítání **VARIANT** z datového proudu.|  
|[CComVariant::SetByRef](#setbyref)|Inicializuje `CComVariant` objekt a nastaví **vt** člena **VT_BYREF**.|  
|[CComVariant::WriteToStream](#writetostream)|Uloží základní **VARIANT** do datového proudu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|||  
|-|-|  
|[CComVariant::operator <](#operator_lt)|Určuje, zda `CComVariant` objektu je menší než zadaný **VARIANT**.|  
|[CComVariant::operator >](#operator_gt)|Určuje, zda `CComVariant` objektu je větší než zadaná **VARIANT**.|  
|[Operator! =](#operator_neq)|Určuje, zda `CComVariant` objekt se nerovná zadané **VARIANT**.|  
|[operátor =](#operator_eq)|Přiřadí hodnota `CComVariant` objektu.|  
|[Operator ==](#operator_eq_eq)|Určuje, zda `CComVariant` objekt rovná zadané **VARIANT**.|  
  
## <a name="remarks"></a>Poznámky  
 `CComVariant` zabalí `VARIANT and VARIANTARG` typu, který se skládá ze sjednocení a členem označující typ dat uložených v sjednocení. **VARIANT**s jsou obvykle používány v automatizaci.  
  
 `CComVariant` odvozená z **VARIANT** typu, aby ho bylo možné použít kdekoli **VARIANT** lze použít. Můžete například použít **V_VT** makro k extrakci typ `CComVariant` lze získat přístup **vt** člen přímo stejně, jako je možné s **VARIANT**.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcomcli.h  
  
##  <a name="attach"></a>  CComVariant::Attach  
 Bezpečně vymaže aktuální obsah `CComVariant` objektu, zkopíruje obsah `pSrc` do tento objekt pak nastaví typ variant `pSrc` k `VT_EMPTY`.  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pSrc`  
 [v] Odkazuje na [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) být připojen k objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Vlastnictví data ukládaná společností `pSrc` se přenese do `CComVariant` objektu.  
  
##  <a name="ccomvariant"></a>  CComVariant::CComVariant  
 Každý konstruktor zpracovává bezpečné inicializace `CComVariant` objekt voláním `VariantInit` funkce Win32 nebo nastavením hodnoty a typ podle parametrů předaných objektu.  
  
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
 *varSrc*  
 [v] `CComVariant` Nebo `VARIANT` použitý k inicializaci `CComVariant` objektu. Obsah zdroje variant se zkopíruje na cílový bez převodu.  
  
 `lpszSrc`  
 [v] Řetězec znaků použitý k inicializaci `CComVariant` objektu. Můžete předat ukončena nula široké (Unicode) znak řetězec tak, aby **LPCOLESTR** verzi v konstruktoru nebo řetězec ANSI do `LPCSTR` verze. V obou případech je daný řetězec převést na typu Unicode `BSTR` přidělen s použitím **SysAllocString**. Typ `CComVariant` objekt se bude `VT_BSTR`.  
  
 `bSrc`  
 [v] `bool` Použitý k inicializaci `CComVariant` objektu. `bool` Argument je převést na **VARIANT_BOOL** před uložené. Typ `CComVariant` objekt se bude `VT_BOOL`.  
  
 `nSrc`  
 [v] `int`, **BAJTŮ**, **krátké**, **dlouho**, **LONGLONG**, **ULONGLONG**, **nepodepsané prostě**, `unsigned long`, nebo `unsigned int` použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, nebo **VT_UI4**, v uvedeném pořadí.  
  
 `vtSrc`  
 [v] Typ varianty. Pokud je první parametr `int`, platné typy jsou `VT_I4` a **VT_INT**. Pokud je první parametr **dlouho**, platné typy jsou `VT_I4` a `VT_ERROR`. Pokud je první parametr **dvojité**, platné typy jsou `VT_R8` a `VT_DATE`. Pokud je první parametr `unsigned int`, platné typy jsou **VT_UI4** a **VT_UINT**.  
  
 `fltSrc`  
 [v] **Float** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_R4`.  
  
 `dblSrc`  
 [v] **Dvojité** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_R8`.  
  
 `cySrc`  
 [v] **CY** použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_CY`.  
  
 `pSrc`  
 [v] `IDispatch` Nebo **IUnknown** ukazatel použitý k inicializaci `CComVariant` objektu. `AddRef` bude mít název na ukazatel rozhraní. Typ `CComVariant` objekt se bude **VT_DISPATCH** nebo **VT_UNKNOWN**, v uvedeném pořadí.  
  
 Nebo **SAFERRAY** ukazatel použitý k inicializaci `CComVariant` objektu. Kopii **SAFEARRAY** je uložen v `CComVariant` objektu. Typ `CComVariant` objekt se bude kombinací původní typ **SAFEARRAY** a **VT_ARRAY**.  
  
 `cSrc`  
 [v] `char` Použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude **VT_I1**.  
  
 `bstrSrc`  
 [v] BSTR použitý k inicializaci `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_BSTR`.  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru spravuje čištění voláním [CComVariant::Clear](#clear).  
  
##  <a name="dtor"></a>  CComVariant:: ~ CComVariant  
 Destruktor.  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda spravuje čištění voláním [CComVariant::Clear](#clear).  
  
##  <a name="changetype"></a>  CComVariant::ChangeType  
 Převede `CComVariant` na nový typ objektu.  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `vtNew`  
 [v] Nový typ pro `CComVariant` objektu.  
  
 `pSrc`  
 [v] Ukazatel `VARIANT` jehož hodnota bude převedena na nový typ. Výchozí hodnota je **NULL**znamená `CComVariant` objektu bude převeden na místě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte hodnotu `pSrc`, `ChangeType` bude používat toto **VARIANT** jako zdroj pro převod. Jinak `CComVariant` objekt se bude zdroj.  
  
##  <a name="clear"></a>  CComVariant::Clear  
 Vymaže `CComVariant` objekt voláním `VariantClear` Win32 funkce.  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Automaticky volání destruktoru **zrušte**.  
  
##  <a name="copy"></a>  CComVariant::Copy  
 Uvolní `CComVariant` objektu a přiřadí ji kopii zadaný **VARIANT**.  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pSrc`  
 [v] Ukazatel [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) ke kopírování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="copyto"></a>  CComVariant::CopyTo  
 Zkopíruje obsah `CComVariant` objektu.  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrDest*  
 Odkazuje na `BSTR` , obdrží kopii obsah `CComVariant` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 **CComVariant** objekt musí být typu `VT_BSTR`.  
  
##  <a name="detach"></a>  CComVariant::Detach  
 Umožňuje odpojit základní **VARIANT** z `CComVariant` objektu a nastaví typ objektu `VT_EMPTY`.  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>Parametry  
 `pDest`  
 [out] Vrátí základní `VARIANT` hodnota objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že obsah `VARIANT` odkazuje `pDest` bude automaticky vymazán před přiřazením hodnoty a typ volání **CComVariant** objektu.  
  
##  <a name="getsize"></a>  CComVariant::GetSize  
 Pro jednoduché pevnou velikost `VARIANT`s, vrátí tato metoda `sizeof` plus základní datový typ `sizeof(VARTYPE)`.  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost v bajtech aktuální obsahu `CComVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `VARIANT` obsahuje ukazatele rozhraní, `GetSize` dotazuje na `IPersistStream` nebo `IPersistStreamInit`. Pokud úspěšné, vrácená hodnota je 32 bity nejnižší hodnoty vrácené `GetSizeMax` a `sizeof` `CLSID` a `sizeof(VARTYPE)`. Pokud je ukazatel rozhraní `NULL`, `GetSize` vrátí `sizeof` `CLSID` plus `sizeof(VARTYPE)`. Pokud celková velikost je větší než `ULONG_MAX`, `GetSize` vrátí `sizeof(VARTYPE)` což označuje chybu.  
  
 Ve všech ostatních případech, dočasného `VARIANT` typu `VT_BSTR` sloučen z aktuální `VARIANT`. Délka této `BSTR` počítá se jako velikost délky řetězce plus délky řetězce samotné plus velikost null znak plus `sizeof(VARTYPE)`. Pokud `VARIANT` nelze přiřadit k `VARIANT` typu `VT_BSTR`, `GetSize` vrátí `sizeof(VARTYPE)`.  
  
 Tato metoda vrátí velikost odpovídá počet bajtů používaných [CComVariant::WriteToStream](#writetostream) za úspěšné podmínek.  
  
##  <a name="operator_eq"></a>  CComVariant::operator =  
 Přiřadí odpovídající typ a hodnotu `CComVariant` objektu.  
  
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
 *varSrc*  
 [v] `CComVariant` Nebo [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) přiřazovaný `CComVariant` objektu. Obsah zdroje variant se zkopíruje na cílový bez převodu.  
  
 `bstrSrc`  
 [v] BSTR pro přiřazení `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_BSTR`.  
  
 `lpszSrc`  
 [v] Řetězec znaků pro přiřazení `CComVariant` objektu. Můžete předat ukončena nula široké (Unicode) znak řetězec tak, aby **LPCOLESTR** verzi operátor nebo řetězec ANSI do `LPCSTR` verze. V obou případech je daný řetězec převést na typu Unicode `BSTR` přidělen s použitím **SysAllocString**. Typ `CComVariant` objekt se bude `VT_BSTR`.  
  
 `bSrc`  
 [v] `bool` Přiřazovaný `CComVariant` objektu. `bool` Argument je převést na **VARIANT_BOOL** před uložené. Typ `CComVariant` objekt se bude `VT_BOOL`.  
  
 `nSrc`  
 [v] `int`, **BAJTŮ**, **krátké**, **dlouho**, **LONGLONG**, **ULONGLONG**, **nepodepsané prostě**, `unsigned long`, nebo `unsigned int` přiřazovaný `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, nebo **VT_UI4**, v uvedeném pořadí.  
  
 `fltSrc`  
 [v] **Float** přiřazovaný `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_R4`.  
  
 `dblSrc`  
 [v] **Dvojité** přiřazovaný `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_R8`.  
  
 `cySrc`  
 [v] **CY** přiřazovaný `CComVariant` objektu. Typ `CComVariant` objekt se bude `VT_CY`.  
  
 `pSrc`  
 [v] `IDispatch` Nebo **IUnknown** ukazatele pro přiřazení `CComVariant` objektu. `AddRef` bude mít název na ukazatel rozhraní. Typ `CComVariant` objekt se bude **VT_DISPATCH** nebo **VT_UNKNOWN**, v uvedeném pořadí.  
  
 Nebo, **SAFEARRAY** ukazatele pro přiřazení `CComVariant` objektu. Kopii **SAFEARRAY** je uložen v `CComVariant` objektu. Typ `CComVariant` objekt se bude kombinací původní typ **SAFEARRAY** a **VT_ARRAY**.  
  
 `cSrc`  
 [v] Char přiřazovaný `CComVariant` objektu. Typ `CComVariant` objekt se bude **VT_I1**.  
  
##  <a name="operator_eq_eq"></a>  CComVariant::operator ==  
 Určuje, zda `CComVariant` objekt rovná zadané **VARIANT**.  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí **true** Pokud hodnota a typ *varSrc* jsou stejné hodnoty a typ, v uvedeném pořadí, `CComVariant` objektu. V opačném **false**. Operátor používá výchozí národní prostředí uživatele k porovnání.  
  
 Operátor porovnává pouze hodnotu typu variant. Porovná řetězce, celá čísla a plovoucí body, ale není pole nebo záznamy.  
  
##  <a name="operator_neq"></a>  CComVariant::operator! =  
 Určuje, zda `CComVariant` objekt se nerovná zadané **VARIANT**.  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí **true** Pokud hodnotu nebo typ *varSrc* není roven hodnotu nebo typu, v uvedeném pořadí, `CComVariant` objektu. V opačném **false**. Operátor používá výchozí národní prostředí uživatele k porovnání.  
  
 Operátor porovnává pouze hodnotu typu variant. Porovná řetězce, celá čísla a plovoucí body, ale není pole nebo záznamy.  
  
##  <a name="operator_lt"></a>  CComVariant::operator &lt;  
 Určuje, zda `CComVariant` objektu je menší než zadaný **VARIANT**.  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí **true** Pokud hodnota `CComVariant` objektu je menší než hodnota *varSrc*. V opačném **false**. Operátor používá výchozí národní prostředí uživatele k porovnání.  
  
##  <a name="operator_gt"></a>  CComVariant::operator &gt;  
 Určuje, zda `CComVariant` objektu je větší než zadaná **VARIANT**.  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí **true** Pokud hodnota `CComVariant` objektu je větší než hodnota *varSrc*. V opačném **false**. Operátor používá výchozí národní prostředí uživatele k porovnání.  
  
##  <a name="readfromstream"></a>  CComVariant::ReadFromStream  
 Nastaví základní **VARIANT** k **VARIANT** obsažené v zadaného datového proudu.  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [v] Ukazatel [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) rozhraní na datový proud, který obsahuje data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 **ReadToStream** vyžaduje předchozí volání [WriteToStream](#writetostream).  
  
##  <a name="setbyref"></a>  CComVariant::SetByRef  
 Inicializuje `CComVariant` objekt a nastaví **vt** člena **VT_BYREF**.  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ **VARIANT**, například `BSTR`, `int`, nebo `char`.  
  
 *PT*  
 Ukazatel použitý k inicializaci `CComVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `SetByRef` je funkce šablonu, která inicializuje `CComVariant` objekt, který má ukazatel *pT* a nastaví **vt** člena **VT_BYREF**. Příklad:  
  
 [!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>  CComVariant::WriteToStream  
 Uloží základní **VARIANT** do datového proudu.  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [v] Ukazatel [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) rozhraní na datový proud.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)