---
title: Podtečení hodnot s plovoucí desetinnou čárkou | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ceaa41dcaca88c7857a03c16ccccabdba086fd0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387821"
---
# <a name="underflow-of-floating-point-values"></a>Podtečení hodnot s plovoucí desetinnou čárkou
**ANSI 4.5.1** nastavená celočíselný výraz funkce Matematika `errno` na hodnotu makro `ERANGE` na podtečení rozsah chyby  
  
 Podtečení čísla s plovoucí desetinnou čárkou nenastaví výraz `errno` na hodnotu `ERANGE`. Pokud se hodnota blíží nule a nakonec dojde k podtečení, je hodnota nastavena na nulu.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)