---
title: Handlenulltraits::Close – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0206433d2b329501b10a8262e7b487ec83e99302
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642107"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close – metoda
Zavře určený.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Obslužná rutina zavřete.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** pokud zpracování *h* zavření úspěšně; v opačném případě **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [HANDLENullTraits – struktura](../windows/handlenulltraits-structure.md)