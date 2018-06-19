---
title: Formáty času data 32bitového systému Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- vc.time
dev_langs:
- C++
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41a415b2601db1e7fc755903145d6dd2b6293ed9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387457"
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