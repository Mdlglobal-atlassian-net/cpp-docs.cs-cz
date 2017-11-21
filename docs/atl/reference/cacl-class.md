---
title: "Třída CAcl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
dev_langs: C++
helpviewer_keywords: CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b49d7bf064d65e9a160311d23b304745f4d1b04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cacl-class"></a>CAcl – třída
Tato třída je obálka pro `ACL` struktury (seznamu řízení přístupu).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAcl
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Pole `ACCESS_MASK`s.|  
|[CAcl::CAceFlagArray](#caceflagarray)|Pole `BYTE`s.|  
|[CAcl::CAceTypeArray](#cacetypearray)|Pole `BYTE`s.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAcl::CAcl](#cacl)|Konstruktor|  
|[CAcl:: ~ CAcl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAcl::GetAceCount](#getacecount)|Vrátí počet řízení přístupu položka (ACE) objekty.|  
|[CAcl::GetAclEntries](#getaclentries)|Získá ze seznamu ACL položky řízení přístupu `CAcl` objektu.|  
|[CAcl::GetAclEntry](#getaclentry)|Načte všechny informace o položce v `CAcl` objektu.|  
|[CAcl::GetLength](#getlength)|Vrátí délku seznamu řízení přístupu.|  
|[CAcl::GetPACL](#getpacl)|Vrátí PACL (ukazatel na ACL).|  
|[CAcl::IsEmpty](#isempty)|Testy `CAcl` objekt pro položky.|  
|[CAcl::IsNull](#isnull)|Vrátí stav `CAcl` objektu.|  
|[CAcl::RemoveAce](#removeace)|Odebere konkrétní ACE (položky řízení přístupu) `CAcl` objektu.|  
|[CAcl::RemoveAces](#removeaces)|Odebere všechny položky řízení přístupu (položky řízení přístupu) `CAcl` které se týkají danou `CSid`.|  
|[CAcl::SetEmpty](#setempty)|Značky `CAcl` objekt jako prázdný.|  
|[CAcl::SetNull](#setnull)|Značky `CAcl` objekt jako `NULL`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAcl::operator const ACL *](#operator_const_acl__star)|Přetypování `CAcl` do objektu `ACL` struktura.|  
|[CAcl::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 **Seznamu ACL** struktura je záhlaví ACL (seznam řízení přístupu). Seznam ACL zahrnuje sekvenční seznam nula nebo více [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868) (položky řízení přístupu). Jednotlivé položky řízení přístupu v seznamu ACL jsou číslována od 0 do *n-1*, kde  *n*  je počet ACE v seznamu ACL. Při úpravě ACL, aplikace se odkazuje na položku řízení přístupu (ACE) v rámci seznamu řízení přístupu podle jeho indexu.  
  
 Existují dva typy seznamu řízení přístupu:  
  
-   Volitelné  
  
-   Systém  
  
 Volitelný seznam řízení přístupu řídí vlastník objektu nebo každý, kdo udělena **zápis_DAC** přístup k objektu. Určuje, že může mít přístup konkrétní uživatele a skupiny do objektu. Vlastník souboru můžete například použít volitelný seznam řízení přístupu k řízení, kteří uživatelé a skupiny můžete a nemůže mít přístup k souboru.  
  
 Objekt může mít také informace o zabezpečení na úrovni systému spojené s, v podobě systému ACL řídí správce systému. Systém seznamu ACL můžete povolit na správce systému a auditovat pokusy o získání přístupu k objektu.  
  
 Další podrobnosti najdete v tématu [seznamu ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872) diskuse ve Windows SDK.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="caccessmaskarray"></a>CAcl::CAccessMaskArray  
 Pole objektů ACCESS_MASK.  
  
```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato typedef Určuje typ pole, která slouží k uložení přístupová práva použít v položek řízení přístupu (ACE).  
  
##  <a name="caceflagarray"></a>CAcl::CAceFlagArray  
 Pole bajtů.  
  
```
typedef CAtlArray<BYTE> CAceFlagArray;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato typedef Určuje typ pole používá k definování příznaky specifické pro typ ovládacího prvku položku řízení řízení přístupu. Najdete v článku [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) definice úplný seznam možných příznaky.  
  
##  <a name="cacetypearray"></a>CAcl::CAceTypeArray  
 Pole bajtů.  
  
```
typedef CAtlArray<BYTE> CAceTypeArray;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato typedef Určuje typ pole používá k definování povaha řízení přístupu (ACE) položka objekty, například ACCESS_ALLOWED_ACE_TYPE nebo ACCESS_DENIED_ACE_TYPE. Najdete v článku [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) definice úplný seznam možných typů.  
  
##  <a name="cacl"></a>CAcl::CAcl  
 Konstruktor  
  
```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Existující objekt `CAcl`.  
  
### <a name="remarks"></a>Poznámky  
 `CAcl` Objekt můžete volitelně vytvořit pomocí existující `CAcl` objektu.  
  
##  <a name="dtor"></a>CAcl:: ~ CAcl  
 Destruktor.  
  
```
virtual ~CAcl() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny prostředky získali objektem.  
  
##  <a name="getacecount"></a>CAcl::GetAceCount  
 Vrátí počet řízení přístupu položka (ACE) objekty.  
  
```
virtual UINT GetAceCount() const throw() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet položek ACE v `CAcl` objektu.  
  
##  <a name="getaclentries"></a>CAcl::GetAclEntries  
 Získá ze seznamu ACL položky řízení přístupu `CAcl` objektu.  
  
```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSids`  
 Ukazatel na pole [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty.  
  
 *pAccessMasks*  
 Masky přístupu.  
  
 *pAceTypes*  
 Položku řízení přístupu ( **ACE**) typy.  
  
 *pAceFlags*  
 **ACE** příznaky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda doplní parametry pole s detaily o každé **ACE** objektů obsažených v `CAcl` objektu. Pokud nejsou požadované podrobnosti o této konkrétní pole, použijte hodnotu NULL.  
  
 Obsah každého pole odpovídají mezi sebou, který je první prvek `CAccessMaskArray` pole odpovídá prvním elementem v `CSidArray` pole a tak dále.  
  
 V tématu [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) další podrobnosti o ACE typy a značky.  
  
##  <a name="getaclentry"></a>CAcl::GetAclEntry  
 Načte všechny informace o položku v seznamu řízení přístupu (ACL).  
  
```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index k položce seznamu ACL pro načtení.  
  
 `pSid`  
 [Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu, pro kterou platí položce seznamu ACL.  
  
 *pMask*  
 Maska určující oprávnění udělit nebo odepřít přístup.  
  
 `pType`  
 Typ položky řízení přístupu.  
  
 `pFlags`  
 Příznaky ACE.  
  
 `pObjectType`  
 Typ objektu. Nastaví ho k GUID_NULL Pokud v této položky řízení přístupu není zadán typ objektu, nebo pokud je položka řízení přístupu není ACE objektu.  
  
 `pInheritedObjectType`  
 Typ zděděné objektu. Nastaví ho k GUID_NULL Pokud typ zděděné objektu není zadané v této položky řízení přístupu, nebo pokud je položka řízení přístupu není ACE objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte všechny informace o jednotlivých ACE, že poskytuje další informace než [CAcl::GetAclEntries](#getaclentries) samostatně zpřístupní.  
  
 V tématu [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) další podrobnosti o ACE typy a značky.  
  
##  <a name="getlength"></a>CAcl::GetLength  
 Vrátí délku seznamu řízení přístupu (ACL).  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí má požadovanou délku v bajtech potřeba k umístění **seznamu ACL** struktura.  
  
##  <a name="getpacl"></a>CAcl::GetPACL  
 Vrátí ukazatel na seznam řízení přístupu (ACL).  
  
```
const ACL* GetPACL() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel **seznamu ACL** struktura.  
  
##  <a name="isempty"></a>CAcl::IsEmpty  
 Testy `CAcl` objekt pro položky.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí **true** Pokud `CAcl` objekt nemá hodnotu NULL a neobsahuje žádné položky. Vrátí **false** Pokud `CAcl` objekt má hodnotu NULL nebo obsahuje minimálně jeden záznam.  
  
##  <a name="isnull"></a>CAcl::IsNull  
 Vrátí stav `CAcl` objektu.  
  
```
bool IsNull() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud `CAcl` objekt má hodnotu NULL, **false** jinak.  
  
##  <a name="operator_const_acl__star"></a>CAcl::operator const ACL *  
 Přetypování `CAcl` do objektu **seznamu ACL** struktury (seznamu řízení přístupu).  
  
```  
operator const ACL *() const throw(...);
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí adresu **seznamu ACL** struktura.  
  
##  <a name="operator_eq"></a>CAcl::operator =  
 Operátor přiřazení.  
  
```
CAcl& operator= (const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CAcl` Přiřadit existující objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktualizaci `CAcl` objektu.  
  
##  <a name="removeace"></a>CAcl::RemoveAce  
 Odebere konkrétní ACE (položky řízení přístupu) **CAcl** objektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index ACE položku k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je odvozený od [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeaces"></a>CAcl::RemoveAces  
 Odebere alls ACE (položky řízení přístupu) `CAcl` které se týkají danou `CSid`.  
  
```
bool RemoveAces(const CSid& rSid) throw(...)
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 Odkaz na `CSid` objektu.  
  
##  <a name="setempty"></a>CAcl::SetEmpty  
 Značky `CAcl` objekt jako prázdný.  
  
```
void SetEmpty() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 `CAcl` Lze nastavit na prázdný nebo na hodnotu NULL: dva stavy jsou jedinečné.  
  
##  <a name="setnull"></a>CAcl::SetNull  
 Značky `CAcl` objektu jako hodnotu NULL.  
  
```
void SetNull() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 `CAcl` Lze nastavit na prázdný nebo na hodnotu NULL: dva stavy jsou jedinečné.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
