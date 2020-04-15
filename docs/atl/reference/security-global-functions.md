---
title: Globální funkce zabezpečení
ms.date: 11/04/2016
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
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326024"
---
# <a name="security-global-functions"></a>Globální funkce zabezpečení

Tyto funkce poskytují podporu pro úpravu objektů SID a ACL.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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
|[Popisovač AtlGetSecurity](#atlgetsecuritydescriptor)|Voláním této funkce načtete popisovač zabezpečení daného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl

Voláním této funkce načtete informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, pro který chcete načíst informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*pDacl*<br/>
Ukazatel na objekt DACL, který bude obsahovat načtené informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud je *neplatný objekt hObject* nebo *pDacl.*

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>AtlSetDacl

Voláním této funkce nastavíte informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, pro který chcete nastavit informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*rDacl*<br/>
Seznam DACL obsahující nové informace o zabezpečení.

*dwInheritanceFlowControl*<br/>
Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_DACL_SECURITY_INFORMATION nebo UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě výrazu, pokud *hObject* je neplatný nebo pokud *dwInheritanceFlowControl* není jednou ze tří povolených hodnot.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid

Voláním této funkce načtete identifikátor zabezpečení skupiny (SID) určitého objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, ze kterého chcete načíst informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*pSid*<br/>
Ukazatel na `CSid` objekt, který bude obsahovat nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid

Voláním této funkce nastavíte identifikátor zabezpečení skupiny (SID) určitého objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, pro který chcete nastavit informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*rSid*<br/>
Objekt `CSid` obsahující nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid

Voláním této funkce načtete identifikátor zabezpečení vlastníka (SID) určitého objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, ze kterého chcete načíst informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*pSid*<br/>
Ukazatel na `CSid` objekt, který bude obsahovat nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid

Voláním této funkce nastavíte identifikátor zabezpečení vlastníka (SID) určitého objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, pro který chcete nastavit informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*rSid*<br/>
Objekt `CSid` obsahující nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>AtlGetSacl

Voláním této funkce načtete informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, ze kterého chcete načíst informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*pSacl*<br/>
Ukazatel na objekt SACL, který bude obsahovat načtené informace o zabezpečení.

*bRequestNeededPrivileges*<br/>
Pokud true, funkce se pokusí povolit SE_SECURITY_NAME oprávnění a obnovit po dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Pokud `AtlGetSacl` má být volána mnohokrát na mnoha různých objektů, bude efektivnější povolit SE_SECURITY_NAME oprávnění jednou před voláním funkce, s *bRequestNeededPrivileges* nastavena na false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>AtlSetSacl

Voláním této funkce nastavíte informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Zpracovat objekt, pro který chcete nastavit informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *hObject.*

*rSacl*<br/>
SACL obsahující nové informace o zabezpečení.

*dwInheritanceFlowControl*<br/>
Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_SACL_SECURITY_INFORMATION nebo UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
Pokud true, funkce se pokusí povolit SE_SECURITY_NAME oprávnění a obnovit po dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě výrazu, pokud *hObject* je neplatný nebo pokud *dwInheritanceFlowControl* není jednou ze tří povolených hodnot.

Pokud `AtlSetSacl` má být volána mnohokrát na mnoha různých objektů, bude efektivnější povolit SE_SECURITY_NAME oprávnění jednou před voláním funkce, s *bRequestNeededPrivileges* nastavena na false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>Popisovač AtlGetSecurity

Voláním této funkce načtete popisovač zabezpečení daného objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

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

*pszName_*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje název objektu, ze kterého chcete načíst informace o zabezpečení.

*Objecttype*<br/>
Určuje hodnotu z [výčtu SE_OBJECT_TYPE,](/windows/win32/api/accctrl/ne-accctrl-se_object_type) která označuje typ objektu identifikovaný parametrem *pszObjectName.*

*popisovač zabezpečení*<br/>
Objekt, který obdrží požadovaný popisovač zabezpečení.

*requestedInfo*<br/>
Sada [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) bitových příznaků, které označují typ informací o zabezpečení, které mají být načteny. Tento parametr může být kombinací následujících hodnot.

*bRequestNeededPrivileges*<br/>
Pokud true, funkce se pokusí povolit SE_SECURITY_NAME oprávnění a obnovit po dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Pokud `AtlGetSecurityDescriptor` má být volána mnohokrát na mnoha různých objektů, bude efektivnější povolit SE_SECURITY_NAME oprávnění jednou před voláním funkce, s *bRequestNeededPrivileges* nastavena na false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
