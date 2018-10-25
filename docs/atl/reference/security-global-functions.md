---
title: Globální funkce zabezpečení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbac8dc499c08d96abd33d49f5adec08095ca420
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067290"
---
# <a name="security-global-functions"></a>Globální funkce zabezpečení

Tyto funkce poskytují podporu pro úpravu objektů SID a seznamu ACL.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AtlGetDacl](#atlgetdacl)|Voláním této funkce načtete informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.|
|[AtlSetDacl](#atlsetdacl)|Voláním této funkce nastavíte informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.|
|[AtlGetGroupSid](#atlgetgroupsid)|Voláním této funkce načtete identifikátor zabezpečení skupiny (SID) určitého objektu.|
|[AtlSetGroupSid](#atlsetgroupsid)|Voláním této funkce nastavíte identifikátor zabezpečení skupiny (SID) určitého objektu.|
|[AtlGetOwnerSid](#atlgetownersid)|Voláním této funkce načtete identifikátor zabezpečení vlastníka (SID) určitého objektu.|
|[AtlSetOwnerSid](#atlsetownersid)|Voláním této funkce nastavíte identifikátor zabezpečení vlastníka (SID) určitého objektu.|
|[AtlGetSacl](#atlgetsacl)|Voláním této funkce načtete informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.|
|[AtlSetSacl](#atlsetsacl)|Voláním této funkce nastavíte informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Voláním této funkce načtete popisovač zabezpečení daného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlgetdacl"></a>  AtlGetDacl

Voláním této funkce načtete informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, pro které chcete načíst informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*pDacl*<br/>
Ukazatel na objekt DACL, který bude obsahovat informace o načtených zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *hObject* nebo *pDacl* je neplatný.

##  <a name="atlsetdacl"></a>  AtlSetDacl

Voláním této funkce nastavíte informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*rDacl*<br/>
Seznam DACL, který obsahuje nové informace o zabezpečení.

*dwInheritanceFlowControl*<br/>
Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_DACL_SECURITY_INFORMATION nebo UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *hObject* je neplatný, nebo pokud *dwInheritanceFlowControl* není jedním ze tří povolených hodnot.
### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid

Voláním této funkce načtete identifikátor zabezpečení skupiny (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, ze kterého se má načíst informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*psid má*<br/>
Ukazatel `CSid` objekt, který bude obsahovat nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid

Voláním této funkce nastavíte identifikátor zabezpečení skupiny (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*rSid*<br/>
`CSid` Objekt, který obsahuje nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid

Voláním této funkce načtete identifikátor zabezpečení vlastníka (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, ze kterého se má načíst informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*psid má*<br/>
Ukazatel `CSid` objekt, který bude obsahovat nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid

Voláním této funkce nastavíte identifikátor zabezpečení vlastníka (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*rSid*<br/>
`CSid` Objekt, který obsahuje nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlgetsacl"></a>  AtlGetSacl

Voláním této funkce načtete informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, ze kterého se má načíst informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*pSacl*<br/>
Ukazatel na objekt SACL, která bude obsahovat informace o načtených zabezpečení.

*bRequestNeededPrivileges*<br/>
Pokud je hodnota true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovte ji po dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Pokud `AtlGetSacl` má být volána v mnoha případech na mnoho různých objektů, je efektivnější povolit oprávnění SE_SECURITY_NAME jednou před voláním funkce, s *bRequestNeededPrivileges* nastavena na hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlsetsacl"></a>  AtlSetSacl

Voláním této funkce nastavíte informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *hObject* parametru.

*rSacl*<br/>
SACL, který obsahuje nové informace o zabezpečení.

*dwInheritanceFlowControl*<br/>
Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_SACL_SECURITY_INFORMATION nebo UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
Pokud je hodnota true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovte ji po dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *hObject* je neplatný, nebo pokud *dwInheritanceFlowControl* není jedním ze tří povolených hodnot.

Pokud `AtlSetSacl` má být volána v mnoha případech na mnoho různých objektů, je efektivnější povolit oprávnění SE_SECURITY_NAME jednou před voláním funkce, s *bRequestNeededPrivileges* nastavena na hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor

Voláním této funkce načtete popisovač zabezpečení daného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*pszObjectName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název objektu, ze kterého se má načíst informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) výčet, který určuje typ objektu identifikován *pszObjectName* parametru.

*pSecurityDescriptor*<br/>
Objekt, který přijímá požadovanou v popisovači.

*requestedInfo*<br/>
Sada [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) bitové příznaky, které označují typ informací o zabezpečení pro načtení. Tento parametr může být kombinací těchto hodnot.

*bRequestNeededPrivileges*<br/>
Pokud je hodnota true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovte ji po dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Pokud `AtlGetSecurityDescriptor` má být volána v mnoha případech na mnoho různých objektů, je efektivnější povolit oprávnění SE_SECURITY_NAME jednou před voláním funkce, s *bRequestNeededPrivileges* nastavena na hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)
