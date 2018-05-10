---
title: Handlet::detach – metoda | Microsoft Docs
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
ms.openlocfilehash: 100d215099494c9b2714fd2c42dee69644a5006c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="handletdetach-method"></a>HandleT::Detach – metoda
Aktuální objekt HandleT z jeho základní popisovač zrušíte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Základní obslužná rutina.  
  
## <a name="remarks"></a>Poznámky  
 Po dokončení této operace aktuální HandleT nastavena na neplatný stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)