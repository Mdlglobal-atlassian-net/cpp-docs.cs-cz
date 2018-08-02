---
title: Asyncbase::Close – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d0798a6ef593e388ce7867ee9a55763be9ae890
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463356"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close – metoda
Ukončí asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud operace ukončí nebo je již uzavřeno; v opačném případě E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Poznámky  
 **Close()** je výchozí implementace `IAsyncInfo::Close`, a nemá žádné samotnou práci. Ve skutečnosti zavřete asynchronní operace, přepsat `OnClose()` čistě virtuální metody.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)