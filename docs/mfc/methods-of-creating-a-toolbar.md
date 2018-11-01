---
title: Metody vytváření panelů nástrojů
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: 5296c0454e035770e196c3d6a4d15291d0c4ca6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612456"
---
# <a name="methods-of-creating-a-toolbar"></a>Metody vytváření panelů nástrojů

Knihovna MFC poskytuje dvě třídy pro vytváření panelů nástrojů: [ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (která zabalí Windows běžný ovládací prvek rozhraní API). `CToolBar` obsahuje všechny funkce běžný ovládací prvek panelu nástrojů, a zpracovává mnoho struktury a vyžaduje obecná nastavení ovládacího prvku pro vás. Avšak výsledný spustitelný soubor obvykle bude větší než vytvořený pomocí `CToolBarCtrl`.

`CToolBarCtrl` obvykle za následek menší spustitelný soubor a možná dáte přednost použití `CToolBarCtrl` Pokud nezamýšlíte integrovat architektury MFC panelu nástrojů. Pokud budete chtít použít `CToolBarCtrl` a integrovat panelu nástrojů do architektury MFC, je nutné provést dodatečnou pozornost komunikovat manipulace ovládacího prvku panel nástrojů ke knihovně MFC. Tato zpráva není složité. je však další práce, nebude potřeba při použití `CToolBar`.

Visual C++ poskytuje dva způsoby, jak využít výhod běžný ovládací prvek panelu nástrojů.

- Vytvoření s použitím nástrojů `CToolBar`a pak vyvolejte [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) získat přístup k `CToolBarCtrl` členské funkce.

- Vytvoření s použitím nástrojů [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)v konstruktoru.

Některé z metod získáte přístup na členské funkce ovládacího prvku toolbar. Při volání `CToolBar::GetToolBarCtrl`, vrátí odkaz na `CToolBarCtrl` objektu, můžete použít buď sadu členské funkce. Zobrazit [ctoolbar –](../mfc/reference/ctoolbar-class.md) informace o vytváření a vytvořit pomocí nástrojů `CToolBar`.

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

