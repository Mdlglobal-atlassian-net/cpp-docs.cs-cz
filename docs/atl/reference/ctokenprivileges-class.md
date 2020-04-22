---
title: Třída CTokenPrivileges
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
ms.openlocfilehash: 75c09f723860540aa54cf3744cde7e61d9202f79
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747358"
---
# <a name="ctokenprivileges-class"></a>Třída CTokenPrivileges

Tato třída je obálka `TOKEN_PRIVILEGES` pro strukturu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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
|[CTokenPrivileges::Přidat](#add)|Přidá k objektu `CTokenPrivileges` jedno nebo více oprávnění.|
|[CTokenPrivileges::Delete](#delete)|Odstraní oprávnění z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Odstraní všechna oprávnění z `CTokenPrivileges` objektu.|
|[CTokenPrivileges::GetCount](#getcount)|Vrátí počet položek oprávnění `CTokenPrivileges` v objektu.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Načte zobrazované názvy oprávnění obsažených v objektu. `CTokenPrivileges`|
|[CTokenPrivileges::GetLength](#getlength)|Vrátí velikost vyrovnávací paměti v bajtů potřebných k uložení `TOKEN_PRIVILEGES` struktury reprezentované objektem. `CTokenPrivileges`|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Načte místně jedinečné identifikátory (LUID) a atributpříznaky z objektu. `CTokenPrivileges`|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Načte názvy oprávnění a `CTokenPrivileges` příznaky atributů z objektu.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Vrátí ukazatel na `TOKEN_PRIVILEGES` strukturu.|
|[CTokenPrivileges::Oprávnění vyhledávání](#lookupprivilege)|Načte atribut přidružený k danému názvu oprávnění.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CTokenPrivileges::operátor const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Předává hodnotu ukazatel na `TOKEN_PRIVILEGES` strukturu.|
|[CTokenPrivileges::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/win32/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému k systému Windows.

Přístupový token se používá k popisu různých oprávnění zabezpečení udělených každému uživateli. Oprávnění se skládá z 64bitového čísla nazývaného místně jedinečný identifikátor ( [LUID](/windows/win32/api/winnt/ns-winnt-luid)) a řetězec popisovače.

Třída `CTokenPrivileges` je obálka pro [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) strukturu a obsahuje 0 nebo více oprávnění. Oprávnění lze přidat, odstranit nebo dotazovat pomocí zadaných metod třídy.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CTokenPrivileges::Přidat

Přidá jedno nebo více `CTokenPrivileges` oprávnění k objektu tokenu přístupu.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje název oprávnění, jak je definováno ve winnt. H hlavičkový soubor.

*bEnable*<br/>
Pokud true, oprávnění je povoleno. Pokud false, oprávnění je zakázáno.

*oprávnění*<br/>
Odkaz na [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) strukturu. Oprávnění a atributy jsou zkopírovány z `CTokenPrivileges` této struktury a přidány do objektu.

### <a name="return-value"></a>Návratová hodnota

První forma této metody vrátí true, pokud jsou úspěšně přidány oprávnění false jinak.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

Konstruktor

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Objekt, `CTokenPrivileges` který má být přiřazen novému objektu.

*oprávnění*<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) struktury přiřadit k `CTokenPrivileges` novému objektu.

### <a name="remarks"></a>Poznámky

Objekt `CTokenPrivileges` lze volitelně vytvořit `TOKEN_PRIVILEGES` pomocí struktury nebo `CTokenPrivileges` dříve definovaného objektu.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CTokenPrivileges::~CTokenPrivileges

Destruktor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CTokenPrivileges::Delete

Odstraní oprávnění z `CTokenPrivileges` objektu tokenu přístupu.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje název oprávnění, jak je definováno ve winnt. H hlavičkový soubor. Tento parametr může například určit konstantní SE_SECURITY_NAME nebo odpovídající řetězec SeSecurityPrivilege.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud bylo oprávnění úspěšně odstraněno, jinak false.

### <a name="remarks"></a>Poznámky

Tato metoda je užitečná jako nástroj pro vytváření tokenů s omezeným přístupem.

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CTokenPrivileges::DeleteAll

Odstraní všechna oprávnění z `CTokenPrivileges` objektu tokenu přístupu.

```cpp
void DeleteAll() throw();
```

### <a name="remarks"></a>Poznámky

Odstraní všechna oprávnění obsažená `CTokenPrivileges` v objektu tokenu přístupu.

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames

Načte zobrazované názvy oprávnění obsažených v objektu tokenu přístupu. `CTokenPrivileges`

```cpp
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDisplayNames*<br/>
Ukazatel na pole `CString` objektů. `CNames`je definovánjako typedef: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Poznámky

Parametr `pDisplayNames` je ukazatel na pole `CString` objektů, které obdrží zobrazované názvy odpovídající `CTokenPrivileges` oprávnění obsaženým v objektu. Tato metoda načte zobrazované názvy pouze pro oprávnění zadaná v části Definovaná oprávnění ve winnt. H.

Tato metoda načte zobrazitelný název: například pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, zobrazitelný název je "Vynutit vypnutí ze vzdáleného systému." Chcete-li získat název systému, použijte [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CTokenPrivileges::GetCount

Vrátí počet položek oprávnění `CTokenPrivileges` v objektu.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet oprávnění obsažených v `CTokenPrivileges` objektu.

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CTokenPrivileges::GetLength

Vrátí délku `CTokenPrivileges` objektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů potřebných `TOKEN_PRIVILEGES` k uložení `CTokenPrivileges` struktury reprezentované objektem, včetně všech položek oprávnění, které obsahuje.

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

Načte místně jedinečné identifikátory (LUID) a atributpříznaky z objektu. `CTokenPrivileges`

```cpp
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Ukazatel na pole [luid](/windows/win32/api/winnt/ns-winnt-luid) objektů. `CLUIDArray`je typedef definované `CAtlArray<LUID> CLUIDArray`jako .

*atributy p*<br/>
Ukazatel na pole objektů DWORD. Pokud je tento parametr vynechán nebo null, atributy nejsou načteny. `CAttributes`je typedef definované `CAtlArray <DWORD> CAttributes`jako .

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří výčet všech oprávnění obsažených `CTokenPrivileges` v objektu tokenu přístupu a umístí jednotlivé identifikátory LUID a (volitelně) atribut ové příznaky do objektů pole.

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

Načte příznaky názvu a `CTokenPrivileges` atributu z objektu.

```cpp
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pNázvy*<br/>
Ukazatel na pole `CString` objektů. `CNames`je typedef definované `CAtlArray <CString> CNames`jako .

*atributy p*<br/>
Ukazatel na pole objektů DWORD. Pokud je tento parametr vynechán nebo null, atributy nejsou načteny. `CAttributes`je typedef definované `CAtlArray <DWORD> CAttributes`jako .

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří výčet všech oprávnění obsažených `CTokenPrivileges` v objektu, umístění názvu a (volitelně) atribut příznaky do pole objektů.

Tato metoda načte název atributu, nikoli zobrazitelný název: například pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, je název systému "SeRemoteShutdownPrivilege." Chcete-li získat zobrazitelný název, použijte metodu [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

Vrátí ukazatel na `TOKEN_PRIVILEGES` strukturu.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) strukturu.

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CTokenPrivileges::Oprávnění vyhledávání

Načte atribut přidružený k danému názvu oprávnění.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje název oprávnění, jak je definováno ve winnt. H hlavičkový soubor. Tento parametr může například určit konstantní SE_SECURITY_NAME nebo odpovídající řetězec SeSecurityPrivilege.

*pdwAttributes*<br/>
Ukazatel na proměnnou, která přijímá atributy.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je atribut úspěšně načten, false otherwise.

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CTokenPrivileges::operátor =

Operátor přiřazení.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*oprávnění*<br/>
[Struktura TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) přiřadit k `CTokenPrivileges` objektu.

*rhs*<br/>
Objekt, `CTokenPrivileges` který má být přiřazen k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CTokenPrivileges` objekt.

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operátor const TOKEN_PRIVILEGES\*

Předává hodnotu ukazatel na `TOKEN_PRIVILEGES` strukturu.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Předává hodnotu ukazatel na [strukturu TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges)

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[Luid](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
