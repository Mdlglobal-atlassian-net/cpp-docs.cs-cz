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
ms.openlocfilehash: 723d4f1e8f44c3ce376b4f39f34a191265ca4eab
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336723"
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
 *TAccessor*  
 Třídu přistupujícího objektu.  
  
 *TRowset*  
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
 *Relace*  
 [in] Relace, pro který je otevřen v tabulce.  
  
 *wszTableName*  
 [in] Název tabulky, pokud chcete otevřít, je předán jako řetězec znaků Unicode.  
  
 *szTableName*  
 [in] Název tabulky, pokud chcete otevřít, je předán jako řetězec ANSI.  
  
 *DBID*  
 [in] `DBID` Tabulky otevřete.  
  
 *pPropSet*  
 [in] Ukazatel na pole [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) struktury obsahující vlastnosti a hodnoty, která se má nastavit. Zobrazit [sady vlastností a vlastností skupiny](https://msdn.microsoft.com/library/ms713696.aspx) v *referenční informace pro OLE DB programátory* ve Windows SDK. Výchozí hodnota Null určuje žádné vlastnosti.  
  
 *ulPropSets*  
 [in] Počet [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) struktury předané *pPropSet* argument.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Další podrobnosti najdete v tématu [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) v *OLE DB referenční informace pro programátory*.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   