---
title: Inicializace a uklízení dokumentů a zobrazení
ms.date: 11/04/2016
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
ms.openlocfilehash: 3c92d60941cd6542bd0d6c27e8a879dc85e3a3d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377207"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializace a uklízení dokumentů a zobrazení

Pro inicializaci a vyčištění po dokumentech a zobrazeních použijte následující pokyny:

- Rozhraní knihovny MFC inicializuje dokumenty a zobrazení. inicializujete všechna data, která k nim přidáte.

- Rámec vyčistí jako dokumenty a zobrazení blízko; je nutné navrátit všechny paměti, které jste přidělili na haldě z v rámci členské funkce těchto dokumentů a zobrazení.

> [!NOTE]
> Připomeňme, že inicializace pro celou aplikaci se nejlépe provádí v přepsání členské funkce [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) třídy `CWinApp`a vyčištění pro celou aplikaci se nejlépe provádí v přepsání `CWinApp` členské funkce [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

Životní cyklus dokumentu (a jeho okna a zobrazení a zobrazení rámce) v aplikaci MDI je následující:

1. Během dynamického vytváření se nazývá konstruktor dokumentu.

1. Pro každý nový dokument se nazývá [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) dokumentu nebo [OnOpenDocument.](../mfc/reference/cdocument-class.md#onopendocument)

1. Uživatel pracuje s dokumentem po celou dobu jeho životnosti. Obvykle k tomu dochází, když uživatel pracuje na datech dokumentu prostřednictvím zobrazení, výběru a úpravy dat. Zobrazení předá změny dokumentu pro ukládání a aktualizaci dalších zobrazení. Během této doby může dokument i zobrazení zpracovávat příkazy.

1. Rozhraní Framework volá [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) k odstranění dat specifických pro dokument.

1. Destruktor dokumentu se nazývá.

V aplikaci SDI krok 1 se provádí jednou při prvním vytvoření dokumentu. Kroky 2 až 4 se pak provádějí opakovaně při každém otevření nového dokumentu. Nový dokument znovu použije existující objekt dokumentu. Nakonec krok 5 se provádí po ukončení aplikace.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Inicializace dokumentů a zobrazení](../mfc/initializing-documents-and-views.md)

- [Uklízení dokumentů a zobrazení](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Viz také

[Architektura dokumentu/zobrazení](../mfc/document-view-architecture.md)
