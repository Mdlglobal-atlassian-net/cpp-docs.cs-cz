---
title: CDBErrorInfo::GetErrorParameters | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
dev_langs:
- C++
helpviewer_keywords:
- GetErrorParameters method
ms.assetid: 3a2dd8e2-fecc-4315-9f2b-ce3138cdd187
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5082fd09b716fbc2d69abaa121397acb3140825a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdberrorinfogeterrorparameters"></a>CDBErrorInfo::GetErrorParameters
Volání [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) vrátit parametry chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT GetErrorParameters(ULONG ulRecordNum,   
  DISPPARAMS* pdispparams) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDBErrorInfo – třída](../../data/oledb/cdberrorinfo-class.md)