---
title: Asyncbase::checkvalidstateforresultscall – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForResultsCall method
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7308651726abd03f9bd4c9a32550644bec156432
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859898"
---
# <a name="asyncbasecheckvalidstateforresultscall-method"></a>AsyncBase::CheckValidStateForResultsCall – metoda
Ověřuje, zda je možné v aktuálním stavu asynchronní shromažďovat výsledky asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline HRESULT CheckValidStateForResultsCall();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud výsledky můžete shromažďovat; v opačném E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)