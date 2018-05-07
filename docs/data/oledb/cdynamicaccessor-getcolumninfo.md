---
title: CDynamicAccessor::GetColumnInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c9fe862f08fc9ecfa280dcbb55f48e14427d6ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetcolumninfo"></a>CDynamicAccessor::GetColumnInfo
Vrátí metadata sloupce potřeby většiny příjemci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRowset`  
 [v] Ukazatel [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) rozhraní.  
  
 *pColumns*  
 [out] Ukazatel na paměti, ve kterém se má vrátit počet sloupců v sadě řádků; Tato hodnota zahrnuje sloupec záložky, pokud existuje.  
  
 *ppColumnInfo*  
 [out] Ukazatel na paměti, ve kterém se má vrátit pole **DBCOLUMNINFO** struktury. V části "DBCOLUMNINFO struktury" v [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
 `ppStringsBuffer`  
 [out] Ukazatel na paměti, ve kterém se vraťte do úložiště pro všechny řetězcové hodnoty ukazatele (názvy použít buď v rámci *columnid* nebo *pwszName*) v rámci bloku jednoho přidělení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) v *referenční příručka programátora technologie OLE DB* informace o typech dat **DBORDINAL**, **DBCOLUMNINFO**, a **OLECHAR**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)