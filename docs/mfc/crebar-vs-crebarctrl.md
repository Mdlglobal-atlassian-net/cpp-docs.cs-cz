---
title: CReBar vs. CReBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CReBar
- CReBarCtrl
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: a1b5cda729e760246449bf197fdc9b32752b96e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241773"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs. CReBarCtrl

Knihovna MFC poskytuje dvě třídy k vytvoření rebars: [Crebar –](../mfc/reference/crebar-class.md) a [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md) (která zabalí Windows běžný ovládací prvek rozhraní API). `CReBar` obsahuje všechny funkce běžný ovládací prvek matrice, a zpracovává mnoho vyžaduje obecná nastavení ovládacího prvku a struktur za vás.

`CReBarCtrl` je třídou obálky ovládacího prvku matrice Win32 a proto může být snadnější implementovat, pokud nechcete matrice integrovat architektury MFC. Pokud budete chtít použít `CReBarCtrl` a integrovat architektury MFC matrice, je nutné provést dodatečnou pozornost komunikovat manipulace ovládacího prvku matrice ke knihovně MFC. Tato zpráva není složité. je však další práce, nebude potřeba při použití `CReBar`.

Visual C++ poskytuje dva způsoby, jak využít výhod běžný ovládací prvek matrice.

- Vytvoření s použitím matrice `CReBar`a pak vyvolejte [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) získat přístup k `CReBarCtrl` členské funkce.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` je vložené členské funkce, která přetypovává **to** ukazatel objektu matrice. To znamená, že v době běhu, volání funkce nemá žádná režie.

- Vytvoření s použitím matrice [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md)v konstruktoru.

Některé z metod získáte přístup na členské funkce ovládacího prvku rebar. Při volání `CReBar::GetReBarCtrl`, vrátí odkaz na `CReBarCtrl` objektu, můžete použít buď sadu členské funkce. Zobrazit [crebar –](../mfc/reference/crebar-class.md) informace o vytváření a vytvořit matrici pomocí `CReBar`.

## <a name="see-also"></a>Viz také:

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
