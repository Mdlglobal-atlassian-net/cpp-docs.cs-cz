---
title: IRowsetImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
dev_langs:
- C++
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: faf782f4386cf2b2640ed65f3a2b24bbf4c5d693
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465961"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl – třída
Poskytuje implementaci `IRowset` rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*>>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IRowsetImpl`.  
  
 *RowsetInterface*  
 Třída odvozená z `IRowsetImpl`.  
  
 *RowClass*  
 Jednotka pro ukládání `HROW`.  
  
 *MapClass*  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrows –](#addrefrows)|Přidá počet odkazů na existující popisovač řádku.|  
|[Createrow –](#createrow)|Volané [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) přidělit nový `HROW`. Nebyla volána přímo uživatelem.|  
|[GetData](#getdata)|Načte data z dané sadě řádků kopii řádku.|  
|[GetDBStatus](#getdbstatus)|Vrátí stav pro zadané pole.|  
|[GetNextRows](#getnextrows)|Načte řádky postupně, pamatovat předchozí pozici.|  
|[IRowsetImpl –](#irowsetimpl)|Konstruktor Nebyla volána přímo uživatelem.|  
|[Refrows –](#refrows)|Volané [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a [releaserows –](../../data/oledb/irowsetimpl-releaserows.md). Nebyla volána přímo uživatelem.|  
|[Releaserows –](#releaserows)|Verze řádků.|  
|[Volání metody RestartPosition](#restartposition)|Přemístí pozici na počáteční pozici; To znamená vytvořit svůj postoj při první sadu řádků.|  
|[SetDBStatus](#setdbstatus)|Nastaví stav příznaky pro zadané pole.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bCanFetchBack](#bcanfetchback)|Označuje, zda poskytovatel podporuje načítání zpětně.|  
|[m_bCanScrollBack](#bcanscrollback)|Označuje, zda zprostředkovatel může mít jeho posunout kurzor zpětně.|  
|[m_bReset](#breset)|Určuje, zda zprostředkovatele má resetovat pozici kurzoru. To má zvláštní význam při posouvání zpětně nebo načítání zpětně v [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m_iRowset](#irowset)|Index tak, aby v sadě řádků reprezentující kurzor.|  
|[m_rgRowHandles](#rgrowhandles)|Seznam popisovačů řádků.|  
  
## <a name="remarks"></a>Poznámky  
 [IRowset](/previous-versions/windows/desktop/ms720986\(v=vs.85\)) je rozhraní pro základní sadu řádků.  

## <a name="addrefrows"></a> IRowsetImpl::AddRefRows
Přidá počet odkazů na existující popisovač řádku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  

## <a name="createrow"></a> IRowsetImpl::CreateRow
Pomocná metoda volána [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) přidělit nový `HROW`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows);  
```  
  
#### <a name="parameters"></a>Parametry  
 *lRowsOffset*  
 Pozice kurzoru řádku, který vytváří.  
  
 *cRowsObtained*  
 Odkaz se předá zpět do uživatele udávající počet řádků, které vytvořili.  
  
 *rgRows*  
 Pole `HROW`s vrátit zpět volajícímu s úchyty pro nově vytvořený řádku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud řádek existuje, tato metoda volá [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a vrátí. V opačném případě přidělí novou instanci třídy proměnnou šablony RowClass a přidá jej do [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## <a name="getdata"></a> IRowsetImpl::GetData
Načte data z dané sadě řádků kopii řádku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowset::GetData](/previous-versions/windows/desktop/ms716988\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
 Některé parametry odpovídají *OLE DB referenční informace pro programátory* parametry jiné názvy, které jsou popsány v `IRowset::GetData`:  
  
|Parametry šablony technologie OLE DB|*OLE DB referenční informace pro programátory* parametry|  
|--------------------------------|------------------------------------------------|  
|*pDstData*|*pData*|  
  
### <a name="remarks"></a>Poznámky  
 Převod dat pomocí převodu dat OLE DB knihovny DLL také zpracovává. 

## <a name="getdbstatus"></a> IRowsetImpl::GetDBStatus
Vrátí stav DBSTATUS příznaky pro zadané pole.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] *vlastnosti CurrentRow platné*  
 Na aktuálním řádku.  
  
 [in] *názvy sloupců*  
 Sloupec, pro který je požadovaný stav.  
  
### <a name="return-value"></a>Návratová hodnota  
 [DBSTATUS](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) příznaky pro sloupec. 

## <a name="getnextrows"></a> IRowsetImpl::GetNextRows
Načte řádky postupně, pamatovat předchozí pozici.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowset::GetNextRows](/previous-versions/windows/desktop/ms709827\(v=vs.85\)) v *referenční informace pro OLE DB programátory*. 

## <a name="irowsetimpl"></a> IRowsetImpl::IRowsetImpl
Konstruktor  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
IRowsetImpl();  
```  
  
### <a name="remarks"></a>Poznámky  
 Obvykle není nutné tuto metodu volat přímo.  

## <a name="refrows"></a> IRowsetImpl::RefRows
Volané [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a [releaserows –](../../data/oledb/irowsetimpl-releaserows.md) buď zvýšit nebo vydání počet odkazů na existující popisovač řádku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RefRows(DBCOUNTITEM cRows,  
   const HROWrghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  

## <a name="releaserows"></a> IRowsetImpl::ReleaseRows
Verze řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWOPTIONS rgRowOptions[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowset::ReleaseRows](/previous-versions/windows/desktop/ms719771\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  

## <a name="restartposition"></a> IRowsetImpl::RestartPosition
Přemístí pozici na počáteční pozici; To znamená vytvořit svůj postoj při první sadu řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowset::RestartPosition](/previous-versions/windows/desktop/ms712877\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Umístění sady řádků nedefinovaný až do `GetNextRow` je volána. Můžete přesunout zpět v rowet voláním `RestartPosition` a načítání nebo posouvání zpětně.  

## <a name="setdbstatus"></a> IRowsetImpl::SetDBStatus
Nastaví příznaky DBSTATUS stavu pro zadané pole.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 *statusFlags*  
 [DBSTATUS](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) příznaky nastavit pro sloupec.  
  
 *vlastnosti CurrentRow platné*  
 Na aktuálním řádku.  
  
 *Vlastnost columnInfo*  
 Sloupec, pro který je nastaven stav.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Zprostředkovatel přepsání této funkce můžete zadat speciální zpracování pro DBSTATUS_S_ISNULL a DBSTATUS_S_DEFAULT. 

## <a name="bcanfetchback"></a> IRowsetImpl::m_bCanFetchBack
Označuje, zda poskytovatel podporuje načítání zpětně.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bCanFetchBack:1;  
```  
  
### <a name="remarks"></a>Poznámky  
 Propojené na `DBPROP_CANFETCHBACKWARDS` vlastnost `DBPROPSET_ROWSET` skupiny. Zprostředkovatel musí podporovat `DBPROP_CANFETCHBACKWARDS` pro `m_bCanFetchBackwards` bude **true**.  

## <a name="bcanscrollback"></a> IRowsetImpl::m_bCanScrollBack
Označuje, zda zprostředkovatel může mít jeho posunout kurzor zpětně.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned  m_bCanScrollBack:1;  
```  
  
### <a name="remarks"></a>Poznámky  
 Propojené na `DBPROP_CANSCROLLBACKWARDS` vlastnost `DBPROPSET_ROWSET` skupiny. Zprostředkovatel musí podporovat `DBPROP_CANSCROLLBACKWARDS` pro `m_bCanFetchBackwards` bude **true**. 

## <a name="breset"></a> IRowsetImpl::m_bReset
Bitový příznak, který umožňuje určit, pokud pozice kurzoru je definována v sadě řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bReset:1;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud příjemce volá [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) s záporné `lOffset` nebo *cRows* a `m_bReset` má hodnotu true, `GetNextRows` přesune na konec objektu sady řádků. Pokud `m_bReset` má hodnotu false, uživatel obdrží chybový kód, v souladu se specifikací OLE DB. `m_bReset` Získá příznak nastaven na **true** při prvním vytvoření v sadě řádků a když se zavolá příjemce [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Získá hodnotu **false** při volání `GetNextRows`. 

## <a name="irowset"></a> IRowsetImpl::m_iRowset
Index tak, aby v sadě řádků reprezentující kurzor.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
DBROWOFFSET m_iRowset;  
```  

## <a name="rgrowhandles"></a> IRowsetImpl::m_rgRowHandles
Mapy popisovačů řádků, které jsou aktuálně obsaženy poskytovatelem v reakci na `GetNextRows`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
MapClass m_rgRowHandles;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisovačů řádků se odeberou voláním `ReleaseRows`. Zobrazit [IRowsetImpl – přehled](../../data/oledb/irowsetimpl-class.md) pro definici *MapClass*.  

## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)    
 [CSimpleRow – třída](../../data/oledb/csimplerow-class.md)