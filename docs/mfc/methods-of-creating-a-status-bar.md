---
title: Metody vytváření stavového řádku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 784cd7f5768b899388978e6715ff6ca071bf439e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397863"
---
# <a name="methods-of-creating-a-status-bar"></a>Metody vytváření stavového řádku

Knihovna MFC poskytuje dvě třídy k vytvoření stavových řádků: [cstatusbar –](../mfc/reference/cstatusbar-class.md) a [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (která zabalí Windows běžný ovládací prvek rozhraní API). `CStatusBar` obsahuje všechny funkce nástroje na stavovém řádku běžný ovládací prvek automaticky komunikuje se službou nabídek a panelů nástrojů a zpracovává mnoho struktury a vyžaduje obecná nastavení ovládacího prvku pro vás. Avšak výsledný spustitelný soubor obvykle bude větší než vytvořený pomocí `CStatusBarCtrl`.

`CStatusBarCtrl` obvykle za následek menší spustitelný soubor a možná dáte přednost použití `CStatusBarCtrl` Pokud nezamýšlíte integrovat architektury MFC stavový řádek. Pokud budete chtít použít `CStatusBarCtrl` a integrovat architektury MFC stavového řádku, je nutné provést dodatečnou pozornost komunikovat stavového řádku ovládací prvek manipulace s knihovnou MFC. Tato zpráva není složité. je však další práce, nebude potřeba při použití `CStatusBar`.

Visual C++ poskytuje dva způsoby, jak využít výhod stavový panel běžný ovládací prvek.

- Vytváření stavového řádku pomocí `CStatusBar`a pak vyvolejte [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) získat přístup k `CStatusBarCtrl` členské funkce.

- Vytváření stavového řádku pomocí [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)v konstruktoru.

Některé z metod získáte přístup na členské funkce ovládacího panelu stavu. Při volání `CStatusBar::GetStatusBarCtrl`, vrátí odkaz na `CStatusBarCtrl` objektu, můžete použít buď sadu členské funkce. Zobrazit [cstatusbar –](../mfc/reference/cstatusbar-class.md) informace o vytváření a vytváření stavovém řádku pomocí `CStatusBar`.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

