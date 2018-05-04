---
title: Třída CPrivateObjectSecurityDesc | Microsoft Docs
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
ms.openlocfilehash: 6f47adc413a0e6d3d9c820b824dec95f55924867
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc – třída
Tato třída reprezentuje objekt popisovače zabezpečení soukromý objekt.  
  
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
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Volejte tuto metodu můžete převést popisovač zabezpečení a jeho seznamy řízení přístupu (ACL) do formátu, který podporuje automatické propagace položky zděditelné řízení přístupu (ACE).|  
|[CPrivateObjectSecurityDesc::Create](#create)|Voláním této metody lze přidělit a inicializace popisovače samorelativní zabezpečení pro privátní objekt vytvořený volání správce prostředků.|  
|[CPrivateObjectSecurityDesc::Get](#get)|Volejte tuto metodu za účelem načtení informací ze soukromý objekt popisovače zabezpečení.|  
|[CPrivateObjectSecurityDesc::Set](#set)|Voláním této metody lze upravit soukromý objekt popisovače zabezpečení.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída odvozená z [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), poskytuje metody pro vytváření a správu popisovač zabezpečení objektu privátní.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 Volejte tuto metodu můžete převést popisovač zabezpečení a jeho seznamy řízení přístupu (ACL) do formátu, který podporuje automatické propagace položky zděditelné řízení přístupu (ACE).  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Ukazatel na [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objekt odkazující na nadřazený kontejner objektu. Pokud není žádný nadřazený kontejner, tento parametr je NULL.  
  
 `ObjectType`  
 Ukazatel na **GUID** struktura, která určuje typ objektu, které jsou přidružené k aktuálnímu objektu. Nastavit `ObjectType` na hodnotu NULL, pokud objekt nemá identifikátor GUID.  
  
 `bIsDirectoryObject`  
 Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true označuje, že nový objekt je kontejner. Hodnota false znamená, že nový objekt není kontejner.  
  
 `GenericMapping`  
 Ukazatel na [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) struktura, která určuje mapování z každé obecná práva na konkrétní práva pro objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se pokusí zjistit, zda seznam ACE v volitelného řízení přístupu (DACL) a seznam řízení přístupu systému (SACL) aktuální popisovače zabezpečení měla zděděná z nadřazené popisovač zabezpečení. Zavolá [ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403) funkce.  
  
##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 Konstruktor  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `CPrivateObjectSecurityDesc` objektu.  
  
##  <a name="dtor"></a>  CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc  
 Destruktor.  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny přidělené prostředky a odstraní soukromý objekt popisovače zabezpečení.  
  
##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create  
 Voláním této metody lze přidělit a inicializace popisovače samorelativní zabezpečení pro privátní objekt vytvořený volání správce prostředků.  
  
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
 `pParent`  
 Ukazatel na [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objekt odkazující na nadřazený adresář, ve kterém se vytváří nový objekt. Nastavte na hodnotu NULL, pokud neexistuje žádný nadřazený adresář.  
  
 `pCreator`  
 Ukazatel na popisovač zabezpečení poskytované tvůrce objektu. Pokud tvůrce objektu explicitně nepředává informace o zabezpečení pro nový objekt, nastavte tento parametr na hodnotu NULL.  
  
 `bIsDirectoryObject`  
 Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true označuje, že nový objekt je kontejner. Hodnota false znamená, že nový objekt není kontejner.  
  
 `Token`  
 Odkaz na [CAccessToken](../../atl/reference/caccesstoken-class.md) objekt pro proces klienta, jehož jménem objekt vytvořen.  
  
 `GenericMapping`  
 Ukazatel na [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) struktura, která určuje mapování z každé obecná práva na konkrétní práva pro objekt.  
  
 `ObjectType`  
 Ukazatel na **GUID** struktura, která určuje typ objektu, které jsou přidružené k aktuálnímu objektu. Nastavit `ObjectType` na hodnotu NULL, pokud objekt nemá identifikátor GUID.  
  
 *bIsContainerObject*  
 Určuje, zda nový objekt může obsahovat jiné objekty. Hodnota true označuje, že nový objekt je kontejner. Hodnota false znamená, že nový objekt není kontejner.  
  
 `AutoInheritFlags`  
 Sadu bitové příznaky, které řídí dědění položek řízení přístupu (ACE) z `pParent`. V tématu [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405) nebo [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581).  
  
 Druhá metoda umožňuje určení typu objektu identifikátor GUID nového objektu nebo řízení dědění položky řízení přístupu.  
  
> [!NOTE]
>  Popisovač samorelativní zabezpečení je popisovač zabezpečení, která ukládá všechny jeho informace o zabezpečení v blok souvislé paměti.  
  
##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get  
 Volejte tuto metodu za účelem načtení informací ze soukromý objekt popisovače zabezpečení.  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 Sada bitové příznaky, které indikují části popisovače zabezpečení pro načtení. Tato hodnota může být kombinací [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bitové příznaky.  
  
 `pResult`  
 Ukazatel na [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objekt, který obdrží kopii požadované informace z Zadaný popisovač zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač zabezpečení je struktura a přidružená data, která obsahuje informace o zabezpečení pro zabezpečitelný objekt.  
  
##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =  
 Operátor přiřazení.  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CPrivateObjectSecurityDesc` Objekt, který chcete přiřadit k aktuálnímu objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CPrivateObjectSecurityDesc` objektu.  
  
##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set  
 Voláním této metody lze upravit soukromý objekt popisovače zabezpečení.  
  
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
 `si`  
 Sada bitové příznaky, které indikují části nastavit popisovač zabezpečení. Tato hodnota může být kombinací [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bitové příznaky.  
  
 *Úpravy*  
 Ukazatel na [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objektu. Uvedené části Tento popisovač zabezpečení `si` parametr se použijí pro popisovač zabezpečení objektu.  
  
 `GenericMapping`  
 Ukazatel na [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) struktura, která určuje mapování z každé obecná práva na konkrétní práva pro objekt.  
  
 `Token`  
 Odkaz na [CAccessToken](../../atl/reference/caccesstoken-class.md) objekt pro proces klienta, jehož jménem objekt vytvořen.  
  
 `AutoInheritFlags`  
 Sadu bitové příznaky, které řídí dědění položek řízení přístupu (ACE) z `pParent`. V tématu [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Druhá metoda umožňuje určení typu objektu GUID objektu nebo řízení dědění položky řízení přístupu.  
  
## <a name="see-also"></a>Viz také  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc – třída](../../atl/reference/csecuritydesc-class.md)
