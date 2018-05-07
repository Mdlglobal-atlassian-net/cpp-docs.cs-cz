---
title: Použití více sad výsledků dotazu z jedné uložené procedury | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6393901839e8450ebc45b11f1d4bd2250da2ca56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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