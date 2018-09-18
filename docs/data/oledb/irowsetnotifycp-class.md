---
title: IRowsetNotifyCP – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 15e00f27c5ad5d5312928bda8f73304a8417a6bc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071819"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP – třída

Implementuje poskytovatele lokality pro bod připojení rozhraní [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\)).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray>,  
   public ReentrantEventSync  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Třída odvozená z `IRowsetNotifyCP`.  
  
*ReentrantEventSync*<br/>
Mutex – třída, která podporuje vícenásobného přístupu (výchozí hodnota je `CComSharedMutex`). Objekt mutex je synchronizační objekt umožňující jeden vlákno vzájemně exkluzivní přístup k prostředku.  
  
*piid*<br/>
Ukazatel rozhraní s ID (`IID*`) pro `IRowsetNotify` rozhraní bodu připojení. Výchozí hodnota je `&__uuidof(IRowsetNotify)`.  
  
*DynamicUnkArray*<br/>
Pole typu [ccomdynamicunkarray –](../../atl/reference/ccomdynamicunkarray-class.md), která je dynamicky přiřazeného pole `IUnknown` ukazatele na klienta jímka rozhraní. 

## <a name="requirements"></a>Požadavky  

**Záhlaví:** atldb.h   
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Fire_OnFieldChange](#onfieldchange)|Upozorní příjemce ke změně hodnoty sloupce.|  
|[Fire_OnRowChange](#onrowchange)|Upozornění uživatelů na změnu by to ovlivnilo řádky.|  
|[Fire_OnRowsetChange](#onrowsetchange)|Upozorní příjemce změny, které mají vliv celá sada řádků.|  
  
## <a name="remarks"></a>Poznámky  

`IRowsetNotifyCP` implementuje vysílání funkce radit naslouchacích procesů najdete v bodě připojení `IID_IRowsetNotify` změny obsahu v sadě řádků.  
  
Všimněte si, že musí také implementovat a zaregistrovat `IRowsetNotify` na spotřebitele (označované také jako "jímka") pomocí [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) tak, aby příjemce může zpracovat oznámení. Zobrazit [příjem oznámení](../../data/oledb/receiving-notifications.md) o implementaci rozhraní bod připojení pro příjemce.  
  
Podrobné informace o implementaci oznámení, naleznete v části "Podpora oznámení" v [vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md).  

## <a name="onfieldchange"></a> IRowsetNotifyCP::Fire_OnFieldChange

Vysílá [onfieldchange –](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) událost oznámení příjemci změnu hodnoty sloupce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,  
   HROW hRow,  
   DBORDINAL cColumns,  
   DBORDINAL* rgColumns,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) v *referenční informace pro OLE DB programátory*. 

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange

Vysílá [onrowchange –](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) události pro všechny posluchače v bodě připojení `IID_IRowsetNotify` oznámit příjemci změny ovlivňující řádky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange

Vysílá [onrowsetchange –](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) události pro všechny posluchače v bodě připojení `IID_IRowsetNotify` oznámit příjemci změny, které mají vliv celá sada řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Oznámení (COM)](/windows/desktop/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)