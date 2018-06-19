---
title: Třída CDacl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2724eebd218cea2795d483351ef91b34c9f1bf39
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364767"
---
# <a name="cdacl-class"></a>CDacl – třída
Tato třída je obálku pro strukturu DACL (seznam volitelného řízení přístupu).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|Konstruktor|  
|[CDacl::~CDacl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|Přidá povolené prostředí ACE (položky řízení přístupu) `CDacl` objektu.|  
|[CDacl::AddDeniedAce](#adddeniedace)|Přidá odepření ACE k `CDacl` objektu.|  
|[CDacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (položky řízení přístupu) `CDacl` objektu.|  
|[CDacl::RemoveAce](#removeace)|Odebere konkrétní ACE (položky řízení přístupu) `CDacl` objektu.|  
|[CDacl::RemoveAllAces](#removeallaces)|Odebere všechny položky řízení přístupu součástí `CDacl` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 Popisovač zabezpečení objektu může obsahovat seznam DACL. Seznam DACL obsahuje nula nebo více ACE (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mohou přistupovat k tomuto objektu. Pokud seznam DACL je prázdná (tj, obsahuje nulové ACE), žádný přístup se explicitně udělí oprávnění, takže implicitně byl odepřen přístup. Pokud popisovač zabezpečení objektu nemá seznam DACL, objekt je ale nechráněné a každý má úplný přístup.  
  
 K načtení objektu DACL, musí být vlastníka objektu nebo mít čtení_informací_o_řízení přístup k objektu. Chcete-li změnit objektu DACL, musí mít zápis_DAC přístup k objektu.  
  
 Používat metody třídy poskytuje vytvářet, přidat, odebrat a odstraňovat položky řízení přístupu z `CDacl` objektu. Viz také [AtlGetDacl](security-global-functions.md#atlgetdacl) a [AtlSetDacl](security-global-functions.md#atlsetdacl).  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="addallowedace"></a>  CDacl::AddAllowedAce  
 Přidá povolené prostředí ACE (položky řízení přístupu) `CDacl` objektu.  
  
```
bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 A [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.  
  
 `AccessMask`  
 Určuje masku přístupová práva, povolit pro danou `CSid` objektu.  
  
 `AceFlags`  
 Sada bitové příznaky, které řídí ACE dědičnosti.  
  
 `pObjectType`  
 Typ objektu.  
  
 `pInheritedObjectType`  
 Typ zděděné objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je položka řízení přístupu je přidán do `CDacl` objekt, **false** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 A `CDacl` objekt obsahuje nula nebo více ACE (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mohou přistupovat k tomuto objektu. Tato metoda přidá ACE položky, která umožňuje přístup k `CDacl` objektu.  
  
 V tématu [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) popis různé příznaky, které lze nastavit v `AceFlags` parametr.  
  
##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce  
 Přidá odepření ACE (položky řízení přístupu) `CDacl` objektu.  
  
```
bool AddDeniedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 A `CSid` objektu.  
  
 `AccessMask`  
 Určuje masku přístupová práva k odepřeny pro zadaný `CSid` objektu.  
  
 `AceFlags`  
 Sada bitové příznaky, které řídí ACE dědičnosti. Výchozí hodnota je 0 v první formulář metody.  
  
 `pObjectType`  
 Typ objektu.  
  
 `pInheritedObjectType`  
 Typ zděděné objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je položka řízení přístupu je přidán do `CDacl` objekt, **false** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 A `CDacl` objekt obsahuje nula nebo více ACE (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mohou přistupovat k tomuto objektu. Tato metoda přidá ACE, které zakazuje přístup `CDacl` objektu.  
  
 V tématu [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) popis různé příznaky, které lze nastavit v `AceFlags` parametr.  
  
##  <a name="cdacl"></a>  CDacl::CDacl  
 Konstruktor  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Existující **seznamu ACL** struktury (seznamu řízení přístupu).  
  
### <a name="remarks"></a>Poznámky  
 `CDacl` Objekt můžete volitelně vytvořit pomocí existující **seznamu ACL** struktura. Je důležité si uvědomit pouze DACL (seznam volitelného řízení přístupu), a ne SACL (seznam řízení přístupu systému), mají být předány jako tento parametr. V sestavení pro ladění předávání SACL způsobí, že vyhodnocení. V sestavení pro vydání předávání SACL způsobí, že položky řízení přístupu (položky řízení přístupu) v seznamu ACL, který se má ignorovat a dojde k žádné chybě.  
  
##  <a name="dtor"></a>  CDacl:: ~ CDacl  
 Destruktor.  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny prostředky získávají pomocí objektu, včetně všech ACE (položky řízení přístupu) pomocí destruktoru [CDacl::RemoveAllAces](#removeallaces).  
  
##  <a name="getacecount"></a>  CDacl::GetAceCount  
 Vrátí počet položek řízení přístupu (položky řízení přístupu) `CDacl` objektu.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet ACE, které jsou součástí `CDacl` objektu.  
  
##  <a name="operator_eq"></a>  CDacl::operator =  
 Operátor přiřazení.  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Seznam řízení přístupu (seznam řízení přístupu) přiřadit existující objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktualizaci `CDacl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, jenom předat DACL (seznam volitelného řízení přístupu) této funkce. Předávání SACL (seznam řízení přístupu systému) pro tuto funkci způsobí, že ASSERT v sestavení pro ladění ale způsobí, že žádná chyba v sestavení pro vydání.  
  
##  <a name="removeace"></a>  CDacl::RemoveAce  
 Odebere konkrétní ACE (položky řízení přístupu) `CDacl` objektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index ACE položku k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je odvozený od [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CDacl::RemoveAllAces  
 Odebere všechny položky řízení přístupu (položky řízení přístupu) součástí `CDacl` objektu.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny **ACE** struktury (položky řízení přístupu) (pokud existuje) v `CDacl` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [CAcl – třída](../../atl/reference/cacl-class.md)   
 [Seznamy ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
