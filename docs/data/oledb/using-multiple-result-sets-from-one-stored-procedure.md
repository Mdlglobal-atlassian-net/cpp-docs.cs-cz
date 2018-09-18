---
title: Použití více sad výsledků dotazu z jedné uložené procedury | Dokumentace Microsoftu
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
ms.openlocfilehash: 3e75a100bb5b56b613419160a3ea063bce42bbdb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092320"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Použití více sad výsledků dotazu z jedné uložené procedury

Většina uložených procedur vrátit několik sad výsledků. Uložená procedura obvykle obsahuje jeden nebo více dotazů select. Spotřebitel musí vzít v úvahu zpracování všech sadách výsledků dotazu.  
  
### <a name="to-handle-multiple-result-sets"></a>Nastaví pro zpracování více výsledků  
  
1. Vytvoření `CCommand` třídy s `CMultipleResults` jako argument šablony a s přistupujícím objektu podle vašeho výběru. To je obvykle přístupový objekt dynamické nebo ruční. Pokud používáte jiný typ přístupového objektu, nemusí být schopní určit, výstupní sloupce pro každou sadu řádků.  
  
1. Spustit uloženou proceduru jako obvykle a vytvořit vazbu sloupce (viz [co a jak načíst Data?](../../data/oledb/fetching-data.md)).  
  
1. Data použijte.  
  
1. Volání `GetNextResult` na `CCommand` třídy. Pokud je k dispozici, jiný výsledek sady řádků `GetNextResult` vrátí hodnotu S_OK a by měl rebind sloupce, pokud používáte ruční přistupujícího objektu. Pokud `GetNextResult` vrátí chybu, existují sady k dispozici žádné další výsledků.  
  
## <a name="see-also"></a>Viz také  

[Použití uložených procedur](../../data/oledb/using-stored-procedures.md)