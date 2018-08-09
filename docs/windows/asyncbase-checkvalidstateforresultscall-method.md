---
title: Asyncbase::checkvalidstateforresultscall – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: dfa3b7222a25ed56d014cc90dbffa5f57a2c9436
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651905"
---
# <a name="asyncbasecheckvalidstateforresultscall-method"></a>AsyncBase::CheckValidStateForResultsCall – metoda
Testuje, jestli výsledky asynchronní operace se můžou shromažďovat v aktuálním asynchronní stavu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline HRESULT CheckValidStateForResultsCall();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud výsledky se můžou shromažďovat; S_OK v opačném případě E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)