---
title: Handlet::detach – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7bf4a6fab735708295a0ae229e7b47101ecc115b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648389"
---
# <a name="handletdetach-method"></a>HandleT::Detach – metoda
Zruší přidružení aktuální **HandleT** objekt z jeho základní popisovač.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Základní popisovač.  
  
## <a name="remarks"></a>Poznámky  
 Když tato operace dokončí, aktuální **HandleT** je nastavena na neplatný stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)