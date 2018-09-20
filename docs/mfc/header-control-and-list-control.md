---
title: Ovládací prvky záhlaví a seznam | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24d40ea26a6ff52490b4a501a8b62c0aace660b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407631"
---
# <a name="header-control-and-list-control"></a>Ovládací prvky záhlaví a seznam

Ve většině případů budete používat, který je vložen do ovládacího prvku záhlaví [CListCtrl](../mfc/reference/clistctrl-class.md) nebo [CListView](../mfc/reference/clistview-class.md) objektu. Existují však případech, kdy je žádoucí, jako je například manipulace s daty, uspořádány do sloupců nebo řádků, objekt samostatné záhlaví ovládacího prvku [CView](../mfc/reference/cview-class.md)-odvozenému objektu. V těchto případech potřebujete větší kontrolu nad vzhled a chování vložený záhlaví ovládacího prvku.

V obvyklém případě, že chcete ovládacím prvkem záhlaví poskytnout standard, výchozí chování, můžete chtít použít [CListCtrl](../mfc/reference/clistctrl-class.md) nebo [CListView](../mfc/reference/clistview-class.md) místo. Použití `CListCtrl` když chcete, aby funkce ovládacího prvku záhlaví výchozí, součástí běžné ovládací prvek zobrazení seznamu. Použití [CListView](../mfc/reference/clistview-class.md) když chcete, aby funkce ovládacího prvku záhlaví výchozí, vložit do zobrazení objektu.

> [!NOTE]
>  Tyto ovládací prvky zahrnují integrované záhlaví ovládacího prvku pouze, pokud ovládací prvek zobrazení seznamu je vytvořen pomocí **LVS_REPORT** style.

Ve většině případů lze upravit vzhled ovládacího prvku vloženého záhlaví tak, že změníte styly obsahující ovládací prvek zobrazení seznamu. Kromě toho nejde získat informace o ovládacím prvku záhlaví pomocí členské funkce nadřazeného ovládacího prvku zobrazení seznamu. Pro úplnou kontrolu a přístup pro atributy a stylů vložené záhlaví ovládacího prvku, ale doporučuje získat ukazatel na objekt ovládacího prvku záhlaví.

Objekt embedded záhlaví ovládacího prvku je přístupný z buď `CListCtrl` nebo `CListView` voláním příslušné třídy `GetHeaderCtrl` členskou funkci. Následující kód ukazuje toto:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Použití seznamů obrázků s ovládacími prvky záhlaví](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

