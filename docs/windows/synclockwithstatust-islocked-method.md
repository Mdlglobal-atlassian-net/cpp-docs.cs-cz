---
title: Synclockwithstatust::islocked – metoda | Microsoft Docs
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
ms.openlocfilehash: a564c4223b09d9295ff0ac3159e165944c4d885d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892550"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool IsLocked() const;  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje, zda je aktuální objekt SyncLockWithStatusT vlastní prostředek; To znamená, je objekt SyncLockWithStatusT *uzamčení*.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud objekt SyncLockWithStatusT je uzamčení, jinak hodnota **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)