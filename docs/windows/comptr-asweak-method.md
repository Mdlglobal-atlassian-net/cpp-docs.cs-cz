---
title: Comptr::asweak – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak method
ms.assetid: 23e29dcd-39cb-423f-abe6-6df4428213bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78f6eb9f3d0acf6a28479593d64616fa6881be76
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648087"
---
# <a name="comptrasweak-method"></a>ComPtr::AsWeak – metoda
Získá nestálý odkaz na aktuální objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AsWeak(  
   _Out_ WeakRef* pWeakRef  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *pWeakRef*  
 Když tato operace dokončí, ukazatel na objekt nestálý odkaz.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)