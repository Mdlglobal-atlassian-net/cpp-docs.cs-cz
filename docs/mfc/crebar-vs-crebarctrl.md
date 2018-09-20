---
title: Porovnání atributů CReBar a. Crebarctrl – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133e298cd0bc5b497fbbba47982a755afeefb2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442848"
---
# <a name="crebar-vs-crebarctrl"></a>Porovnání atributů CReBar a. CReBarCtrl

Knihovna MFC poskytuje dvě třídy k vytvoření rebars: [crebar –](../mfc/reference/crebar-class.md) a [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md) (která zabalí Windows běžný ovládací prvek rozhraní API). `CReBar` obsahuje všechny funkce běžný ovládací prvek matrice, a zpracovává mnoho vyžaduje obecná nastavení ovládacího prvku a struktur za vás.

`CReBarCtrl` je třídou obálky ovládacího prvku matrice Win32 a proto může být snadnější implementovat, pokud nechcete matrice integrovat architektury MFC. Pokud budete chtít použít `CReBarCtrl` a integrovat architektury MFC matrice, je nutné provést dodatečnou pozornost komunikovat manipulace ovládacího prvku matrice ke knihovně MFC. Tato zpráva není složité. je však další práce, nebude potřeba při použití `CReBar`.

Visual C++ poskytuje dva způsoby, jak využít výhod běžný ovládací prvek matrice.

- Vytvoření s použitím matrice `CReBar`a pak vyvolejte [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) získat přístup k `CReBarCtrl` členské funkce.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` je vložené členské funkce, která přetypovává **to** ukazatel objektu matrice. To znamená, že v době běhu, volání funkce nemá žádná režie.

- Vytvoření s použitím matrice [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md)v konstruktoru.

Některé z metod získáte přístup na členské funkce ovládacího prvku rebar. Při volání `CReBar::GetReBarCtrl`, vrátí odkaz na `CReBarCtrl` objektu, můžete použít buď sadu členské funkce. Zobrazit [crebar –](../mfc/reference/crebar-class.md) informace o vytváření a vytvořit matrici pomocí `CReBar`.

## <a name="see-also"></a>Viz také

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

