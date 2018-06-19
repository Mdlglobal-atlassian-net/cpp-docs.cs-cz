---
title: IErrorRecordsImpl::GetErrorHelpContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
dev_langs:
- C++
helpviewer_keywords:
- GetErrorHelpContext method
ms.assetid: 53d70239-0d64-482e-9ad4-4e1f4f02d5a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 684f619dfbf8318951d5668789b6aad18ae48aef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101575"
---
# <a name="ierrorrecordsimplgeterrorhelpcontext"></a>IErrorRecordsImpl::GetErrorHelpContext
Získá ID kontextové nápovědy z záznam chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      DWORD GetErrorHelpContext(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rCurError`  
 `ERRORINFO` v záznamu **IErrorInfo** rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 ID kontextu nápovědy pro chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IErrorRecordsImpl – třída](../../data/oledb/ierrorrecordsimpl-class.md)