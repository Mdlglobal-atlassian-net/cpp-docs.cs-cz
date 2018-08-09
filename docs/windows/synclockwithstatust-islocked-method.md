---
title: Synclockwithstatust::islocked – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ebe723811efe62efa85a1cc2fa35736689306c7e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645630"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool IsLocked() const;  
```  
  
## <a name="remarks"></a>Poznámky  
 Označuje, zda aktuální **synclockwithstatust –** vlastní prostředek objektu; to znamená, **synclockwithstatust –** objekt je *uzamčen*.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud **synclockwithstatust –** objekt je uzamčena, jinak **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)