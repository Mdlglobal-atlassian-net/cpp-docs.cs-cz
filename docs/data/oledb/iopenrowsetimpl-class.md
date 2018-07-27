---
title: Iopenrowsetimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd3281aa21cfd20caa902572e9ad39e16a18e6f6
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269823"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl – třída
Poskytuje implementaci pro `IOpenRowset` rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
### <a name="parameters"></a>Parametry  
 *SessionClass*  
 Vaše třída odvozena od `IOpenRowsetImpl`.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Createrowset –](#createrowset)|Vytvoří objekt sady řádků. Nebyla volána přímo uživatelem.|  
|[OpenRowset](#openrowset)|Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu. (Není v ATLDB. H)|  
  
## <a name="remarks"></a>Poznámky  
 [IOpenRowset](https://msdn.microsoft.com/library/ms716946.aspx) rozhraní je povinné pro objekt relace. Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu.  
  
## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset
Vytvoří objekt sady řádků. Nebyla volána přímo uživatelem. Zobrazit [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) v *referenční informace pro OLE DB programátory.*  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parametry  
 *RowsetClass*  
 Šablona člena třídy představující třídu sady řádků uživatele. Obvykle generované průvodcem knihovnou.  
  
 *pRowsetObj*  
 [out] Ukazatel na objektu sady řádků. Tento parametr se obvykle nepoužívá, ale lze použít, pokud před předáním objektu COM je nutné provést další práce na dané sadě řádků. Životnost *pRowsetObj* je svázaná s *ppRowset*.  
  
 Další parametry, naleznete v tématu [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) v *OLE DB referenční informace pro programátory.*  

## <a name="openrowset"></a> IOpenRowsetImpl::OpenRowset
Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nebyla nalezena v ATLDB. H. Je vytvořen objekt Průvodcem knihovnou ATL při vytváření zprostředkovatele.  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
