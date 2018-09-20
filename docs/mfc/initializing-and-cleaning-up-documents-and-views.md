---
title: Inicializace a Uklízení dokumentů a zobrazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdc1efa9d2284a48e4f906a326efcd62dd6c61b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412948"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializace a uklízení dokumentů a zobrazení

Pomocí následujících pokynů pro inicializace a Uklízení po dokumentů a zobrazení:

- Rozhraní MFC inicializuje dokumentů a zobrazení; můžete inicializovat všechna data, která přidáte do nich.

- Rozhraní framework vyčistí jako dokumenty a zobrazeními zavřete; musí uvolnit paměť, která je přidělena v haldě z v rámci členských funkcí těchto dokumentů a zobrazení.

> [!NOTE]
>  Připomínáme, že inicializace pro celou aplikaci se nejlépe provádí v přepsání metody [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) členské funkce třídy `CWinApp`, a čištění pro celou aplikaci se nejlépe provádí v přepsání metody `CWinApp`členskou funkci [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

Životní cyklus dokumentu (a její okno rámce a zobrazení nebo zobrazení) v MDI aplikace vypadá takto:

1. Během dynamické vytváření se nazývá konstruktor dokumentu.

1. Pro každého nového dokumentu, dokument [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) nebo [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) je volána.

1. Uživatel pracuje s dokumentem v průběhu svého životního cyklu. K tomu obvykle dochází, uživatel pracuje s daty dokumentu prostřednictvím zobrazení, výběru a úpravy dat. Zobrazení předává změny do dokumentu za úložiště a aktualizují ostatní zobrazení. Během této doby může zpracovávat příkazy dokumentů a zobrazení.

1. Rámec volá [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) odstranit data specifická pro dokument.

1. Dokumentu destruktoru je volána.

V aplikaci SDI kroku 1 se provádí jednou při prvním vytvoření dokumentu. Kroky 2 až 4 potom opakovaně provádějí pokaždé, když je otevřen nový dokument. Nový dokument opětovně používá existující objekt dokumentu. Krok 5 nakonec je provedena při ukončení aplikace.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Inicializace dokumentů a zobrazení](../mfc/initializing-documents-and-views.md)

- [Uklízení dokumentů a zobrazení](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)

