---
title: IErrorRecordsImpl::GetErrorSource | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
dev_langs:
- C++
helpviewer_keywords:
- GetErrorSource method
ms.assetid: 5436f1ce-c5a4-403b-a62b-c58e70e5c925
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f076bb7c7d436e65473aadb197a90eae51b07fd4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100379"
---
# <a name="ierrorrecordsimplgeterrorsource"></a>IErrorRecordsImpl::GetErrorSource
Získá zdrojový kód, který způsobil chybu z záznam chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      LPOLESTR GetErrorSource(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rCurError`  
 `ERRORINFO` v záznamu **IErrorInfo** rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který obsahuje zdrojový kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IErrorRecordsImpl – třída](../../data/oledb/ierrorrecordsimpl-class.md)