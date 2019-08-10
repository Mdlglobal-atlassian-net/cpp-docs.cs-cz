---
title: CTokenPrivileges – třída
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: 5f8379d20d8c8d525cd645e1d4aa0c751e16f531
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915537"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges – třída

Tato třída je obálkou pro `TOKEN_PRIVILEGES` strukturu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenPrivileges
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Konstruktor|
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CTokenPrivileges:: Add](#add)|Přidá k `CTokenPrivileges` objektu jedno nebo více oprávnění.|
|[CTokenPrivileges::D dstranit](#delete)|Odstraní oprávnění z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::D eleteAll](#deleteall)|Odstraní všechna oprávnění z `CTokenPrivileges` objektu.|
|[CTokenPrivileges:: GetCount](#getcount)|Vrátí počet položek oprávnění v `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Načte zobrazované názvy pro oprávnění obsažená v `CTokenPrivileges` objektu.|
|[CTokenPrivileges:: GetLength](#getlength)|Vrátí velikost vyrovnávací paměti v bajtech potřebných k uložení `TOKEN_PRIVILEGES` struktury reprezentované `CTokenPrivileges` objektem.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Načte místně jedinečné identifikátory (LUID) a příznaky atributů z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Načte názvy oprávnění a příznaky atributů z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Vrátí ukazatel na `TOKEN_PRIVILEGES` strukturu.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Načte atribut přidružený k danému názvu oprávnění.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CTokenPrivileges:: operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Přetypování hodnoty na ukazatel na `TOKEN_PRIVILEGES` strukturu.|
|[CTokenPrivileges:: operator =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému do systému Windows.

Přístupový token se používá k popisu různých oprávnění zabezpečení udělených každému uživateli. Oprávnění se skládá z 64 čísla s názvem místně jedinečného identifikátoru ( [LUID](/windows/desktop/api/winnt/ns-winnt-luid)) a řetězce popisovače.

Třída je obálkou pro strukturu TOKEN_PRIVILEGES a obsahuje 0 nebo více oprávnění. [](/windows/desktop/api/winnt/ns-winnt-token_privileges) `CTokenPrivileges` Oprávnění lze přidat, odstranit nebo dotazovat pomocí zadaných metod třídy.

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/desktop/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="add"></a>CTokenPrivileges:: Add

Přidá jedno nebo více oprávnění k `CTokenPrivileges` objektu přístupového tokenu.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název oprávnění, jak je definováno v souboru WINNT. Soubor hlaviček H

*bEnable*<br/>
Pokud je nastaveno na true, oprávnění je povolené. V případě hodnoty false je oprávnění zakázáno.

*rPrivileges*<br/>
Odkaz na strukturu [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) . Oprávnění a atributy se zkopírují z této struktury a přidají se `CTokenPrivileges` do objektu.

### <a name="return-value"></a>Návratová hodnota

První forma této metody vrátí hodnotu true, pokud jsou oprávnění úspěšně přidána, jinak false.

##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

Konstruktor

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
`CTokenPrivileges` Objekt, který se má přiřadit k novému objektu.

*rPrivileges*<br/>
Struktura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) , která se má přiřadit k `CTokenPrivileges` novému objektu.

### <a name="remarks"></a>Poznámky

Objekt lze volitelně vytvořit `TOKEN_PRIVILEGES` pomocí struktury nebo dříve definovaného `CTokenPrivileges` objektu. `CTokenPrivileges`

##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges

Destruktor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

##  <a name="delete"></a>CTokenPrivileges::D dstranit

Odstraní oprávnění z `CTokenPrivileges` objektu přístupového tokenu.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název oprávnění, jak je definováno v souboru WINNT. Soubor hlaviček H Tento parametr například může určovat konstantu SE_SECURITY_NAME nebo odpovídající řetězec "SeSecurityPrivilege".

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud bylo oprávnění úspěšně odstraněno, jinak false.

### <a name="remarks"></a>Poznámky

Tato metoda je užitečná jako nástroj pro vytváření omezených tokenů.

##  <a name="deleteall"></a>CTokenPrivileges::D eleteAll

Odstraní všechna oprávnění z `CTokenPrivileges` objektu přístupového tokenu.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Poznámky

Odstraní všechna oprávnění obsažená v `CTokenPrivileges` objektu přístupového tokenu.

##  <a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames

Načte zobrazované názvy pro oprávnění obsažená v `CTokenPrivileges` objektu přístupového tokenu.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDisplayNames*<br/>
Ukazatel na pole `CString` objektů. `CNames`je definován jako typedef: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Poznámky

Parametr `pDisplayNames` je ukazatel na `CString` pole objektů, které budou přijímat zobrazované názvy odpovídající oprávněním obsaženým v `CTokenPrivileges` objektu. Tato metoda načte zobrazované názvy pouze pro oprávnění uvedená v části definovaná oprávnění v souboru WINNT. Y.

Tato metoda načte zobrazitelný název, například pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, zobrazovaný název je "vynucené vypnutí ze vzdáleného systému". Chcete-li získat název systému, použijte [CTokenPrivileges:: GetNamesAndAttributes](#getnamesandattributes).

##  <a name="getcount"></a>CTokenPrivileges:: GetCount

Vrátí počet položek oprávnění v `CTokenPrivileges` objektu.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet oprávnění obsažených v `CTokenPrivileges` objektu.

##  <a name="getlength"></a>CTokenPrivileges:: GetLength

Vrátí délku `CTokenPrivileges` objektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů vyžadovaných k uložení `TOKEN_PRIVILEGES` struktury reprezentované `CTokenPrivileges` objektem, včetně všech položek oprávnění, které obsahuje.

##  <a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

Načte místně jedinečné identifikátory (LUID) a příznaky atributů z `CTokenPrivileges` objektu.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Ukazatel na pole objektů [LUID](/windows/desktop/api/winnt/ns-winnt-luid) . `CLUIDArray`je definice typu definovaná jako `CAtlArray<LUID> CLUIDArray`.

*pAttributes*<br/>
Ukazatel na pole objektů typu DWORD. Pokud tento parametr vynecháte nebo je NULL, atributy se nenačte. `CAttributes`je definice typu definovaná jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří výčet všech oprávnění obsažených v `CTokenPrivileges` objektu přístupového tokenu a umístí jednotlivé identifikátory LUID a (volitelně) příznaky atributu do objektů Array.

##  <a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

Načte názvy a příznaky atributů z `CTokenPrivileges` objektu.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pNames*<br/>
Ukazatel na pole `CString` objektů. `CNames`je definice typu definovaná jako `CAtlArray <CString> CNames`.

*pAttributes*<br/>
Ukazatel na pole objektů typu DWORD. Pokud tento parametr vynecháte nebo je NULL, atributy se nenačte. `CAttributes`je definice typu definovaná jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Poznámky

Tato metoda provede výčet všech oprávnění obsažených v `CTokenPrivileges` objektu a umístění názvu a (volitelně) příznaků atributů do objektů Array.

Tato metoda načte název atributu místo nezobrazitelného názvu: například, pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, název systému je "SeRemoteShutdownPrivilege". Chcete-li získat zobrazitelný název, použijte metodu [CTokenPrivileges:: GetDisplayNames](#getdisplaynames).

##  <a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

Vrátí ukazatel na `TOKEN_PRIVILEGES` strukturu.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na strukturu [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) .

##  <a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege

Načte atribut přidružený k danému názvu oprávnění.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název oprávnění, jak je definováno v souboru WINNT. Soubor hlaviček H Tento parametr například může určovat konstantu SE_SECURITY_NAME nebo odpovídající řetězec "SeSecurityPrivilege".

*pdwAttributes*<br/>
Ukazatel na proměnnou, která přijímá atributy.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je atribut úspěšně načten, jinak false.

##  <a name="operator_eq"></a>CTokenPrivileges:: operator =

Operátor přiřazení

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Struktura [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) , která se má přiřadit `CTokenPrivileges` k objektu.

*zarovnání indirekce RHS*<br/>
`CTokenPrivileges` Objekt, který má být přiřazen objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CTokenPrivileges` objekt.

##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges:: operator const TOKEN_PRIVILEGES\*

Přetypování hodnoty na ukazatel na `TOKEN_PRIVILEGES` strukturu.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Přetypování hodnoty na ukazatel na strukturu [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) .

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
