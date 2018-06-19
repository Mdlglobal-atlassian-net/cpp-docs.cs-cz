---
title: IRowsetNotifyCP::Fire_OnRowsetChange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- Fire_OnRowsetChange method
ms.assetid: 412a9ec2-5041-4c56-acda-dc8f8e9b35f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a46879cb301f0140993834021eeaf2bda99b4379
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101991"
---
# <a name="irowsetnotifycpfireonrowsetchange"></a>IRowsetNotifyCP::Fire_OnRowsetChange
Vysílá [onrowsetchange –](https://msdn.microsoft.com/en-us/library/ms722669.aspx) událost pro všechny moduly pro naslouchání ve spojovacím bodě **IID_IRowsetNotify** oznámení příjemci změnu ovlivňující celou sadu řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetNotifyCP – třída](../../data/oledb/irowsetnotifycp-class.md)