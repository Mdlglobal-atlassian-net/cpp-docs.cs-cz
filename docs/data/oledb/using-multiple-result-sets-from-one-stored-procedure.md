---
title: Použití více sad výsledků dotazu z jedné uložené procedury
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209284"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Použití více sad výsledků dotazu z jedné uložené procedury

Většina uložených procedur vrací více sad výsledků dotazu. Taková uložená procedura obvykle obsahuje jeden nebo více příkazů SELECT. Spotřebitel musí toto zahrnutí vzít v úvahu, aby zpracovávala všechny sady výsledků.

## <a name="to-handle-multiple-result-sets"></a>Postup zpracování více sad výsledků

1. Vytvořte třídu `CCommand` s `CMultipleResults` jako argument šablony a pomocí přístupového objektu podle vlastního výběru, obvykle dynamického nebo ručního přístupového objektu. Pokud použijete jiný typ přístupového objektu, možná nebudete moci určit výstupní sloupce pro každou sadu řádků.

1. Spusťte uloženou proceduru obvyklým způsobem a navažte sloupce (viz [jak načíst data?](../../data/oledb/fetching-data.md)).

1. Použijte data.

1. Volejte `GetNextResult` na `CCommand` třídě. Pokud je k dispozici další sada řádků výsledků, `GetNextResult` vrátí S_OK a pokud používáte ruční přistupující objekt, měli byste znovu vytvořit vazby na sloupce. Pokud `GetNextResult` vrátí chybu, nejsou k dispozici žádné další sady výsledků.

## <a name="see-also"></a>Viz také

[Použití uložených procedur](../../data/oledb/using-stored-procedures.md)
