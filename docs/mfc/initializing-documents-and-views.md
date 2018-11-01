---
title: Inicializace dokumentů a zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 2fb557d55576678d8c1199bec20e1fa4c849e1b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612248"
---
# <a name="initializing-documents-and-views"></a>Inicializace dokumentů a zobrazení

Dokumenty jsou vytvořeny dvěma různými způsoby, takže dokumentové třídy musí podporovat oba způsoby. Uživatel nejprve můžete vytvořit nový prázdný dokument pomocí příkazu soubor nový. V takovém případě inicializace dokumentu v přepsání metody [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) členské funkce třídy [CDocument](../mfc/reference/cdocument-class.md). Za druhé můžete uživatele pomocí příkazu Otevřít v nabídce soubor vytvořit nový dokument, jejichž obsah se čtení ze souboru. V takovém případě inicializace dokumentu v přepsání metody [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) členské funkce třídy `CDocument`. Pokud obě inicializace jsou stejné, můžete volat běžné členské funkce z obou přepsání nebo `OnOpenDocument` můžete volat `OnNewDocument` inicializovat vyčistit dokument a pak dokončení operace otevření.

Zobrazení vytvořené po vytvoření své dokumenty. Nejvhodnější čas k inicializaci zobrazení se po dokončení vytváření dokumentů, okno rámce a zobrazení rozhraní framework. Zobrazení můžete inicializovat tak, že přepíšete [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) členskou funkci [CView](../mfc/reference/cview-class.md). Pokud je potřeba znovu inicializovat nebo úpravě pokaždé, když dokumentovat změny, můžete přepsat [OnUpdate](../mfc/reference/cview-class.md#onupdate).

## <a name="see-also"></a>Viz také

[Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

