---
title: Třída CSacl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116e66d36dde016ef902a0b345eec33e46177b6c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363581"
---
# <a name="csacl-class"></a>CSacl – třída
Tato třída je obálku pro strukturu SACL (seznam řízení přístupu systému).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|Konstruktor|  
|[CSacl:: ~ CSacl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|Přidá k auditu řízení přístupu (ACE) `CSacl` objektu.|  
|[CSacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (ACE) `CSacl` objektu.|  
|[CSacl::RemoveAce](#removeace)|Odebere konkrétní ACE (položky řízení přístupu) **CSacl** objektu.|  
|[CSacl::RemoveAllAces](#removeallaces)|Odebere všechny položky řízení přístupu součástí `CSacl` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 Seznam SACL obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení řadiče domény. Všimněte si, že seznam SACL generuje položky protokolu pouze v řadiči domény, kde došlo k pokusu o přístup, není na každém řadiči domény, který obsahuje repliku objektu.  
  
 Nastavit nebo načíst SACL v popisovač zabezpečení objektu, musí být povoleno oprávnění SE_SECURITY_NAME v tokenu přístupu z požadavku vlákno. Toto oprávnění udělená ve výchozím nastavení má skupina administrators a mohl být přidělen na jiné uživatele nebo skupiny. Má oprávnění uděleno není všechny, která je nutná: před provedením operace definované oprávnění, musí být povoleno oprávnění v přístupový token zabezpečení aby vstoupila v platnost. Model umožňuje oprávnění být povolen pouze pro konkrétního systému operace, a pak zakázán, když už nejsou potřeba. V tématu [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl) příklady povolení SE_SECURITY_NAME.  
  
 Používat metody třídy poskytuje přidat, odebrat, vytvářet a odstraňovat položky řízení přístupu z **SACL** objektu. Viz také [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl).  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="addauditace"></a>  CSacl::AddAuditAce  
 Přidá k auditu řízení přístupu (ACE) `CSacl` objektu.  
  
```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.  
  
 `AccessMask`  
 Určuje masku přístupová práva k auditování pro zadaný `CSid` objektu.  
  
 `bSuccess`  
 Určuje, zda mají vždycky možné auditovat pokusy o povolený přístup. Nastavit tento příznak na hodnotu PRAVDA, aby povolit auditování; jinak ji nastavte na hodnotu false.  
  
 *bFailure*  
 Určuje, zda mají být auditovat pokusy o odepření přístupu. Nastavit tento příznak na hodnotu PRAVDA, aby povolit auditování; jinak ji nastavte na hodnotu false.  
  
 `AceFlags`  
 Sada bitové příznaky, které řídí ACE dědičnosti.  
  
 `pObjectType`  
 Typ objektu.  
  
 `pInheritedObjectType`  
 Typ zděděné objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je položka řízení přístupu je přidán do `CSacl` objekt, **false** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 A `CSacl` objekt obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení. Tato metoda přidá ACE, na `CSacl` objektu.  
  
 V tématu [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) popis různé příznaky, které lze nastavit v `AceFlags` parametr.  
  
##  <a name="csacl"></a>  CSacl::CSacl  
 Konstruktor  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Existující **seznamu ACL** struktury (seznamu řízení přístupu).  
  
### <a name="remarks"></a>Poznámky  
 `CSacl` Objekt můžete volitelně vytvořit pomocí existující **seznamu ACL** struktura. Ujistěte se, že tento parametr je systémový seznam řízení přístupu (SACL) a ne seznamu volitelného řízení přístupu (DACL). V sestavení pro ladění, pokud je zadaný seznam DACL kontrolní výrazy dojde. Ve verzi sestavení jsou ignorovány všechny položky DACL.  
  
##  <a name="dtor"></a>  CSacl:: ~ CSacl  
 Destruktor.  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny prostředky, které získávají pomocí objektu, včetně všech položek řízení přístupu (ACE).  
  
##  <a name="getacecount"></a>  CSacl::GetAceCount  
 Vrátí počet položek řízení přístupu (ACE) `CSacl` objektu.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet ACE, které jsou součástí `CSacl` objektu.  
  
##  <a name="operator_eq"></a>  CSacl::operator =  
 Operátor přiřazení.  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 **Seznamu ACL** (seznam řízení přístupu) přiřadit existující objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktualizaci `CSacl` objektu. Ujistěte se, že **seznamu ACL** parametr je ve skutečnosti seznamu řízení přístupu systému (SACL) a není seznamu volitelného řízení přístupu (DACL). V sestavení pro ladění dojde k kontrolní výrazy a v sestavení pro vydání **seznamu ACL** parametr bude ignorován.  
  
##  <a name="removeace"></a>  CSacl::RemoveAce  
 Odebere konkrétní ACE (položky řízení přístupu) **CSacl** objektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index ACE položku k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je odvozený od [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CSacl::RemoveAllAces  
 Odebere všechny položky řízení přístupu (ACE), součástí `CSacl` objektu.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny **ACE** struktury (pokud existuje) v `CSacl` objektu.  
  
## <a name="see-also"></a>Viz také  
 [CAcl – třída](../../atl/reference/cacl-class.md)   
 [Seznamy ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
