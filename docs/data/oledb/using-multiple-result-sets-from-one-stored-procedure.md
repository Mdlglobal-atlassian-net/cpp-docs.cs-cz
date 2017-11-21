---
title: "Použití více sad výsledků dotazu z jedné uložené procedury | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 787c2123981f894eb4b6ba088cfcef774b6ed6f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Použití více sad výsledků dotazu z jedné uložené procedury
Většina uložených procedur vracejí víc výsledných sad. Uložená procedura obvykle zahrnuje jednu nebo více dotazů select. Příjemce musí obsahovat zpracování všech sad výsledků dotazu.  
  
### <a name="to-handle-multiple-result-sets"></a>Nastaví pro zpracování více výsledků  
  
1.  Vytvoření `CCommand` třídy s `CMultipleResults` jako šablonu argumentu a s přistupujícím podle svého výběru. To je obvykle, dynamické nebo ruční přistupující. Pokud používáte jiný typ přistupujícího objektu, nemusí být schopní určit výstupní sloupce pro každou sadu řádků.  
  
2.  Obvyklým spuštění uložené procedury a vytvořte vazbu sloupce (viz [jak se dá načíst Data?](../../data/oledb/fetching-data.md)).  
  
3.  Použijte data.  
  
4.  Volání `GetNextResult` na `CCommand` třídy. Pokud je k dispozici, jiný výsledek sady řádků `GetNextResult` S_OK vrátí a pokud používáte ruční přistupující objekt by měl znovu svázat sloupce. Pokud `GetNextResult` vrátí chybu, neexistují žádné další výsledky sad k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Použití uložených procedur](../../data/oledb/using-stored-procedures.md)