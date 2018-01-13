---
title: "Bez propojení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: abacc6fbd49f9f42620385a4206c9412648c173b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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