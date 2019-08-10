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
ms.openlocfilehash: 435ab4756808a530749e110302b73d16a31c38c6
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915515"
---
# <a name="security-global-functions"></a>Globální funkce zabezpečení

Tyto funkce poskytují podporu pro úpravu objektů SID a seznamů ACL.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

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

**Záhlaví:** atlsecurity. h

##  <a name="atlgetdacl"></a>AtlGetDacl

Voláním této funkce načtete informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, pro který mají být načteny informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*pDacl*<br/>
Ukazatel na objekt DACL, který bude obsahovat načtené informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud buď *hObject* nebo *pDacl* není platný.

##  <a name="atlsetdacl"></a>AtlSetDacl

Voláním této funkce nastavíte informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, pro který chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*rDacl*<br/>
DACL obsahující nové informace o zabezpečení.

*dwInheritanceFlowControl*<br/>
Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_DACL_SECURITY_INFORMATION nebo UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud je *hObject* neplatný nebo pokud *dwInheritanceFlowControl* není jedna ze tří přípustných hodnot.
### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid

Voláním této funkce načtete identifikátor zabezpečení skupiny (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, ze kterého mají být načteny informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*pSid*<br/>
Ukazatel na `CSid` objekt, který bude obsahovat nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid

Voláním této funkce nastavíte identifikátor zabezpečení skupiny (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, pro který chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*rSid*<br/>
`CSid` Objekt obsahující nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlgetownersid"></a>AtlGetOwnerSid

Voláním této funkce načtete identifikátor zabezpečení vlastníka (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, ze kterého mají být načteny informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*pSid*<br/>
Ukazatel na `CSid` objekt, který bude obsahovat nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlsetownersid"></a>AtlSetOwnerSid

Voláním této funkce nastavíte identifikátor zabezpečení vlastníka (SID) určitého objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, pro který chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*rSid*<br/>
`CSid` Objekt obsahující nové informace o zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlgetsacl"></a>AtlGetSacl

Voláním této funkce načtete informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Zpracování objektu, ze kterého mají být načteny informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*pSacl*<br/>
Ukazatel na objekt SACL, který bude obsahovat načtené informace o zabezpečení.

*bRequestNeededPrivileges*<br/>
Pokud je hodnota true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovit ji při dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Pokud `AtlGetSacl` se má volat mnohokrát pro mnoho různých objektů, bude efektivnější povolit oprávnění SE_SECURITY_NAME před voláním funkce s *bRequestNeededPrivileges* nastavenou na hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlsetsacl"></a>AtlSetSacl

Voláním této funkce nastavíte informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

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
Zpracování objektu, pro který chcete nastavit informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *hObject* .

*rSacl*<br/>
Seznam SACL obsahující nové informace o zabezpečení.

*dwInheritanceFlowControl*<br/>
Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_SACL_SECURITY_INFORMATION nebo UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
Pokud je hodnota true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovit ji při dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud je *hObject* neplatný nebo pokud *dwInheritanceFlowControl* není jedna ze tří přípustných hodnot.

Pokud `AtlSetSacl` se má volat mnohokrát pro mnoho různých objektů, bude efektivnější povolit oprávnění SE_SECURITY_NAME před voláním funkce s *bRequestNeededPrivileges* nastavenou na hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="atlgetsecuritydescriptor"></a>AtlGetSecurityDescriptor

Voláním této funkce načtete popisovač zabezpečení daného objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

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
Ukazatel na řetězec zakončený hodnotou null, který určuje název objektu, ze kterého mají být načteny informace o zabezpečení.

*ObjectType*<br/>
Určuje hodnotu z výčtu [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-se_object_type) , která označuje typ objektu identifikovaného parametrem *pszObjectName* .

*pSecurityDescriptor*<br/>
Objekt, který přijímá požadovaný popisovač zabezpečení.

*requestedInfo*<br/>
Sada [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) bitových příznaků, které označují typ informací o zabezpečení, které mají být načteny. Tento parametr může být kombinací následujících hodnot.

*bRequestNeededPrivileges*<br/>
Pokud je hodnota true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovit ji při dokončení.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Pokud `AtlGetSecurityDescriptor` se má volat mnohokrát pro mnoho různých objektů, bude efektivnější povolit oprávnění SE_SECURITY_NAME před voláním funkce s *bRequestNeededPrivileges* nastavenou na hodnotu false.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)
