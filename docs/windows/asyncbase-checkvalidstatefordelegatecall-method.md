---
title: Asyncbase::checkvalidstatefordelegatecall – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForDelegateCall method
ms.assetid: d997ebe7-2378-4e74-a379-f0f85e6922f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81e3420304b0432f635d04a4892e7984dd38f144
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859872"
---
# <a name="asyncbasecheckvalidstatefordelegatecall-method"></a>AsyncBase::CheckValidStateForDelegateCall – metoda
Ověřuje, zda vlastnosti delegáta lze upravit v aktuálním stavu asynchronní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline HRESULT CheckValidStateForDelegateCall();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud lze upravovat vlastnosti delegáta. v opačném E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)