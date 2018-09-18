---
title: Cprivateobjectsecuritydesc – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f69172986a2f9bd3ca7c0b2373bb815a2f52186b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029010"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Cprivateobjectsecuritydesc – třída

Tato třída reprezentuje objekt popisovače zabezpečení privátní objekt.

## <a name="syntax"></a>Syntaxe

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Konstruktor|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Volání této metody pro převod do formátu, který podporuje automatické šíření hodnoty záznamů odvoditelný řízení přístupu (ACE) popisovače zabezpečení a jeho seznamy řízení přístupu (ACL).|
|[CPrivateObjectSecurityDesc::Create](#create)|Volejte tuto metodu za účelem přidělení a inicializace popisovače samorelativní zabezpečení pro privátní objekt vytvořený pomocí volání resource Manageru.|
|[CPrivateObjectSecurityDesc::Get](#get)|Volejte tuto metodu za účelem načtení informací z privátní objekt popisovače zabezpečení.|
|[CPrivateObjectSecurityDesc::Set](#set)|Voláním této metody lze upravit privátní objekt popisovače zabezpečení.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

Tato třída odvozená z [csecuritydesc –](../../atl/reference/csecuritydesc-class.md), poskytuje metody pro vytváření a správu popisovač zabezpečení objektu privátní.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Csecuritydesc –](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

Volání této metody pro převod do formátu, který podporuje automatické šíření hodnoty záznamů odvoditelný řízení přístupu (ACE) popisovače zabezpečení a jeho seznamy řízení přístupu (ACL).

```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Ukazatel [csecuritydesc –](../../atl/reference/csecuritydesc-class.md) objekt odkazující na nadřazený kontejner objektu. Pokud se nadřazený kontejner nepoužívá, je tento parametr hodnotu NULL.

*ObjectType*<br/>
Ukazatel `GUID` struktura, která identifikuje typ objekt přidružený k aktuálnímu objektu. Nastavte *ObjectType* na hodnotu NULL, pokud objekt nemá identifikátor GUID.

*bIsDirectoryObject*<br/>
Určuje, zda nový objekt může obsahovat další objekty. Hodnota true označuje, že tento nový objekt je kontejner. Hodnota false označuje, že nový objekt není kontejner.

*GenericMapping*<br/>
Ukazatel [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) struktura, která určuje mapování z obecných práv u konkrétní práva pro objekt.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí zjistit, zda seznam ACE volitelný řízení přístupu (DACL) a systému seznam řízení přístupu (SACL) popisovače zabezpečení aktuální byly Zdědit z nadřazené popisovač zabezpečení. Volá [ConvertToAutoInheritPrivateObjectSecurity](https://msdn.microsoft.com/library/windows/desktop/aa376403) funkce.

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Konstruktor

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje `CPrivateObjectSecurityDesc` objektu.

##  <a name="dtor"></a>  Cprivateobjectsecuritydesc –:: ~ cprivateobjectsecuritydesc –

Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky a odstraní privátní objekt popisovače zabezpečení.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

Volejte tuto metodu za účelem přidělení a inicializace popisovače samorelativní zabezpečení pro privátní objekt vytvořený pomocí volání resource Manageru.

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
Ukazatel [csecuritydesc –](../../atl/reference/csecuritydesc-class.md) objekt odkazující na nadřazený adresář, ve kterém se vytváří nový objekt. Nastavte na hodnotu NULL, pokud není žádný nadřazený adresář.

*pCreator*<br/>
Ukazatel do popisovače zabezpečení poskytované tvůrce objektu. Pokud tvůrce objektu informací o zabezpečení pro nový objekt explicitně nepředá, nastavte tento parametr na hodnotu NULL.

*bIsDirectoryObject*<br/>
Určuje, zda nový objekt může obsahovat další objekty. Hodnota true označuje, že tento nový objekt je kontejner. Hodnota false označuje, že nový objekt není kontejner.

*Token*<br/>
Odkaz [caccesstoken –](../../atl/reference/caccesstoken-class.md) objekt pro proces, jehož jménem se vytváří objekt.

*GenericMapping*<br/>
Ukazatel [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) struktura, která určuje mapování z obecných práv u konkrétní práva pro objekt.

*ObjectType*<br/>
Ukazatel `GUID` struktura, která identifikuje typ objekt přidružený k aktuálnímu objektu. Nastavte *ObjectType* na hodnotu NULL, pokud objekt nemá identifikátor GUID.

*bIsContainerObject*<br/>
Určuje, zda nový objekt může obsahovat další objekty. Hodnota true označuje, že tento nový objekt je kontejner. Hodnota false označuje, že nový objekt není kontejner.

*AutoInheritFlags*<br/>
Sadu bitových příznaků, které řídí, jak jsou zděděné položky řízení přístupu (ACE) z *pParent*. Zobrazit [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CreatePrivateObjectSercurity](https://msdn.microsoft.com/library/windows/desktop/aa376405) nebo [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581).

Druhá metoda umožňuje určit typ objektu identifikátor GUID nového objektu nebo řízení, jak jsou zděděné položky řízení přístupu.

> [!NOTE]
>  Popisovač zabezpečení samorelativní je popisovač zabezpečení, která ukládá všechny jeho informace o zabezpečení v souvislém bloku paměti.

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

Volejte tuto metodu za účelem načtení informací z privátní objekt popisovače zabezpečení.

```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Sadu bitových příznaků, které označují součásti popisovač zabezpečení pro načtení. Tato hodnota může být kombinací [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) bitové příznaky.

*pResult*<br/>
Ukazatel [csecuritydesc –](../../atl/reference/csecuritydesc-class.md) objekt, který přijímá kopii požadované informace z Zadaný popisovač zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení je struktura a související data, která obsahuje informace o zabezpečení pro zabezpečitelný objekt.

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

Operátor přiřazení.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`CPrivateObjectSecurityDesc` Objektu, který chcete přiřadit k aktuálnímu objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CPrivateObjectSecurityDesc` objektu.

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

Voláním této metody lze upravit privátní objekt popisovače zabezpečení.

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
Sadu bitových příznaků, které označují části nastavit popisovač zabezpečení. Tato hodnota může být kombinací [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) bitové příznaky.

*Úpravy*<br/>
Ukazatel [csecuritydesc –](../../atl/reference/csecuritydesc-class.md) objektu. Součástí tohoto popisovače zabezpečení indikován *si* parametrů se použijí pro popisovač zabezpečení objektu.

*GenericMapping*<br/>
Ukazatel [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) struktura, která určuje mapování z obecných práv u konkrétní práva pro objekt.

*Token*<br/>
Odkaz [caccesstoken –](../../atl/reference/caccesstoken-class.md) objekt pro proces, jehož jménem se vytváří objekt.

*AutoInheritFlags*<br/>
Sadu bitových příznaků, které řídí, jak jsou zděděné položky řízení přístupu (ACE) z *pParent*. Zobrazit [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Druhá metoda umožňuje určit typ objektu identifikátor GUID objektu nebo řízení, jak jsou zděděné položky řízení přístupu.

## <a name="see-also"></a>Viz také

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc – třída](../../atl/reference/csecuritydesc-class.md)
