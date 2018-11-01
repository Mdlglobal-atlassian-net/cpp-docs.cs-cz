---
title: Třídy pole, seznamu a mapy
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: 0856a9de06d07b3851dc748644e84ba9c4b56c4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601042"
---
# <a name="array-list-and-map-classes"></a>Třídy pole, seznamu a mapy

Pro zpracování agregace dat, poskytuje knihovna tříd skupinu tříd kolekcí, pole, seznamy a mapy –, který může obsahovat řadu objektu a předdefinovaných typů. Kolekce jsou dynamicky velikost. Tyto třídy lze použít v jakékoli aplikaci, zapsán pro Windows, nebo ne. Nicméně jsou zvláště užitečná pro implementaci datové struktury, které definují třídy dokumentu v rámci aplikace. Specializované kolekce tříd lze snadno odvodit z těchto nebo je můžete vytvořit podle třídy šablony. Další informace o těchto přístupů, najdete v článku [kolekce](../mfc/collections.md). Seznam tříd kolekce šablon, najdete v článku [třídy šablon pro pole, seznamy a mapy](../mfc/template-classes-for-arrays-lists-and-maps.md).

Pole je jednorozměrné datových struktur, které jsou uložena souvisle v paměti. Podporují taky velmi vysoká rychlost náhodného přístupu, protože adresa paměti pro libovolný daný prvek je možné vypočítat index prvku vynásobí velikost elementu a přidáním výsledek do pole Základní adresa. Ale pole jsou velmi náročná, pokud je třeba vložit prvky do pole, od poslední celého pole element vloží má k přesunutí, aby uvolnil prostor pro element, který má být vložen. Pole můžete zvětšovat a zmenšovat podle potřeby.

Seznamy jsou podobná pole, ale jsou uloženy nějak významně odlišně. Každý prvek v seznamu také obsahuje ukazatel na předchozí a další prvky, takže dvakrát propojený seznam. Je velmi rychle přidat nebo odstranit položky, protože to pouze zahrnuje změnu odkazy. Hledání v seznamu však může být nákladné, protože všechna hledání, musí spustit v některém z konce seznamu.

Maps se týkají hodnotu klíče datové hodnoty. Klíč objektu map může být například řetězec a datového ukazatele do seznamu. Zeptáte na mapě získáte ukazatel spojené s konkrétní řetězec. Vyhledávání map jsou rychlé, protože maps používají klíče vyhledávání zatřiďovacích tabulek. Přidávání a odstraňování položek je také rychlé. Mapy se často používá s další datové struktury jako pomocné indexy. Knihovna MFC používá zvláštní druh mapy volána [mapu zpráv](../mfc/mapping-messages.md) mapování zpráv Windows na ukazatel na funkci obslužné rutiny pro zprávy.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

