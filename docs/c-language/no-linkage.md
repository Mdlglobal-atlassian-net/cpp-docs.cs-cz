---
title: Bez propojení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc6515020272d19a9b9efca7341293be4983a56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383784"
---
# <a name="no-linkage"></a>Bez propojení
Pokud deklarace identifikátoru v rámci bloku neobsahuje specifikátor paměťové třídy `extern`, nemá identifikátor žádné propojení a je pro funkci unikátní.  
  
 Následující identifikátory nemají žádné propojení:  
  
-   Identifikátor deklarovaný jako cokoli jiného než objekt nebo funkce  
  
-   Identifikátor deklarovaný jako parametr funkce  
  
-   Identifikátor rozsahu bloku pro objekt deklarovaný bez specifikátoru třídy úložiště `extern`  
  
 Pokud nemá identifikátor žádné propojení, deklarování stejného názvu znovu (v deklarátoru nebo specifikátoru typu) ve stejné úrovni rozsahu vygeneruje chybu předefinování symbolu.  
  
## <a name="see-also"></a>Viz také  
 [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)