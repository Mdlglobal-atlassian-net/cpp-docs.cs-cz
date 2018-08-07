---
title: Handlet::internalclose – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a54b61902c8994397c7bd6effa74a90d43c7e512
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568638"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose – metoda
Zavře aktuální **HandleT** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud aktuální **handlet –** zavření úspěšně; v opačném případě **false**.  
  
## <a name="remarks"></a>Poznámky  
 **InternalClose()** je **chráněné**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)