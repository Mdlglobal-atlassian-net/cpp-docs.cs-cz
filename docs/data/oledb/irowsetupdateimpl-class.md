---
title: IRowsetUpdateImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afbf8b42b4d518412c1004d78c5c718e54078c1c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340778"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl – třída
Šablony technologie OLE DB provádění [IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Třída odvozená z `IRowsetUpdateImpl`.  
  
 *Úložiště*  
 Záznam uživatele.  
  
 *UpdateArray*  
 Pole obsahující data uložená v mezipaměti pro aktualizaci v sadě řádků.  
  
 *RowClass*  
 Jednotka pro ukládání `HROW`.  
  
 *MapClass*  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)  
  
|||  
|-|-|  
|[SetData](#setdata)|Nastaví hodnoty dat v jedné nebo více sloupců.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Metody rozhraní (používá se s IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](#getoriginaldata)|Získá data naposledy předány nebo získané ze zdroje dat, ignoruje se čekající změny.|  
|[Getpendingrows –](#getpendingrows)|Vrátí seznam hodnot řádků s čekajícími změnami.|  
|[GetRowStatus –](#getrowstatus)|Vrátí stav zadaných řádků.|  
|[Vrácení zpět](#undo)|Zruší všechny změny řádku od posledního načtení nebo aktualizace.|  
|[Aktualizace](#update)|Odesílá všechny změny provedené od posledního načtení nebo aktualizace řádku.|  
  
### <a name="implementation-methods-callback"></a>Implementace metody (zpětného volání)  
  
|||  
|-|-|  
|[IsUpdateAllowed –](#isupdateallowed)|Používá se ke kontrole integrity, zabezpečení a tak dále předtím, než aktualizace.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_mapCachedData](#mapcacheddata)|Obsahuje původní data pro odložené operaci.|  
  
## <a name="remarks"></a>Poznámky  
 Nejprve byste si a porozuměli jim v dokumentaci k [IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx), protože všechno, co je popsáno zde platí i zde. Doporučujeme přečíst kapitola 6 *OLE DB referenční informace pro programátory* o nastavení data.  
  
 `IRowsetUpdateImpl` implementuje rozhraní OLE DB `IRowsetUpdate` rozhraní, která umožňuje uživatelům zpoždění přenosu změn provedených s `IRowsetChange` do zdroje dat a vrátit zpět změny před samotným přenosem.  
  
> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si přečetli následující dokumentace před pokusem o implementaci poskytovatele:  
  
-   [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Kapitola 6 *odkaz programátora technologie OLE DB*  
  
-   Také naleznete v tématu Jak `RUpdateRowset` třída se používá v ukázce UpdatePV  

## <a name="setdata"></a> IRowsetUpdateImpl::SetData
Nastaví hodnoty dat v jedné nebo více sloupců.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowsetChange::SetData](https://msdn.microsoft.com/library/ms721232.aspx) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Přepíše tuto metodu [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) metoda ale zahrnuje ukládání do mezipaměti původní data tak, aby povolovala okamžité nebo odložené zpracování operace.

## <a name="getoriginaldata"></a> IRowsetUpdateImpl::GetOriginalData
Získá data naposledy předány nebo získané ze zdroje dat, ignoruje se čekající změny.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/library/ms709947.aspx) v *referenční informace pro OLE DB programátory*.   

## <a name="getpendingrows"></a> IRowsetUpdateImpl::GetPendingRows
Vrátí seznam hodnot řádků s čekajícími změnami.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hReserved*  
 [in] Odpovídá *hChapter* parametr [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx).  
  
 Další parametry, naleznete v tématu [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx) v *OLE DB referenční informace pro programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx) v *OLE DB referenční informace pro programátory*.  

## <a name="getrowstatus"></a> IRowsetUpdateImpl::GetRowStatus
Vrátí stav zadaných řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hReserved*  
 [in] Odpovídá *hChapter* parametr [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/library/ms724377.aspx).  
  
 Další parametry, naleznete v tématu [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/library/ms724377.aspx) v *OLE DB referenční informace pro programátory*.  

## <a name="undo"></a> IRowsetUpdateImpl::Undo
Zruší všechny změny řádku od posledního načtení nebo aktualizace.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hReserved*  
 [in] Odpovídá *hChapter* parametr [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx).  
  
 *pcRowsUndone*  
 [out] Odpovídá *pcRows* parametr [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx).  
  
 *prgRowsUndone*  
 [in] Odpovídá *prgRows* parametr [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx).  
  
 Další parametry, naleznete v tématu [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx) v *OLE DB referenční informace pro programátory*. 

## <a name="update"></a> IRowsetUpdateImpl::Update
Odesílá všechny změny provedené od posledního načtení nebo aktualizace řádku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hReserved*  
 [in] Odpovídá *hChapter* parametr [IRowsetUpdate::Update](https://msdn.microsoft.com/library/ms719709.aspx).  
  
 Další parametry, naleznete v tématu [IRowsetUpdate::Update](https://msdn.microsoft.com/library/ms719709.aspx) v *OLE DB referenční informace pro programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Změny se přenáší pomocí volání [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Spotřebitel musí volat [CRowset::Update](../../data/oledb/crowset-update.md) se změny projevily. Nastavte *prgRowstatus* na odpovídající hodnotu jak je popsáno v [stavy řádků](https://msdn.microsoft.com/library/ms722752.aspx) v *OLE DB referenční informace pro programátory*. 
  
## <a name="isupdateallowed"></a> IRowsetUpdateImpl::IsUpdateAllowed
Potlačí tuto metodu ke kontrole integrity a tak dále před aktualizací zabezpečení.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Stav*  
 [in] Stav čekající operace na řádky.  
  
 *hRowUpdate*  
 [in] Popisovač pro řádky, které chce uživatel aktualizovat.  
  
 *pRowStatus*  
 [out] Vrátí stav pro uživatele.  
  
### <a name="remarks"></a>Poznámky  
 Pokud zjistíte, že má být povolený aktualizace, vrátí hodnotu S_OK; v opačném případě vrátí E_FAIL. Pokud povolíte aktualizaci, musíte také nastavit `DBROWSTATUS` v [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) na odpovídající [řádek stavu](https://msdn.microsoft.com/library/ms722752.aspx).  

## <a name="mapcacheddata"></a> IRowsetUpdateImpl::m_mapCachedData
Mapa obsahuje původní data pro odložené operaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>Parametry  
 *hRow*  
 Popisovač řádků pro data.  
  
 *pData*  
 Ukazatel na data ukládat do mezipaměti. Data jsou typu *úložiště* (třída uživatelského záznamu). Zobrazit *úložiště* argumentem šablony [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md).  

## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)