---
title: CTokenGroups – třída
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 4e5d06ca01201bf415afedbe6f6e5bca096f68fa
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915582"
---
# <a name="ctokengroups-class"></a>CTokenGroups – třída

Tato třída je obálkou pro `TOKEN_GROUPS` strukturu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenGroups
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor|
|[CTokenGroups:: ~ CTokenGroups](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CTokenGroups:: Add](#add)|Přidá do `CTokenGroups` objektu `TOKEN_GROUPS` neboexistujícístrukturu.`CSid`|
|[CTokenGroups::D dstranit](#delete)|Odstraní a jeho přidružené atributy `CTokenGroups` z objektu. `CSid`|
|[CTokenGroups::D eleteAll](#deleteall)|Odstraní všechny `CSid` objekty a jejich přidružené atributy `CTokenGroups` z objektu.|
|[CTokenGroups:: GetCount](#getcount)|Vrátí počet `CSid` objektů a přidružených atributů obsažených `CTokenGroups` v objektu.|
|[CTokenGroups:: GetLength](#getlength)|Vrátí velikost `CTokenGroups` objektu.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Načte ukazatel na `TOKEN_GROUPS` strukturu.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Načte objekty a atributy patřící `CTokenGroups` k objektu. `CSid`|
|[CTokenGroups::LookupSid](#lookupsid)|Načte atributy přidružené `CSid` k objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CTokenGroups:: operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Přetypování `TOKEN_GROUPS` objektu na ukazatel na strukturu. `CTokenGroups`|
|[CTokenGroups:: operator =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému do systému Windows.

Třída je obálkou pro strukturu TOKEN_GROUPS, která obsahuje informace o identifikátorech zabezpečení skupiny (SID) v přístupovém tokenu. [](/windows/desktop/api/winnt/ns-winnt-token_groups) `CTokenGroups`

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/desktop/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="add"></a>CTokenGroups:: Add

Přidá do `CTokenGroups` objektu `TOKEN_GROUPS` neboexistujícístrukturu.`CSid`

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Objekt [CSID](../../atl/reference/csid-class.md) .

*dwAttributes*<br/>
Atributy, které mají být spojeny s `CSid` objektem.

*rTokenGroups*<br/>
Struktura [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)

### <a name="remarks"></a>Poznámky

Tyto metody přidávají `CTokenGroups` k objektu `CSid` jeden nebo více objektů a jejich přidružené atributy.

##  <a name="ctokengroups"></a>CTokenGroups::CTokenGroups

Konstruktor

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Objekt nebo struktura [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) , pomocí `CTokenGroups` které se vytvoří objekt. `CTokenGroups`

### <a name="remarks"></a>Poznámky

Objekt lze volitelně vytvořit `TOKEN_GROUPS` pomocí struktury nebo dříve definovaného `CTokenGroups` objektu. `CTokenGroups`

##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups

Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

##  <a name="delete"></a>CTokenGroups::D dstranit

Odstraní a jeho přidružené atributy `CTokenGroups` z objektu. `CSid`

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Objekt [CSID](../../atl/reference/csid-class.md) , pro který by měl být odebrán identifikátor zabezpečení (SID) a atributy.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, `CSid` Pokud je odstraněno, jinak false.

##  <a name="deleteall"></a>CTokenGroups::D eleteAll

Odstraní všechny `CSid` objekty a jejich přidružené atributy `CTokenGroups` z objektu.

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>CTokenGroups:: GetCount

Vrátí počet `CSid` objektů obsažených v `CTokenGroups`.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet objektů [CSID](../../atl/reference/csid-class.md) a jejich přidružených atributů obsažených v `CTokenGroups` objektu.

##  <a name="getlength"></a>CTokenGroups:: GetLength

Vrátí velikost `CTokenGroup` objektu.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí celkovou velikost `CTokenGroup` objektu v bajtech.

##  <a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Načte ukazatel na `TOKEN_GROUPS` strukturu.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel na strukturu [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) patřící `CTokenGroups` objektu přístupového tokenu.

##  <a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Načte objekty a (volitelně) atributy patřící `CTokenGroups` objektu. `CSid`

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Ukazatel na pole objektů [CSID](../../atl/reference/csid-class.md) .

*pAttributes*<br/>
Ukazatel na pole hodnot typu DWORD. Pokud tento parametr vynecháte nebo je NULL, atributy se nenačte.

### <a name="remarks"></a>Poznámky

Tato metoda provede výčet všech `CSid` objektů obsažených `CTokenGroups` v objektu a jejich umístění a (volitelně) příznaky atributu do objektů Array.

##  <a name="lookupsid"></a>CTokenGroups::LookupSid

Načte atributy přidružené `CSid` k objektu.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Objekt [CSID](../../atl/reference/csid-class.md)

*pdwAttributes*<br/>
Ukazatel na DWORD, který bude souhlasit s `CSid` atributem objektu. Pokud tento parametr vynecháte nebo je NULL, atribut se nenačte.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, `CSid` Pokud je nalezen, jinak false.

### <a name="remarks"></a>Poznámky

Nastavení *pdwAttributes* na hodnotu null poskytuje způsob, jak potvrdit existenci existence `CSid` bez přístupu k atributu. Všimněte si, že tato metoda by se neměla používat ke kontrole přístupových práv. Aplikace by místo toho měly používat metodu [CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) .

##  <a name="operator_eq"></a>CTokenGroups:: operator =

Operátor přiřazení

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Objekt nebo struktura [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) `CTokenGroups` , která se má přiřadit k objektu. `CTokenGroups`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CTokenGroups` objekt.

##  <a name="operator_const_token_groups__star"></a>CTokenGroups:: operator const TOKEN_GROUPS *

Přetypování hodnoty na ukazatel na `TOKEN_GROUPS` strukturu.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Přetypování hodnoty na ukazatel na strukturu [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) .

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[CSid – třída](../../atl/reference/csid-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
