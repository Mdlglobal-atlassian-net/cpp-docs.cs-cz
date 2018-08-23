---
title: Porovnání znaků | Dokumentace Microsoftu
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 246801abcb04cc8d9c2fd1a005183501bde240d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612323"
---
# <a name="character-comparison"></a>Porovnávání znaků
Použijte následující tipy:  
  
-   Porovnání známé vedoucí bajt s znaku ASCII funguje správně:  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Porovnání dvou znaků Neznámý vyžaduje použití některého z makra definovaná v Mbstring.h:  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Tím se zajistí, že jsou oba bajtů dvoubajtové znakové porovnána shoda.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Přetečení vyrovnávací paměti](../text/buffer-overflow.md)