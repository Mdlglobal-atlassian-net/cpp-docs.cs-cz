---
title: Třídy pole, seznamu a mapy
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: f5fe4acb35074e924555029d715ccbc23b55f49a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446508"
---
# <a name="array-list-and-map-classes"></a>Třídy pole, seznamu a mapy

Pro zpracování agregovaných dat knihovna tříd poskytuje skupinu tříd kolekcí – pole, seznamy a mapy – to může obsahovat nejrůznější objekty a předdefinované typy. Kolekce mají dynamicky velikost. Tyto třídy lze použít v jakémkoli programu bez ohledu na to, zda jsou napsány pro systém Windows nebo ne. Jsou však nejužitečnější pro implementaci datových struktur, které definují třídy dokumentů v aplikačním rozhraní. Můžete snadno odvodit specializované třídy kolekcí z těchto nebo je můžete vytvořit na základě tříd šablon. Další informace o těchto přístupůch najdete v článku [kolekce](../mfc/collections.md)článků. Seznam tříd kolekcí šablon naleznete v tématu [třídy šablon článků pro pole, seznamy a mapy](../mfc/template-classes-for-arrays-lists-and-maps.md).

Pole jsou jednorozměrné datové struktury, které jsou uloženy souvisle v paměti. Podporují velmi rychlý přístup s náhodným přístupem, protože adresu paměti libovolného daného elementu lze vypočítat vynásobením indexu prvku velikostí prvku a přidáním výsledku na základní adresu pole. Ale pole jsou velmi nákladné, pokud je nutné vkládat prvky do pole, protože celé pole po vloženém elementu musí být přesunuto, aby uvolnilo místo pro vložení elementu. Pole lze podle potřeby zvětšovat a zmenšovat.

Seznamy jsou podobné polím, ale jsou uloženy velmi jinak. Každý prvek v seznamu také obsahuje ukazatel na předchozí a další prvky, takže je seznam dvakrát propojený. Přidávání nebo odstraňování položek je velmi rychlé, protože pokud tomu tak je, zahrnuje pouze změnu několika ukazatelů. Hledání v seznamu ale může být nákladné, protože všechna hledání musí začít na jednom z konců seznamu.

Mapy mapují klíčovou hodnotu na datovou hodnotu. Například klíč mapy může být řetězec a data a ukazatel na seznam. Požádejte o mapu, aby vám poskytla ukazatel k určitému řetězci. Hledání map je rychlé, protože mapy používají pro vyhledání klíčů zatřiďovací tabulky. Přidávání a odstraňování položek je také rychlé. Mapy se často používají s ostatními datovými strukturami jako pomocné indexy. MFC používá speciální druh mapy označované jako [Mapa zprávy](../mfc/mapping-messages.md) pro mapování zpráv systému Windows na ukazatel na funkci obslužné rutiny pro danou zprávu.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
