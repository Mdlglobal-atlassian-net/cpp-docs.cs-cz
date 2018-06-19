---
title: Globální funkce zabezpečení | Microsoft Docs
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
ms.openlocfilehash: ad9ad170706b72c9d236e095db0e2b6df00031ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365051"
---
# <a name="security-global-functions"></a>Globální funkce zabezpečení
Tyto funkce podporují úprav SID a seznamu ACL objektů.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
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
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, pro které chcete získat informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `pDacl`  
 Ukazatel na objekt DACL, který bude obsahovat informace načtené zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud buď `hObject` nebo `pDacl` je neplatný.  
  
##  <a name="atlsetdacl"></a>  AtlSetDacl  
 Voláním této funkce nastavíte informace o volitelném seznamu řízení přístupu (DACL) zadaného objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `rDacl`  
 Seznam DACL, který obsahuje nové informace o zabezpečení.  
  
 `dwInheritanceFlowControl`  
 Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_DACL_SECURITY_INFORMATION nebo UNPROTECTED_DACL_SECURITY_INFORMATION.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `hObject` je neplatná, nebo pokud `dwInheritanceFlowControl` není jednu ze tří povolených hodnot.  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid  
 Voláním této funkce načtete identifikátor zabezpečení skupiny (SID) určitého objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, ze kterého chcete načíst informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `pSid`  
 Ukazatel na `CSid` objekt, který bude obsahovat nové informace o zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid  
 Voláním této funkce nastavíte identifikátor zabezpečení skupiny (SID) určitého objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `rSid`  
 `CSid` Objekt, který obsahuje nové informace o zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid  
 Voláním této funkce načtete identifikátor zabezpečení vlastníka (SID) určitého objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, ze kterého chcete načíst informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `pSid`  
 Ukazatel na `CSid` objekt, který bude obsahovat nové informace o zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid  
 Voláním této funkce nastavíte identifikátor zabezpečení vlastníka (SID) určitého objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `rSid`  
 `CSid` Objekt, který obsahuje nové informace o zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlgetsacl"></a>  AtlGetSacl  
 Voláním této funkce načtete informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, ze kterého chcete načíst informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 `pSacl`  
 Ukazatel na SACL objekt, který bude obsahovat informace načtené zabezpečení.  
  
 `bRequestNeededPrivileges`  
 V případě hodnoty true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovte ji po dokončení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `AtlGetSacl` má být volána mnohokrát na mnoha různých objektů, bude efektivnější povolit oprávnění SE_SECURITY_NAME jednou před voláním funkce, s `bRequestNeededPrivileges` nastavena na hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlsetsacl"></a>  AtlSetSacl  
 Voláním této funkce nastavíte informace o seznamu řízení auditování přístupu (SACL) zadaného objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Popisovač objektu, pro kterou chcete nastavit informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí `hObject` parametr.  
  
 *rSacl*  
 SACL obsahující nové informace o zabezpečení.  
  
 `dwInheritanceFlowControl`  
 Řízení toku dědičnosti. Tato hodnota může být 0 (výchozí), PROTECTED_SACL_SECURITY_INFORMATION nebo UNPROTECTED_SACL_SECURITY_INFORMATION.  
  
 `bRequestNeededPrivileges`  
 V případě hodnoty true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovte ji po dokončení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `hObject` je neplatná, nebo pokud `dwInheritanceFlowControl` není jednu ze tří povolených hodnot.  
  
 Pokud `AtlSetSacl` má být volána mnohokrát na mnoha různých objektů, bude efektivnější povolit oprávnění SE_SECURITY_NAME jednou před voláním funkce, s `bRequestNeededPrivileges` nastavena na hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor  
 Voláním této funkce načtete popisovač zabezpečení daného objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
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
 *pszObjectName*  
 Ukazatel na řetězec ukončené hodnotou null, který určuje název objektu, ze kterého chcete načíst informace o zabezpečení.  
  
 `ObjectType`  
 Určuje hodnotu z [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) výčtu, která určuje typ objektu, na které se identifikovanou pomocí *pszObjectName* parametr.  
  
 *pSecurityDescriptor*  
 Pro objekt, který obdrží popisovač požadovaný zabezpečení.  
  
 *requestedInfo*  
 Sadu [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bitové příznaky, které označují typ informací o zabezpečení pro načtení. Tento parametr může být kombinací následující hodnoty.  
  
 `bRequestNeededPrivileges`  
 V případě hodnoty true, funkce se pokusí povolit oprávnění SE_SECURITY_NAME a obnovte ji po dokončení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `AtlGetSecurityDescriptor` má být volána mnohokrát na mnoha různých objektů, bude efektivnější povolit oprávnění SE_SECURITY_NAME jednou před voláním funkce, s `bRequestNeededPrivileges` nastavena na hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 
   
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
