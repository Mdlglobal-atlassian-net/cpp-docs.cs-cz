---
title: Výhody architektury Document / View | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 213fc108b11d6056df6696f92658e74a736c4a16
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392837"
---
# <a name="advantages-of-the-documentview-architecture"></a>Výhody architektury dokument/zobrazení

Hlavní výhodou používání architektury dokument/zobrazení MFC je, že architektura podporuje několik zobrazení stejné dokumentu obzvláště dobře. (Pokud není nutné více zobrazení a malé nároky na dokument/zobrazení je příliš ve vaší aplikaci, můžete se vyhnout architekturu. [Alternativy k architektuře dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md).)

Předpokládejme, že vaše aplikace umožňuje uživatelům prohlížet číselná data v podobě tabulky nebo v podobě grafu. Uživatel může být potřeba se podívat současně nezpracovaná data, ve formuláři tabulky a grafu, která je výsledkem data. Tyto samostatné zobrazení se zobrazí v samostatném okna s rámečkem nebo rozdělovač podokna v jednom okně. Nyní předpokládejme, že uživatel může upravovat data v tabulce a viz změny okamžitě projeví v grafu.

V knihovně MFC zobrazení tabulky a zobrazení grafu vycházet z jiné třídy odvozené od CView. Obě zobrazení bude přidružena k objektu jednotlivý dokument. Dokument uloží data (nebo možná získá z databáze). Obě zobrazení přístup k dokumentu a zobrazit data, která se načíst z něj.

Když uživatel aktualizuje jedno zobrazení, které zobrazení volání objektu `CDocument::UpdateAllViews`. Tuto funkci se upozorní všechna zobrazení dokumentu a každé zobrazení aktualizuje pomocí nejnovějších dat z dokumentu. Jediné volání `UpdateAllViews` synchronizuje různá zobrazení.

Tento scénář by bylo obtížné kódu bez oddělit data ze zobrazení, zejména v případě, že zobrazení ukládají data sami. S dokument/zobrazení je snadné. Většina práce koordinace rozhraní udělá za vás.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Alternativy k dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)

