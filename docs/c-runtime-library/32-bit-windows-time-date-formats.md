---
title: "Formáty času data 32bitového systému Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.time
dev_langs:
- C++
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20e812a1eca6e620e0c1847b6ea6a07b871a407d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="32-bit-windows-timedate-formats"></a>Formáty času a data 32bitového systému Windows
Datum a čas souboru jsou uloženy jednotlivě, pomocí znaménka jako bitových polí. Datum a čas souboru plní následujícím způsobem:  
  
### <a name="time"></a>Čas  
  
|Bit pozice:|0   1   2   3   4|5 6 7 8 9 A|B C D E F|  
|-------------------|-----------------------|---------------------------|-----------------------|  
|Délka:|5|6|5|  
|Obsah:|hodiny|minuty|zvýší na 2 sekundy|  
|Rozsah hodnot:|0-23|0-59|0-29 ve 2-druhé intervaly|  
  
### <a name="date"></a>Datum  
  
|Bit pozice:|0   1   2   3   4   5   6|7 8 9 A|B C D E F|  
|-------------------|-------------------------------|-------------------|-----------------------|  
|Délka:|7|4|5|  
|Obsah:|Rok|Měsíc|Den|  
|Rozsah hodnot:|0-119|1-12|1-31|  
||(relativní vůči 1980)|||  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)