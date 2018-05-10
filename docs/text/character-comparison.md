---
title: Znak porovnání | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b969783a19c0836a8ab81d75820fc688df3ef31e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="character-comparison"></a>Porovnávání znaků
Použijte následující tipy:  
  
-   Porovnání známé úvodní bajt znakem ASCII funguje správně:  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Porovnání dvou neznámých znaků vyžaduje použití jednoho z maker definovaných v Mbstring.h:  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Tím se zajistí, že jsou oba bajtů dvoubajtové znakové porovnána shoda.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Přetečení vyrovnávací paměti](../text/buffer-overflow.md)