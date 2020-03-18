---
title: CReBar vs. CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 94f889be453a17a55357a260bd2a0c07037f6ded
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445283"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs. CReBarCtrl

Knihovna MFC poskytuje dvě třídy pro vytvoření panelů: [CReBar –](../mfc/reference/crebar-class.md) a [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md) (které balí rozhraní API pro běžné ovládací prvky systému Windows). `CReBar` poskytuje všechny funkce společného ovládacího prvku matrice a zpracovává mnoho z požadovaných obecných nastavení a struktur pro vás.

`CReBarCtrl` je Obálková třída pro matrice ovládací prvek Win32, a proto může být snazší implementovat, pokud nechcete integrovat matrice do architektury MFC. Pokud plánujete použít `CReBarCtrl` a integrujte matrice do architektury knihovny MFC, je nutné provést dodatečnou péči, aby komunikovala s manipulací s řízením matrice do knihovny MFC. Tato komunikace není obtížná; Při použití `CReBar`se ale jedná o další práci, která není potřebná.

Vizuál C++ nabízí dva způsoby, jak využít běžný ovládací prvek matrice.

- Vytvořte matrice pomocí `CReBar`a pak zavolejte [CReBar –:: GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) pro získání přístupu k funkcím členů `CReBarCtrl`.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` je vložená členská funkce, která přetypování ukazatel **This** objektu matrice. To znamená, že v době běhu nemá volání funkce žádnou režii.

- Vytvořte matrice pomocí konstruktoru [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md).

Kterákoli z metod vám poskytne přístup k členským funkcím ovládacího prvku matrice. Když zavoláte `CReBar::GetReBarCtrl`, vrátí odkaz na objekt `CReBarCtrl`, aby bylo možné použít kteroukoli z množiny členských funkcí. Informace o konstrukci a vytváření matrice pomocí `CReBar`najdete v tématu [CReBar –](../mfc/reference/crebar-class.md) .

## <a name="see-also"></a>Viz také

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
