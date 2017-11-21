---
title: "Třída CTokenGroups | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
dev_langs: C++
helpviewer_keywords: CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6c08f9105d51112f1261a79bd5b96341b5504f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctokengroups-class"></a>CTokenGroups – třída
Tato třída je obálka pro **TOKEN_GROUPS** struktury.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CTokenGroups
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor|  
|[CTokenGroups:: ~ CTokenGroups](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTokenGroups::Add](#add)|Přidá `CSid` nebo existující **TOKEN_GROUPS** struktury k `CTokenGroups` objektu.|  
|[CTokenGroups::Delete](#delete)|Odstraní `CSid` a jeho přidružených atributů z `CTokenGroups` objektu.|  
|[CTokenGroups::DeleteAll](#deleteall)|Odstraní všechna `CSid` objekty a jejich přidružených atributů z `CTokenGroups` objektu.|  
|[CTokenGroups::GetCount](#getcount)|Vrátí počet `CSid` objekty a přidružených atributů, které jsou součástí **CTokenGroups** objektu.|  
|[CTokenGroups::GetLength](#getlength)|Vrátí velikost `CTokenGroups` objektu.|  
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Načte ukazatel **TOKEN_GROUPS** struktury.|  
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Načte `CSid` objektů a atributů, které patří do `CTokenGroups` objektu.|  
|[CTokenGroups::LookupSid](#lookupsid)|Načte atributy přidružené `CSid` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Přetypování `CTokenGroups` objekt, který má ukazatel **TOKEN_GROUPS** struktury.|  
|[CTokenGroups::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 [Přístupový token](http://msdn.microsoft.com/library/windows/desktop/aa374909) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen všem uživatelům přihlášení systému Windows NT nebo Windows 2000.  
  
 **CTokenGroups** třída je obálka pro [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktura, která obsahuje informace o tokenu přístupu skupiny identifikátory zabezpečení (SID).  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="add"></a>CTokenGroups::Add  
 Přidá `CSid` nebo existující **TOKEN_GROUPS** struktury k `CTokenGroups` objektu.  
  
```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 A [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.  
  
 `dwAttributes`  
 Atributy, které se přidružit `CSid` objektu.  
  
 *rTokenGroups*  
 A [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tyto metody přidat jeden nebo víc `CSid` objekty a jejich atributy přidružené k `CTokenGroups` objektu.  
  
##  <a name="ctokengroups"></a>CTokenGroups::CTokenGroups  
 Konstruktor  
  
```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CTokenGroups` Objekt nebo [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktura, pomocí kterého můžete vytvořit `CTokenGroups` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CTokenGroups` Můžete volitelně vytvořit objekt pomocí **TOKEN_GROUPS** struktura nebo dříve definovaném `CTokenGroups` objektu.  
  
##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups  
 Destruktor.  
  
```
virtual ~CTokenGroups() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny přidělené prostředky.  
  
##  <a name="delete"></a>CTokenGroups::Delete  
 Odstraní `CSid` a jeho přidružených atributů z `CTokenGroups` objektu.  
  
```
bool Delete(const CSid& rSid) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekt, pro který měla by být odebrána identifikátor zabezpečení (SID) a atributy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud `CSid` je odebrán, false jinak.  
  
##  <a name="deleteall"></a>CTokenGroups::DeleteAll  
 Odstraní všechna `CSid` objekty a jejich přidružených atributů z `CTokenGroups` objektu.  
  
```
void DeleteAll() throw();
```  
  
##  <a name="getcount"></a>CTokenGroups::GetCount  
 Vrátí počet `CSid` objekty obsažené v `CTokenGroups`.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty a jejich přidruženými atributy, které jsou součástí `CTokenGroups` objektu.  
  
##  <a name="getlength"></a>CTokenGroups::GetLength  
 Vrátí velikost **CTokenGroup** objektu.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí celková velikost **CTokenGroup** objektu v bajtech.  
  
##  <a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS  
 Načte ukazatel **TOKEN_GROUPS** struktury.  
  
```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte ukazatel [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktura patřící do `CTokenGroups` objektu tokenu přístupu.  
  
##  <a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes  
 Načte `CSid` objekty a (volitelně) atributy, které patří do `CTokenGroups` objektu.  
  
```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSids`  
 Ukazatele na pole [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty.  
  
 `pAttributes`  
 Ukazatel na pole typu DWORD. Pokud tento parametr vynechán nebo má hodnotu NULL, nejsou načíst atributy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří výčet všech `CSid` objekty obsažené v `CTokenGroups` objektu a umístit je a (volitelně) atribut příznaky do pole objektů.  
  
##  <a name="lookupsid"></a>CTokenGroups::LookupSid  
 Načte atributy přidružené `CSid` objektu.  
  
```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.  
  
 `pdwAttributes`  
 Ukazatel na DWORD, která bude přijímat `CSid` atribut objektu. Pokud není zadán nebo hodnotu NULL, nebudou načteny atribut.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud `CSid` je nalezena, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Nastavení `pdwAttributes` na hodnotu NULL zajištěný potvrzení existenci `CSid` bez přístupu k atributu. Poznamenat, že tato metoda by neměl použít ke kontrole přístupová práva jako v systému Windows 2000 může dojít k nesprávné výsledkům. Aplikace by měly používat místo toho [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) metoda.  
  
##  <a name="operator_eq"></a>CTokenGroups::operator =  
 Operátor přiřazení.  
  
```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CTokenGroups` Objekt nebo [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktura přiřadit `CTokenGroups` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CTokenGroups` objektu.  
  
##  <a name="operator_const_token_groups__star"></a>CTokenGroups::operator const TOKEN_GROUPS *  
 Vrhá hodnotu na ukazatel **TOKEN_GROUPS** struktury.  
  
```  
operator const TOKEN_GROUPS *() const throw(...);
```  
  
### <a name="remarks"></a>Poznámky  
 Vrhá hodnotu na ukazatel [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktury.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [Identifikační číslo volané stanice – třída](../../atl/reference/csid-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
