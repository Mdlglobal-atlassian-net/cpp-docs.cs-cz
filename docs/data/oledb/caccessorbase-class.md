---
title: CAccessorBase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18199a700cbc5065d987a57cc076a5d0cf670577
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340661"
---
# <a name="caccessorbase-class"></a>CAccessorBase – třída
Všechny přistupující objekty v šablonách technologie OLE DB odvozovat z této třídy. `CAccessorBase` Umožňuje spravovat několik přístupových objektů jedné sady řádků. Také poskytuje vazby pro parametry a výstupní sloupce.  
  
## <a name="syntax"></a>Syntaxe

```cpp
// Replace with syntax  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zavřít](#close)|Zavře přístupové objekty.|  
|[Gethaccessor –](#geth)|Načte popisovač přistupujícího objektu.|  
|[Getnumaccessors –](#getnum)|Získá počet přistupující objekty vytvořené třídy.|  
|[Isautoaccessor –](#isauto)|Ověřuje, zda je zadaný přistupující objekt automaticky přistupující objekt.|  
|[Releaseaccessors –](#release)|Uvolní přístupové objekty.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  

## <a name="close"></a> CAccessorBase::Close
Zavře přístupové objekty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void Close();  
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné volat [releaseaccessors –](../../data/oledb/caccessorbase-releaseaccessors.md) první.  

## <a name="geth"></a> CAccessorBase::GetHAccessor
Načte popisovač přistupujícího objektu zadaného přístupového objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 *nAccessor*  
 [in] Číslo nula posun pro přistupující objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač přistupujícího objektu.  

## <a name="getnum"></a> CAccessorBase::GetNumAccessors
Získá počet přistupující objekty vytvořené třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
ULONG GetNumAccessors() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet přistupující objekty vytvořené třídy.  

## <a name="isauto"></a> CAccessorBase::IsAutoAccessor
Vrátí true, pokud je během operace přesunu automaticky načíst data pro přistupující objekt.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
bool IsAutoAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 *nAccessor*  
 [in] Číslo nula posun pro přistupující objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je přistupující objekt automaticky přistupující objekt. V opačném případě vrátí **false**.  

## <a name="release"></a> CAccessorBase::ReleaseAccessors
Uvolní přistupující objekty vytvořené třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Ukazatel `IUnknown` rozhraní pro objekt modelu COM, pro kterou byly vytvořeny přístupové objekty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Volá se z [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md). 
  
## <a name="see-also"></a>Viz také  
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Reference šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessorBase – třída](../../data/oledb/caccessorbase-class.md)