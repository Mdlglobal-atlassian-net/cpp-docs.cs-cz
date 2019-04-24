---
title: Bez propojení
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232386"
---
# <a name="no-linkage"></a>Bez propojení

Pokud deklarace identifikátoru v rámci bloku neobsahuje specifikátor paměťové třídy `extern`, nemá identifikátor žádné propojení a je pro funkci unikátní.

Následující identifikátory nemají žádné propojení:

- Identifikátor deklarovaný jako cokoli jiného než objekt nebo funkce

- Identifikátor deklarovaný jako parametr funkce

- Identifikátor rozsahu bloku pro objekt deklarovaný bez specifikátoru třídy úložiště `extern`

Pokud nemá identifikátor žádné propojení, deklarování stejného názvu znovu (v deklarátoru nebo specifikátoru typu) ve stejné úrovni rozsahu vygeneruje chybu předefinování symbolu.

## <a name="see-also"></a>Viz také:

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)
