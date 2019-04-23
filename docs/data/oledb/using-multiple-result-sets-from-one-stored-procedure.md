---
title: Použití více sad výsledků dotazu z jedné uložené procedury
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 69e5c956d897e217501cbac9b9b93db868731221
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028422"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Použití více sad výsledků dotazu z jedné uložené procedury

Většina uložených procedur vrátit několik sad výsledků. Uložená procedura obvykle obsahuje jeden nebo více dotazů select. Spotřebitel musí vzít v úvahu tato zahrnutí pro zpracování všech sadách výsledků dotazu.

## <a name="to-handle-multiple-result-sets"></a>Nastaví pro zpracování více výsledků

1. Vytvoření `CCommand` třídy s `CMultipleResults` jako argument šablony a s přistupujícím objektu podle vašeho výběru, obvykle dynamická nebo ruční přistupující objekt. Pokud používáte jiný typ přístupového objektu, nemusí být schopní určit, výstupní sloupce pro každou sadu řádků.

1. Spustit uloženou proceduru jako obvykle a vytvořit vazbu sloupce (viz [co a jak načíst Data?](../../data/oledb/fetching-data.md)).

1. Data použijte.

1. Volání `GetNextResult` na `CCommand` třídy. Pokud je k dispozici, jiný výsledek sady řádků `GetNextResult` vrátí hodnotu S_OK a by měl rebind sloupce, pokud používáte ruční přistupujícího objektu. Pokud `GetNextResult` vrátí chybu, existují sady k dispozici žádné další výsledků.

## <a name="see-also"></a>Viz také:

[Použití uložených procedur](../../data/oledb/using-stored-procedures.md)