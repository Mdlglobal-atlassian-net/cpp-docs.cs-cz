---
title: CTable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c94152a9322b64acafe91e1fb0eb34ab82aa2902
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081296"
---
# <a name="ctable-class"></a>CTable – třída

Poskytuje prostředky pro přímý přístup k jednoduché sady řádků (jeden bez parametrů).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
```  
  
### <a name="parameters"></a>Parametry  

*TAccessor*<br/>
Třídu přistupujícího objektu.  
  
*TRowset*<br/>
Třídy sady řádků.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Otevřít](#open)|Otevře se v tabulce.|  
  
## <a name="remarks"></a>Poznámky  

Zobrazit [CCommand](../../data/oledb/ccommand-class.md) informace o tom, jak provést příkaz pro přístup k sadě řádků.  

## <a name="open"></a> CTable::Open

Otevře se v tabulce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  

HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  

HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  

*Relace*<br/>
[in] Relace, pro který je otevřen v tabulce.  
  
*wszTableName*<br/>
[in] Název tabulky, pokud chcete otevřít, je předán jako řetězec znaků Unicode.  
  
*szTableName*<br/>
[in] Název tabulky, pokud chcete otevřít, je předán jako řetězec ANSI.  
  
*DBID*<br/>
[in] `DBID` Tabulky otevřete.  
  
*pPropSet*<br/>
[in] Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury obsahující vlastnosti a hodnoty, která se má nastavit. Zobrazit [sady vlastností a vlastností skupiny](/previous-versions/windows/desktop/ms713696\(v=vs.85\)) v *referenční informace pro OLE DB programátory* ve Windows SDK. Výchozí hodnota Null určuje žádné vlastnosti.  
  
*ulPropSets*<br/>
[in] Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury předané *pPropSet* argument.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Další podrobnosti najdete v tématu [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) v *OLE DB referenční informace pro programátory*.  
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   