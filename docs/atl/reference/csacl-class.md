---
title: Csacl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 817875dd32457fa47eafca9d634bc2e7cc8e079d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206567"
---
# <a name="csacl-class"></a>Csacl – třída
Tato třída představuje obálku pro strukturu SACL (seznam řízení přístupu systému).  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|Konstruktor|  
|[Csacl –:: ~ csacl –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|Přidá k auditu řízení přístupu (ACE) `CSacl` objektu.|  
|[CSacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (ACE), které se `CSacl` objektu.|  
|[CSacl::RemoveAce](#removeace)|Odebere z konkrétní ACE (položky řízení přístupu) `CSacl` objektu.|  
|[CSacl::RemoveAllAces](#removeallaces)|Odebere všechny položky obsažené v řízení přístupu `CSacl` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 SACL obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení řadiče domény. Všimněte si, že SACL generuje položky protokolu pouze na řadiči domény, kde došlo k pokusu o přístup, ne na všech řadičích domény, který obsahuje repliku objektu.  
  
 K nastavení nebo načtení SACL v objektu popisovače zabezpečení, musí být povoleno oprávnění SE_SECURITY_NAME v přístupovém tokenu žádající vlákna. Tato oprávnění udělena ve výchozím nastavení má skupina administrators a mohl být přidělen na jiné uživatele nebo skupiny. Máte oprávnění udělena není vše, co se vyžaduje: před provedením operace definované oprávnění, musí být povolené oprávnění v přístupovém tokenu zabezpečení k projeví. Model umožňuje oprávnění povolen pouze pro konkrétní systém operace, a potom zakázán, když už nejsou potřeba. Zobrazit [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl) příklady povolení SE_SECURITY_NAME.  
  
 Používat metody třídy přidat, odebrat, vytvářet a odstraňovat položky řízení přístupu z k dispozici `SACL` objektu. Viz také [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl).  
  
 Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Cacl –](../../atl/reference/cacl-class.md)  
  
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
 *rSid*  
 [Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.  
  
 *AccessMask*  
 Určuje masku přístupová práva, které se budou auditovat pro zadaný rozbočovač `CSid` objektu.  
  
 *bSuccess*  
 Určuje, zda mají být zaznamenávány pokusů o přístup povolený. Nastavit tento příznak, který true pro povolení auditování; jinak ji nastavte na hodnotu false.  
  
 *bFailure*  
 Určuje, zda pokusy o odepření přístupu budou auditovány. Nastavit tento příznak, který true pro povolení auditování; jinak ji nastavte na hodnotu false.  
  
 *AceFlags*  
 Sadu bitových příznaků, které řídí ACE dědičnosti.  
  
 *pObjectType*  
 Typ objektu.  
  
 *pInheritedObjectType*  
 Typ zděděných objektů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí TRUE, pokud je položka řízení přístupu se přidá do `CSacl` objektu NEPRAVDA při selhání.  
  
### <a name="remarks"></a>Poznámky  
 A `CSacl` objekt obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení. Tato metoda přidá tyto ESEM k `CSacl` objektu.  
  
 Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) popis různé příznaky, které je možné nastavit v *AceFlags* parametru.  
  
##  <a name="csacl"></a>  CSacl::CSacl  
 Konstruktor  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *Zarovnání indirekce RHS*  
 Existující `ACL` struktury (seznamu řízení přístupu).  
  
### <a name="remarks"></a>Poznámky  
 `CSacl` Objekt můžete případně vytvořit pomocí existující `ACL` struktury. Ujistěte se, že tento parametr je systémový seznam řízení přístupu (SACL) a nikoli seznam volitelných řízení přístupu (DACL). V sestavení ladění, pokud je DACL zadaný kontrolní výraz dojde. V sestaveních pro vydání jsou ignorovány všechny položky ze seznamu DACL.  
  
##  <a name="dtor"></a>  Csacl –:: ~ csacl –  
 Destruktor.  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktor uvolní všechny prostředky získané v objektu, včetně všech položek řízení přístupu (ACE).  
  
##  <a name="getacecount"></a>  CSacl::GetAceCount  
 Vrátí počet položek řízení přístupu (ACE), které se `CSacl` objektu.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet součástí položky řízení přístupu `CSacl` objektu.  
  
##  <a name="operator_eq"></a>  CSacl::operator =  
 Operátor přiřazení.  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *Zarovnání indirekce RHS*  
 `ACL` (Seznam řízení přístupu) přiřadit existující objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktualizovaný `CSacl` objektu. Ujistěte se, `ACL` parametr je ve skutečnosti seznam řízení přístupu systému (SACL) a nikoli seznam volitelných řízení přístupu (DACL). V sestavení ladění, dojde k kontrolní výraz a v sestaveních pro vydání `ACL` parametr bude ignorován.  
  
##  <a name="removeace"></a>  CSacl::RemoveAce  
 Odebere z konkrétní ACE (položky řízení přístupu) `CSacl` objektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Index položky ACE odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je odvozen z [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CSacl::RemoveAllAces  
 Odebere všechny položky řízení přístupu (ACE), součástí `CSacl` objektu.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny `ACE` strukturu (pokud existuje) v `CSacl` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Cacl – třída](../../atl/reference/cacl-class.md)   
 [Seznamy ACL](/windows/desktop/SecAuthZ/access-control-lists)   
 [Položky řízení přístupu](/windows/desktop/SecAuthZ/access-control-entries)   
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
