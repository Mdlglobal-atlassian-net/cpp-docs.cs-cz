---
title: IRowsetNotifyCP::Fire_OnRowsetChange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3116901a5984e0af2587abf17419df3923d1940d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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