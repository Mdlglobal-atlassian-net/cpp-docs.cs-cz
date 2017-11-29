---
title: "Asyncbase::checkvalidstateforresultscall – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
dev_langs: C++
helpviewer_keywords: CheckValidStateForResultsCall method
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 45b985c3c7b2cffa2ae4f441aad982f677ec40be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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