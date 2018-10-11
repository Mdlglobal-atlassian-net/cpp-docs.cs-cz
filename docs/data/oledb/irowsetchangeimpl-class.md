---
title: IRowsetChangeImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0ee351771d56b417396583ef41a96c62ff6bafd
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082524"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl – třída

Šablony technologie OLE DB provádění [IRowsetChange](/previous-versions/windows/desktop/ms715790) rozhraní ve specifikaci OLE DB.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Třída odvozená z `IRowsetChangeImpl`.  
  
*Úložiště*<br/>
Záznam uživatele.  
  
*BaseInterface*<br/>
Základní třídu pro rozhraní, jako například `IRowsetChange`.  
  
*RowClass*<br/>
Jednotky úložiště pro popisovač řádku.  
  
*MapClass*<br/>
Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](#deleterows)|Odstraní řádky ze sady řádků.|  
|[Insertrow –](#insertrow)|Vloží řádek do sady řádků.|  
|[SetData](#setdata)|Nastaví hodnoty dat v jedné nebo více sloupců.|  
  
### <a name="implementation-method-callback"></a>Implementace metody (zpětného volání)  
  
|||  
|-|-|  
|[FlushData](#flushdata)|Overidden poskytovatelem se zapsat data do svého úložiště.|  
  
## <a name="remarks"></a>Poznámky  

Toto rozhraní je zodpovědná za operace okamžitou zápisu do úložiště dat. "Ihned možných" znamená, že pokud koncový uživatel (uživatel příjemce) odešle všechny změny, tyto změny se okamžitě přenáší data uložit (a není možné vrátit zpět).  
  
`IRowsetChangeImpl` implementuje rozhraní OLE DB `IRowsetChange` rozhraní, která umožňuje aktualizaci hodnot sloupce v existující řádky, odstranění řádků a vložením nových řádků.  
  
Šablony technologie OLE DB implementace podporuje všechny základní metody (`SetData`, `InsertRow`, a `DeleteRows`).  
  
> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si přečetli následující dokumentace před pokusem o implementaci poskytovatele:  
  
- [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)  
  
- Kapitola 6 *odkaz programátora technologie OLE DB*  
  
- Také naleznete v tématu Jak `RUpdateRowset` třída se používá [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku.  
  
## <a name="deleterows"></a> IRowsetChangeImpl::DeleteRows

Odstraní řádky ze sady řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v%3dvs.85)) v *referenční informace pro OLE DB programátory*. 

## <a name="insertrow"></a> IRowsetChangeImpl::InsertRow

Vytvoří a inicializuje nový řádek v dané sadě řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921) v *referenční informace pro OLE DB programátory*. 

## <a name="setdata"></a> IRowsetChangeImpl::SetData

Nastaví hodnoty dat v jedné nebo více sloupců.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232) v *referenční informace pro OLE DB programátory*. 

## <a name="flushdata"></a> IRowsetChangeImpl::FlushData

Overidden poskytovatelem se zapsat data do svého úložiště.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FlushData(HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush);  
```  
  
#### <a name="parameters"></a>Parametry  

*hRowToFlush*<br/>
[in] Popisovač řádků pro data. Typ tohoto řádku je určen z *RowClass* argument šablony `IRowsetImpl` třídy (`CSimpleRow` ve výchozím nastavení).  
  
*hAccessorToFlush*<br/>
[in] Popisovač přistupujícího objektu, který obsahuje informace o vazbě a informace o typu v jeho `PROVIDER_MAP` (viz [IAccessorImpl –](../../data/oledb/iaccessorimpl-class.md)).  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)