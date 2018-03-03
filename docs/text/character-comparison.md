---
title: "Znak porovnání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28c2cd3a2e868a595d73d06b5cae8e71ec8cc313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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