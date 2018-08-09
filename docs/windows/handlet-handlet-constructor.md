---
title: Handlet::handlet – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT, constructor
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7a0bb864fa1356089552fb3c48461fef2a63920b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641376"
---
# <a name="handlethandlet-constructor"></a>HandleT::HandleT – konstruktor
Inicializuje novou instanci třídy **HandleT** třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
explicit HandleT(  
   typename HandleTraits::Type h =   
      HandleTraits::GetInvalidValue()  
);  
  
HandleT(  
   _Inout_ HandleT&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Popisovač.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje **HandleT** objekt, který není platný popisovač pro objekt. Druhý konstruktor vytvoří novou **handlet –** objekt z parametru *h*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)