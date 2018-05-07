---
title: Inicializace dokumentů a zobrazení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e46d130f535076c2591101ab57423db1130ef749
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="initializing-documents-and-views"></a>Inicializace dokumentů a zobrazení
Dokumenty jsou vytvořené v dvěma různými způsoby, takže dokumentové třídy musí podporovat obou směrech. První uživatel může vytvořit nového prázdného dokumentu se příkaz Nový soubor. V takovém případě inicializace dokumentu v přepsání systému [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) funkce člena třídy [CDocument](../mfc/reference/cdocument-class.md). Druhý uživatel může použít příkaz Otevřít v nabídce soubor vytvořit nový dokument, jejichž obsah se číst ze souboru. V takovém případě inicializace dokumentu v přepsání systému [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) funkce člena třídy **CDocument**. Pokud oba inicializacích jsou stejné, můžete volat běžné členské funkce z obou přepsání nebo `OnOpenDocument` můžete volat `OnNewDocument` k inicializaci čistou dokumentu a poté otevřete operaci dokončit.  
  
 Zobrazení jsou vytvořeny po vytvoření své dokumenty. Nyní můžete inicializovat zobrazení je po dokončení vytváření dokumentů, oken s rámečkem a zobrazení rozhraní. Zobrazení můžete inicializovat přepsáním [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) členské funkce [CView](../mfc/reference/cview-class.md). Pokud je potřeba znovu inicializovat nebo upravit nic každé změně dokumentu, můžete přepsat [OnUpdate](../mfc/reference/cview-class.md#onupdate).  
  
## <a name="see-also"></a>Viz také  
 [Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

