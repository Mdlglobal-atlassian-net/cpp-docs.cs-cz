---
title: HandleT::operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa253bec9f150d08f699333cd5d5f6d4538fc2d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653154"
---
# <a name="handletoperator-operator"></a>HandleT::operator= – operátor
Přesune hodnotu zadaného **handlet –** objektů na aktuální **HandleT** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odkaz rvalue na popisovač.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální **HandleT** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Tato operace zruší platnost **handlet –** objekt zadaný parametrem *h*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)