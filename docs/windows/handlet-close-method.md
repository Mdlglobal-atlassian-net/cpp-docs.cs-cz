---
title: Handlet::Close – metoda | Microsoft Docs
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
ms.openlocfilehash: 4f0c1e47420106651cfe0526d6d212e9819a72ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873248"
---
# <a name="handletclose-method"></a>HandleT::Close – metoda
Zavře aktuální objekt HandleT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Poznámky  
 Popisovač, který je základem aktuální HandleT se zavře a HandleT nastavena na neplatný stav.  
  
 Pokud není správně zavřít popisovač v volající vlákno je vyvolána výjimka.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)