---
title: Handlet::handlet – konstruktor | Microsoft Docs
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
ms.openlocfilehash: a0caad909803a0f73987f3e1132920b0948d8d1b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881894"
---
# <a name="handlethandlet-constructor"></a>HandleT::HandleT – konstruktor
Inicializuje novou instanci třídy HandleT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit HandleT(  
   typename HandleTraits::Type h =   
      HandleTraits::GetInvalidValue()  
);  
  
HandleT(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Popisovač.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje objekt HandleT, který není platný popisovač pro objekt. Druhý konstruktor vytvoří nový objekt HandleT z parametru `h`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)