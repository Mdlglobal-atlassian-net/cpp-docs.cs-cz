---
title: CTokenGroups Class
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
ms.openlocfilehash: 934d746dafafb39c2ffc3477c59c95914d270196
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772823"
---
# <a name="ctokengroups-class"></a>CTokenGroups Class

Tato třída představuje obálku pro `TOKEN_GROUPS` struktury.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenGroups
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor|
|[CTokenGroups::~CTokenGroups](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTokenGroups::Add](#add)|Přidá `CSid` nebo existující `TOKEN_GROUPS` struktury na `CTokenGroups` objektu.|
|[CTokenGroups::Delete](#delete)|Odstraní `CSid` a jeho přidružených atributů z `CTokenGroups` objektu.|
|[CTokenGroups::DeleteAll](#deleteall)|Odstraní všechny `CSid` objekty a jejich přidružených atributů z `CTokenGroups` objektu.|
|[CTokenGroups::GetCount](#getcount)|Vrátí počet `CSid` objekty a přidruženými atributy, které jsou součástí `CTokenGroups` objektu.|
|[CTokenGroups::GetLength](#getlength)|Vrátí velikost položky `CTokenGroups` objektu.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Načte ukazatel `TOKEN_GROUPS` struktury.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Načte `CSid` objektů a atributy, které patří k `CTokenGroups` objektu.|
|[CTokenGroups::LookupSid](#lookupsid)|Získá atributy přidružené k `CSid` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Přetypování `CTokenGroups` na ukazatel na objekt `TOKEN_GROUPS` struktury.|
|[CTokenGroups::operator =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje proces nebo vlákno kontextu zabezpečení a přidělené každému uživateli přihlášení systému Windows.

`CTokenGroups` Třídy tvoří obálku pro [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktura obsahující informace o identifikátory zabezpečení skupiny (SID) v tokenu přístupu.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="add"></a>  CTokenGroups::Add

Přidá `CSid` nebo existující `TOKEN_GROUPS` struktury na `CTokenGroups` objektu.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
A [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.

*dwAttributes*<br/>
Atributy pro přidružení k `CSid` objektu.

*rTokenGroups*<br/>
A [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury.

### <a name="remarks"></a>Poznámky

Tyto metody přidat jeden nebo více `CSid` objekty a jejich přidružených atributů, které mají `CTokenGroups` objektu.

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

Konstruktor

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`CTokenGroups` Objektu nebo [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) strukturu, pomocí kterého se má vytvořit `CTokenGroups` objektu.

### <a name="remarks"></a>Poznámky

`CTokenGroups` Objektu je volitelně možné vytvořit `TOKEN_GROUPS` struktury nebo dříve definované `CTokenGroups` objektu.

##  <a name="dtor"></a>  Ctokengroups –:: ~ ctokengroups –

Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

##  <a name="delete"></a>  CTokenGroups::Delete

Odstraní `CSid` a jeho přidružených atributů z `CTokenGroups` objektu.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu, pro který by měl odebrán identifikátor zabezpečení (SID) a atributy.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud `CSid` Odebereme, false v opačném případě.

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

Odstraní všechny `CSid` objekty a jejich přidružených atributů z `CTokenGroups` objektu.

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

Vrátí počet `CSid` objekty obsažené v `CTokenGroups`.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty a jejich přidruženými atributy, které jsou součástí `CTokenGroups` objektu.

##  <a name="getlength"></a>  CTokenGroups::GetLength

Vrátí velikost položky `CTokenGroup` objektu.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí celkovou velikost `CTokenGroup` objektu v bajtech.

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

Načte ukazatel `TOKEN_GROUPS` struktury.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury, které patří do `CTokenGroups` objekt tokenu přístupu.

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

Načte `CSid` objekty a (volitelně) atributy, které patří k `CTokenGroups` objektu.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Ukazatel na pole [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty.

*pAttributes*<br/>
Ukazatel na pole typu DWORD. Pokud je tento parametr vynechán nebo mít hodnotu NULL, nejsou načíst atributy.

### <a name="remarks"></a>Poznámky

Tato metoda projde všechny `CSid` objekty obsažené v `CTokenGroups` objektu a umístit je a (volitelně příznaků atributu) na pole objektů.

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

Získá atributy přidružené k `CSid` objektu.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.

*pdwAttributes*<br/>
Ukazatel na DWORD, který bude přijímat `CSid` objektu atributu. Pokud vynechán nebo hodnotu NULL, nebude možné načíst atribut.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud `CSid` nenajde, false v opačném případě.

### <a name="remarks"></a>Poznámky

Nastavení *pdwAttributes* na NULL poskytuje způsob, jak potvrzují se existence `CSid` není potřeba přístup k atributu. Všimněte si, že tato metoda by neměla být ke kontrole přístupová práva. Aplikace by měly místo toho používat [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) metody.

##  <a name="operator_eq"></a>  CTokenGroups::operator =

Operátor přiřazení.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`CTokenGroups` Objektu nebo [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktura přiřadit `CTokenGroups` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CTokenGroups` objektu.

##  <a name="operator_const_token_groups__star"></a>  CTokenGroups::operator const TOKEN_GROUPS *

Přetypování na ukazatel na hodnotu `TOKEN_GROUPS` struktury.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Přetypování na ukazatel na hodnotu [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[CSid – třída](../../atl/reference/csid-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
