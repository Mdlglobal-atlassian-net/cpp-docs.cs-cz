---
title: Vnitřní propojení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b5703ca23a30cdb1d080e1dc379dabfc6c0df1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383992"
---
# <a name="internal-linkage"></a>Vnitřní propojení
Pokud obsahuje deklaraci rozsah souboru identifikátor pro objekt nebo funkce *specifikátor třídy úložiště* **statické**, vnitřní propojení nemá identifikátor. Jinak má identifikátor vnější propojení. V tématu [třídy úložiště](../c-language/c-storage-classes.md) diskuzi o *specifikátor třídy úložiště* nonterminal.  
  
 V rámci jedné jednotky překladu označuje každá instance identifikátoru s vnitřním propojením stejný identifikátor nebo funkci. Vnitřně propojené identifikátory jsou pro jednotku překladu jedinečné.  
  
## <a name="see-also"></a>Viz také  
 [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)