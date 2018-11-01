---
title: Bez propojení
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: 9775270c5c1fb0b6758f994c432104d75e19d38d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505076"
---
# <a name="no-linkage"></a>Bez propojení

Pokud deklarace identifikátoru v rámci bloku neobsahuje specifikátor paměťové třídy `extern`, nemá identifikátor žádné propojení a je pro funkci unikátní.

Následující identifikátory nemají žádné propojení:

- Identifikátor deklarovaný jako cokoli jiného než objekt nebo funkce

- Identifikátor deklarovaný jako parametr funkce

- Identifikátor rozsahu bloku pro objekt deklarovaný bez specifikátoru třídy úložiště `extern`

Pokud nemá identifikátor žádné propojení, deklarování stejného názvu znovu (v deklarátoru nebo specifikátoru typu) ve stejné úrovni rozsahu vygeneruje chybu předefinování symbolu.

## <a name="see-also"></a>Viz také

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)