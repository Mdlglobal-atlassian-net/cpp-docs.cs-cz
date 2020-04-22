---
title: Třída CTokenGroups
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
ms.openlocfilehash: ccfa628f4a099f7e13eb09d272c72c2bdd846f37
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746390"
---
# <a name="ctokengroups-class"></a>Třída CTokenGroups

Tato třída je obálka `TOKEN_GROUPS` pro strukturu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenGroups
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor|
|[CTokenGroups::~CTokenGroups](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTokenGroups::Přidat](#add)|Přidá `CSid` k `TOKEN_GROUPS` objektu `CTokenGroups` nebo existující strukturu.|
|[CTokenGroups::Delete](#delete)|Odstraní `CSid` a jeho přidružené atributy `CTokenGroups` z objektu.|
|[CTokenGroups::DeleteAll](#deleteall)|Odstraní z `CSid` objektu všechny objekty `CTokenGroups` a jejich přidružené atributy.|
|[CTokenGroups::GetCount](#getcount)|Vrátí počet `CSid` objektů a přidružených atributů `CTokenGroups` obsažených v objektu.|
|[CTokenGroups::GetLength](#getlength)|Vrátí velikost objektu. `CTokenGroups`|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Načte ukazatel na `TOKEN_GROUPS` strukturu.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Načte `CSid` objekty a atributy, které patří k objektu. `CTokenGroups`|
|[CTokenGroups::LookupSid](#lookupsid)|Načte atributy přidružené `CSid` k objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CTokenGroups::operátor const TOKEN_GROUPS *](#operator_const_token_groups__star)|Přetypovat `CTokenGroups` objekt na ukazatel `TOKEN_GROUPS` na strukturu.|
|[CTokenGroups::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/win32/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému k systému Windows.

Třída `CTokenGroups` je obálka pro [strukturu TOKEN_GROUPS,](/windows/win32/api/winnt/ns-winnt-token_groups) obsahující informace o identifikátorech zabezpečení skupiny (SID) v přístupovém tokenu.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CTokenGroups::Přidat

Přidá `CSid` k `TOKEN_GROUPS` objektu `CTokenGroups` nebo existující strukturu.

```cpp
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) objekt.

*dwAtributy*<br/>
Atributy přidružit `CSid` k objektu.

*rTokenGroups*<br/>
[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) struktura.

### <a name="remarks"></a>Poznámky

Tyto metody přidat `CSid` jeden nebo více objektů `CTokenGroups` a jejich přidružené atributy objektu.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CTokenGroups::CTokenGroups

Konstruktor

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Objekt `CTokenGroups` nebo [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) struktury, se `CTokenGroups` kterou chcete vytvořit objekt.

### <a name="remarks"></a>Poznámky

Objekt `CTokenGroups` lze volitelně vytvořit `TOKEN_GROUPS` pomocí struktury nebo `CTokenGroups` dříve definovaného objektu.

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CTokenGroups::~CTokenGroups

Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CTokenGroups::Delete

Odstraní `CSid` a jeho přidružené atributy `CTokenGroups` z objektu.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) objekt, pro který identifikátor zabezpečení (SID) a atributy by měly být odebrány.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CSid` true, pokud je odebrán, false jinak.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CTokenGroups::DeleteAll

Odstraní z `CSid` objektu všechny objekty `CTokenGroups` a jejich přidružené atributy.

```cpp
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CTokenGroups::GetCount

Vrátí počet `CSid` objektů obsažených `CTokenGroups`v .

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet objektů [CSid](../../atl/reference/csid-class.md) a jejich přidružené atributy obsažené v objektu. `CTokenGroups`

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CTokenGroups::GetLength

Vrátí velikost objektu. `CTokenGroup`

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí celkovou velikost `CTokenGroup` objektu v bajtech.

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Načte ukazatel na `TOKEN_GROUPS` strukturu.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel na [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) struktury `CTokenGroups` patřící k objektu tokenu přístupu.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Načte `CSid` objekty a (volitelně) atributy, které patří k objektu. `CTokenGroups`

```cpp
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Ukazatel na pole [csid](../../atl/reference/csid-class.md) objektů.

*atributy p*<br/>
Ukazatel na pole DWORDs. Pokud je tento parametr vynechán nebo null, atributy nejsou načteny.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří výčet všech `CSid` objektů obsažených `CTokenGroups` v objektu a umístí je a (volitelně) atribut příznaky do pole objektů.

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CTokenGroups::LookupSid

Načte atributy přidružené `CSid` k objektu.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) objekt.

*pdwAttributes*<br/>
Ukazatel na DWORD, který `CSid` bude akceptovat atribut objektu. Pokud je vynecháno nebo null, atribut nebude načten.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CSid` true, pokud je nalezen, false otherwise.

### <a name="remarks"></a>Poznámky

Nastavení *pdwAttributes* na HODNOTU NULL poskytuje způsob, jak potvrdit existenci `CSid` bez přístupu k atributu. Všimněte si, že tato metoda by neměla být použita ke kontrole přístupových práv. Aplikace by místo toho měly používat metodu [CAccessToken::CheckTokenMembership.](../../atl/reference/caccesstoken-class.md#checktokenmembership)

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CTokenGroups::operátor =

Operátor přiřazení.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Objekt `CTokenGroups` nebo [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) strukturu přiřadit `CTokenGroups` k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CTokenGroups` objekt.

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CTokenGroups::operátor const TOKEN_GROUPS *

Předává hodnotu ukazatel na `TOKEN_GROUPS` strukturu.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Předává hodnotu ukazatel na [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) struktury.

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[Třída CSid](../../atl/reference/csid-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
