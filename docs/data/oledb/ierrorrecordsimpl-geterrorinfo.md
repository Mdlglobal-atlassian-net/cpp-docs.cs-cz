---
title: IErrorRecordsImpl::GetErrorInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetErrorInfo
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
dev_langs: C++
helpviewer_keywords: GetErrorInfo method
ms.assetid: 44d0872f-f25f-4102-8f7f-a2cfb3eeb1a0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dc478f7e33423971e2e11e09099baabb92fdd666
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ierrorrecordsimplgeterrorinfo"></a>IErrorRecordsImpl::GetErrorInfo
Vrátí [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) ukazatel rozhraní na zadaný záznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD( GetErrorInfo )(  
   ULONG ulRecordNum,  
   LCID lcid,  
   IErrorInfo **ppErrorInfo   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IErrorRecordsImpl – třída](../../data/oledb/ierrorrecordsimpl-class.md)