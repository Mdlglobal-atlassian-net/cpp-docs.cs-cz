---
title: Ctokenprivileges – třída
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
ms.openlocfilehash: 80302d59d081b7cdf6f29960c3d8f4859b4ecbf4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280443"
---
# <a name="ctokenprivileges-class"></a>Ctokenprivileges – třída

Tato třída představuje obálku pro `TOKEN_PRIVILEGES` struktury.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenPrivileges
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Konstruktor|
|[CTokenPrivileges::~CTokenPrivileges](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTokenPrivileges::Add](#add)|Přidá jednu nebo více oprávnění `CTokenPrivileges` objektu.|
|[CTokenPrivileges::Delete](#delete)|Odstraní oprávnění z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Odstraní všechna oprávnění z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetCount](#getcount)|Vrátí počet položek oprávnění v `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Načte zobrazované názvy pro oprávnění součástí `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetLength](#getlength)|Vrátí velikost vyrovnávací paměti v bajtech potřebných k uložení `TOKEN_PRIVILEGES` konstrukce reprezentované `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Načte místně jedinečné identifikátory (LUID) a atribut příznaků z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Načte názvy oprávnění a příznaky atribut z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Vrací ukazatel `TOKEN_PRIVILEGES` struktury.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Načte atribut přidružený název dané oprávnění.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Přetypování na ukazatel na hodnotu `TOKEN_PRIVILEGES` struktury.|
|[CTokenPrivileges::operator =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje proces nebo vlákno kontextu zabezpečení a přidělené každému uživateli přihlášení systému Windows.

Přístupový token se používá k popisu různých zabezpečení oprávněních udělených jednotlivým uživatelům. Oprávnění se skládá z 64bitové číslo volá místně jedinečný identifikátor ( [LUID](/windows/desktop/api/winnt/ns-winnt-_luid)) a řetězce popisovače.

`CTokenPrivileges` Třídy tvoří obálku pro [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury a obsahuje 0 nebo více oprávnění. Oprávnění se dají přidat, odstraněné nebo dotaz pomocí metody zadané třídy.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="add"></a>  CTokenPrivileges::Add

Přidá jednu nebo více oprávnění `CTokenPrivileges` objekt tokenu přístupu.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název oprávnění, jak jsou definovány v WINNT. Soubor hlaviček H.

*bEnable*<br/>
Při hodnotě true je oprávnění povoleno. Pokud má hodnotu false, oprávnění je zakázaná.

*rPrivileges*<br/>
Odkaz [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury. Oprávnění a atributy jsou zkopírovány z této struktury a přidán do `CTokenPrivileges` objektu.

### <a name="return-value"></a>Návratová hodnota

První formulář této metody vrátí hodnotu true, pokud oprávnění se úspěšně přidají, false v opačném případě.

##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges

Konstruktor

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`CTokenPrivileges` Objektu, který chcete přiřadit nový objekt.

*rPrivileges*<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktura přiřazena novému `CTokenPrivileges` objektu.

### <a name="remarks"></a>Poznámky

`CTokenPrivileges` Objektu je volitelně možné vytvořit `TOKEN_PRIVILEGES` struktury nebo dříve definované `CTokenPrivileges` objektu.

##  <a name="dtor"></a>  Ctokenprivileges –:: ~ ctokenprivileges –

Destruktor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

##  <a name="delete"></a>  CTokenPrivileges::Delete

Odstraní oprávnění z `CTokenPrivileges` objekt tokenu přístupu.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název oprávnění, jak jsou definovány v WINNT. Soubor hlaviček H. Například může tento parametr zadejte konstanta SE_SECURITY_NAME nebo její odpovídající řetězec "SeSecurityPrivilege."

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud oprávnění se úspěšně odstranila, false, jinak.

### <a name="remarks"></a>Poznámky

Tato metoda je užitečná jako nástroj pro vytváření tokenů s omezeným přístupem.

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

Odstraní všechna oprávnění z `CTokenPrivileges` objekt tokenu přístupu.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Poznámky

Odstraní všechna oprávnění, které jsou součástí `CTokenPrivileges` objekt tokenu přístupu.

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

Načte zobrazované názvy pro oprávnění součástí `CTokenPrivileges` objekt tokenu přístupu.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDisplayNames*<br/>
Ukazatel na pole `CString` objekty. `CNames` je definován jako definice typu: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Poznámky

Parametr `pDisplayNames` je ukazatel na pole `CString` objekty, které obdrží zobrazované názvy odpovídající oprávnění součástí `CTokenPrivileges` objektu. Tato metoda načte zobrazované názvy pouze pro oprávnění definováno v sekci definované oprávnění WINNT. H.

Tato metoda načte zobrazitelný název: například, pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, zobrazitelný název je "Vynutit vypnutí ze vzdáleného systému." Chcete-li získat název systému, použijte [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

Vrátí počet položek oprávnění v `CTokenPrivileges` objektu.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet součástí oprávnění `CTokenPrivileges` objektu.

##  <a name="getlength"></a>  CTokenPrivileges::GetLength

Vrátí délku objektu `CTokenPrivileges` objektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů vyžadovaných k uložení `TOKEN_PRIVILEGES` konstrukce reprezentované `CTokenPrivileges` objektu, včetně všech položek oprávnění ho obsahuje.

##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes

Načte místně jedinečné identifikátory (LUID) a atribut příznaků z `CTokenPrivileges` objektu.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Ukazatel na pole [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) objekty. `CLUIDArray` definice typu je definován jako `CAtlArray<LUID> CLUIDArray`.

*pAttributes*<br/>
Ukazatel na pole objektů typu DWORD. Pokud je tento parametr vynechán nebo mít hodnotu NULL, nejsou načíst atributy. `CAttributes` definice typu je definován jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Poznámky

Tato metoda projde veškerá oprávnění součástí `CTokenPrivileges` přístup k objektu tokenu a umístění jednotlivých LUID a (volitelně) příznaků atributu do pole objektů.

##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes

Načte název a atribut příznaků z `CTokenPrivileges` objektu.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pNames*<br/>
Ukazatel na pole `CString` objekty. `CNames` definice typu je definován jako `CAtlArray <CString> CNames`.

*pAttributes*<br/>
Ukazatel na pole objektů typu DWORD. Pokud je tento parametr vynechán nebo mít hodnotu NULL, nejsou načíst atributy. `CAttributes` definice typu je definován jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Poznámky

Tato metoda projde veškerá oprávnění součástí `CTokenPrivileges` objekt umístění název a (volitelně) příznaků atributu na pole objektů.

Tato metoda načte název atributu, nikoli název zobrazitelný: Pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, název systému je například "Oprávnění SeRemoteShutdownPrivilege." K získání názvu zobrazitelný, použijte metodu [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES

Vrací ukazatel `TOKEN_PRIVILEGES` struktury.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury.

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

Načte atribut přidružený název dané oprávnění.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název oprávnění, jak jsou definovány v WINNT. Soubor hlaviček H. Například může tento parametr zadejte konstanta SE_SECURITY_NAME nebo její odpovídající řetězec "SeSecurityPrivilege."

*pdwAttributes*<br/>
Ukazovat na proměnnou, která přijímá atributy.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je atribut úspěšně načteny, false v opačném případě.

##  <a name="operator_eq"></a>  CTokenPrivileges::operator =

Operátor přiřazení.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktura přiřadit `CTokenPrivileges` objektu.

*Zarovnání indirekce RHS*<br/>
`CTokenPrivileges` Objektu, který chcete přiřadit k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CTokenPrivileges` objektu.

##  <a name="operator_const_token_privileges__star"></a>  CTokenPrivileges::operator const TOKEN_PRIVILEGES \*

Přetypování na ukazatel na hodnotu `TOKEN_PRIVILEGES` struktury.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Přetypování na ukazatel na hodnotu [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges)<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
