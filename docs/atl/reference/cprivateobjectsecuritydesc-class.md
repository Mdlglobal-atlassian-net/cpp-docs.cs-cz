---
title: CPrivateObjectSecurityDesc Class
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
ms.openlocfilehash: 97ea2b8411b404caf9f833ad85f226d18aea1e73
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496572"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc Class

Tato třída reprezentuje objekt popisovače zabezpečení privátního objektu.

## <a name="syntax"></a>Syntaxe

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Konstruktor|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Voláním této metody můžete převést popisovač zabezpečení a seznamy řízení přístupu (ACL) na formát, který podporuje automatické šíření dědičných položek řízení přístupu (ACE).|
|[CPrivateObjectSecurityDesc::Create](#create)|Voláním této metody přidělíte a inicializujete samostatný relativní popisovač zabezpečení pro privátní objekt vytvořený volajícím správcem prostředků.|
|[CPrivateObjectSecurityDesc::Get](#get)|Voláním této metody načtete informace z popisovače zabezpečení privátního objektu.|
|[CPrivateObjectSecurityDesc::Set](#set)|Voláním této metody upravíte popisovač zabezpečení privátního objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

Tato třída odvozená z [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)poskytuje metody pro vytváření a správu popisovačů zabezpečení soukromého objektu.

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

Voláním této metody můžete převést popisovač zabezpečení a seznamy řízení přístupu (ACL) na formát, který podporuje automatické šíření dědičných položek řízení přístupu (ACE).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Ukazatel na objekt [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odkazující na nadřazený kontejner objektu. Pokud není k dispozici žádný nadřazený kontejner, tento parametr má hodnotu NULL.

*ObjectType*<br/>
Ukazatel na `GUID` strukturu, která identifikuje typ objektu přidruženého k aktuálnímu objektu. Nastavte *ObjectType* na null, pokud objekt neobsahuje identifikátor GUID.

*bIsDirectoryObject*<br/>
Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true značí, že nový objekt je kontejner. Hodnota false znamená, že nový objekt není kontejner.

*GenericMapping*<br/>
Ukazatel na strukturu [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) , která určuje mapování z každého obecného práva na specifická práva pro daný objekt.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí zjistit, jestli jsou položky ACE v seznamu řízení přístupu (DACL) a seznam řízení přístupu (SACL) aktuálního popisovače zabezpečení zděděné z nadřazeného popisovače zabezpečení. Volá funkci [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) .

##  <a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Konstruktor

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

`CPrivateObjectSecurityDesc` Inicializuje objekt.

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky a odstraní popisovač zabezpečení privátního objektu.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

Voláním této metody přidělíte a inicializujete samostatný relativní popisovač zabezpečení pro privátní objekt vytvořený volajícím správcem prostředků.

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
Ukazatel na objekt [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odkazující na nadřazený adresář, ve kterém se vytváří nový objekt. Nastavte na hodnotu NULL, pokud není k dispozici žádný nadřazený adresář.

*pCreator*<br/>
Ukazatel na popisovač zabezpečení poskytnutý autorem objektu. Pokud tvůrce objektu explicitně neprojde informace o zabezpečení nového objektu, nastavte tento parametr na hodnotu NULL.

*bIsDirectoryObject*<br/>
Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true značí, že nový objekt je kontejner. Hodnota false znamená, že nový objekt není kontejner.

*Klíčové*<br/>
Odkaz na objekt [CAccessToken](../../atl/reference/caccesstoken-class.md) pro klientský proces, jehož jménem se objekt vytváří.

*GenericMapping*<br/>
Ukazatel na strukturu [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) , která určuje mapování z každého obecného práva na specifická práva pro daný objekt.

*ObjectType*<br/>
Ukazatel na `GUID` strukturu, která identifikuje typ objektu přidruženého k aktuálnímu objektu. Nastavte *ObjectType* na null, pokud objekt neobsahuje identifikátor GUID.

*bIsContainerObject*<br/>
Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true značí, že nový objekt je kontejner. Hodnota false znamená, že nový objekt není kontejner.

*AutoInheritFlags*<br/>
Sada bitových příznaků, které řídí způsob dědění položek řízení přístupu (ACE) z *pParent*. Další podrobnosti najdete v tématu [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) .

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) nebo [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

Druhá metoda povoluje zadání identifikátoru GUID typu objektu nového objektu nebo řízení způsobu dědění položek ACE.

> [!NOTE]
>  Samostatný relativní popisovač zabezpečení je popisovač zabezpečení, který ukládá všechny informace o zabezpečení do souvislého bloku paměti.

##  <a name="get"></a>CPrivateObjectSecurityDesc:: Get

Voláním této metody načtete informace z popisovače zabezpečení privátního objektu.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Sada bitových příznaků, které označují části popisovače zabezpečení, které se mají načíst. Tato hodnota může být kombinací bitových příznaků [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) .

*pResult*<br/>
Ukazatel na objekt [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) , který obdrží kopii požadovaných informací ze zadaného popisovače zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení je struktura a přidružená data, která obsahují informace o zabezpečení pro zabezpečitelný objekt.

##  <a name="operator_eq"></a>CPrivateObjectSecurityDesc:: operator =

Operátor přiřazení

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
`CPrivateObjectSecurityDesc` Objekt, který se má přiřadit k aktuálnímu objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CPrivateObjectSecurityDesc` objekt.

##  <a name="set"></a>CPrivateObjectSecurityDesc:: set

Voláním této metody upravíte popisovač zabezpečení privátního objektu.

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
Sada bitových příznaků, které označují části popisovače zabezpečení, které mají být nastaveny. Tato hodnota může být kombinací bitových příznaků [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) .

*Měně*<br/>
Ukazatel na objekt [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) . Části tohoto popisovače zabezpečení označené parametrem *si* jsou aplikovány na popisovač zabezpečení objektu.

*GenericMapping*<br/>
Ukazatel na strukturu [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) , která určuje mapování z každého obecného práva na specifická práva pro daný objekt.

*Klíčové*<br/>
Odkaz na objekt [CAccessToken](../../atl/reference/caccesstoken-class.md) pro klientský proces, jehož jménem se objekt vytváří.

*AutoInheritFlags*<br/>
Sada bitových příznaků, které řídí způsob dědění položek řízení přístupu (ACE) z *pParent*. Další podrobnosti najdete v tématu [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) .

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Druhá metoda povoluje zadání identifikátoru GUID objektu nebo řízení způsobu, jakým jsou zděděny položky ACE.

## <a name="see-also"></a>Viz také:

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc – třída](../../atl/reference/csecuritydesc-class.md)
