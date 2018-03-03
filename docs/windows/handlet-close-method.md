---
title: "Handlet::Close – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2edd3fee9893c72685eb334bf4b361997646b7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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