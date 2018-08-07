---
title: Handlet::Close – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69f3f2c756d158954676f6fc42941b1b80f4345e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569915"
---
# <a name="handletclose-method"></a>HandleT::Close – metoda
Zavře aktuální **HandleT** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Poznámky  
 Popisovač, které je základem aktuální **handlet –** je zavřená a **HandleT** je nastavena na neplatný stav.  
  
 Pokud je popisovač nezavírá správně, je vyvolána výjimka ve volajícím vlákně.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)