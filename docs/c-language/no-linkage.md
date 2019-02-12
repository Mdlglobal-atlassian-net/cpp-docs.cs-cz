---
title: Bez propojení
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152843"
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
