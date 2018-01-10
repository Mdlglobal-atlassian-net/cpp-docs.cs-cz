---
title: "Podtečení hodnot s plovoucí desetinnou čárkou | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecea42172ed285f24a22cba004fb156784483643
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="underflow-of-floating-point-values"></a>Podtečení hodnot s plovoucí desetinnou čárkou
**ANSI 4.5.1** nastavená celočíselný výraz funkce Matematika `errno` na hodnotu makro `ERANGE` na podtečení rozsah chyby  
  
 Podtečení čísla s plovoucí desetinnou čárkou nenastaví výraz `errno` na hodnotu `ERANGE`. Pokud se hodnota blíží nule a nakonec dojde k podtečení, je hodnota nastavena na nulu.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)