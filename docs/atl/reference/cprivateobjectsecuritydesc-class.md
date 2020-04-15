---
title: Třída CPrivateObjectSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331409"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Třída CPrivateObjectSecurityDesc

Tato třída představuje objekt popisovače zabezpečení soukromého objektu.

## <a name="syntax"></a>Syntaxe

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecuritySecurityDesc](#cprivateobjectsecuritydesc)|Konstruktor|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecuritySecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Volání této metody převést popisovač zabezpečení a jeho seznamy řízení přístupu (ACN) do formátu, který podporuje automatické šíření dědičné položky řízení přístupu (ACE).|
|[CPrivateObjectSecurityDesc::Vytvořit](#create)|Volání této metody přidělit a inicializovat deskriptor zabezpečení relativní pro soukromý objekt vytvořený správcem prostředků volání.|
|[CPrivateObjectSecurityDesc::Získat](#get)|Volání této metody k načtení informací z popisovače zabezpečení soukromého objektu.|
|[CPrivateObjectSecurityDesc::Set](#set)|Volání této metody upravit popisovač zabezpečení soukromého objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

Tato třída, odvozená z [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), poskytuje metody pro vytváření a správu popisovače zabezpečení soukromého objektu.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit

Volání této metody převést popisovač zabezpečení a jeho seznamy řízení přístupu (ACN) do formátu, který podporuje automatické šíření dědičné položky řízení přístupu (ACE).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Ukazatel na [cSecurityDesc](../../atl/reference/csecuritydesc-class.md) objekt odkazující na nadřazený kontejner objektu. Pokud neexistuje žádný nadřazený kontejner, tento parametr je NULL.

*Objecttype*<br/>
Ukazatel na `GUID` strukturu, která identifikuje typ objektu přidruženého k aktuálnímu objektu. Pokud objekt nemá identifikátor GUID, nastavte *objekt ObjectType* na hodnotu NULL.

*bIsDirectoryObject*<br/>
Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true označuje, že nový objekt je kontejner. Hodnota false označuje, že nový objekt není kontejner.

*Obecné mapování*<br/>
Ukazatel na [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) strukturu, která určuje mapování z každého obecného práva na určitá práva pro objekt.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí zjistit, zda ace v seznamu řízení přístupu (DACL) a systému řízení přístupu (SACL) aktuální popisovač zabezpečení byly zděděny z popisovače nadřazeného zabezpečení. Volá funkci [ConvertToAutoInheritPrivateObjectSecurity.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecuritySecurityDesc

Konstruktor

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje `CPrivateObjectSecurityDesc` objekt.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc::~CPrivateObjectSecuritySecurityDesc

Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky a odstraní popisovač zabezpečení soukromého objektu.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Vytvořit

Volání této metody přidělit a inicializovat deskriptor zabezpečení relativní pro soukromý objekt vytvořený správcem prostředků volání.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Ukazatel na objekt [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odkazující na nadřazený adresář, ve kterém je vytvářen nový objekt. Pokud neexistuje žádný nadřazený adresář, nastavte hodnotu NULL.

*pTvůrce*<br/>
Ukazatel na popisovač zabezpečení poskytnutý tvůrcem objektu. Pokud tvůrce objektu explicitně nepředá informace o zabezpečení pro nový objekt, nastavte tento parametr na HODNOTU NULL.

*bIsDirectoryObject*<br/>
Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true označuje, že nový objekt je kontejner. Hodnota false označuje, že nový objekt není kontejner.

*Token*<br/>
Odkaz na objekt [CAccessToken](../../atl/reference/caccesstoken-class.md) pro proces klienta, jehož jménem je objekt vytvářen.

*Obecné mapování*<br/>
Ukazatel na [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) strukturu, která určuje mapování z každého obecného práva na určitá práva pro objekt.

*Objecttype*<br/>
Ukazatel na `GUID` strukturu, která identifikuje typ objektu přidruženého k aktuálnímu objektu. Pokud objekt nemá identifikátor GUID, nastavte *objekt ObjectType* na hodnotu NULL.

*bIsContainerObject*<br/>
Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true označuje, že nový objekt je kontejner. Hodnota false označuje, že nový objekt není kontejner.

*AutoInheritFlags*<br/>
Sada bitových příznaků, které řídí, jak jsou zděděny položky řízení přístupu (ACE) z *pParent*. Další podrobnosti najdete [v tématu CreatePrivateObjectSecurityEx.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) nebo [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

Druhá metoda umožňuje určení typu objektu GUID nového objektu nebo řízení způsobu zdědění objektů Řízení anutů.

> [!NOTE]
> Deskriptor zabezpečení relativní k sobě je popisovač zabezpečení, který ukládá všechny své informace o zabezpečení v souvislém bloku paměti.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Získat

Volání této metody k načtení informací z popisovače zabezpečení soukromého objektu.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Sada bitových příznaků, které označují části popisovače zabezpečení, které mají být načteny. Tato hodnota může být kombinací [příznaků bitu SECURITY_INFORMATION.](/windows/win32/SecAuthZ/security-information)

*výsledek*<br/>
Ukazatel na [csecuritydesc](../../atl/reference/csecuritydesc-class.md) objekt, který obdrží kopii požadovaných informací z deskriptoru zadaného zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení je struktura a přidružená data, která obsahuje informace o zabezpečení zabezpečeného objektu.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::operátor =

Operátor přiřazení.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Objekt, `CPrivateObjectSecurityDesc` který má být přiřazen aktuálnímu objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CPrivateObjectSecurityDesc` objekt.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Set

Volání této metody upravit popisovač zabezpečení soukromého objektu.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Sada bitových příznaků, které označují části popisovače zabezpečení, které chcete nastavit. Tato hodnota může být kombinací [příznaků bitu SECURITY_INFORMATION.](/windows/win32/SecAuthZ/security-information)

*Úpravy*<br/>
Ukazatel na [csecuritydesc](../../atl/reference/csecuritydesc-class.md) objektu. Části tohoto popisovače zabezpečení označené parametrem *si* jsou použity na popisovač zabezpečení objektu.

*Obecné mapování*<br/>
Ukazatel na [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) strukturu, která určuje mapování z každého obecného práva na určitá práva pro objekt.

*Token*<br/>
Odkaz na objekt [CAccessToken](../../atl/reference/caccesstoken-class.md) pro proces klienta, jehož jménem je objekt vytvářen.

*AutoInheritFlags*<br/>
Sada bitových příznaků, které řídí, jak jsou zděděny položky řízení přístupu (ACE) z *pParent*. Další podrobnosti najdete [v tématu CreatePrivateObjectSecurityEx.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Druhá metoda umožňuje určení typu objektu GUID objektu nebo řízení způsobu zdědění objektů ACE.

## <a name="see-also"></a>Viz také

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)<br/>
[Třída CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
