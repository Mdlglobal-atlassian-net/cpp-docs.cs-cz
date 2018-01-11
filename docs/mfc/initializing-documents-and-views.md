---
title: "Inicializace dokumentů a zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f80d870f9804454dc652fdda00f34fcdb7a52062
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-documents-and-views"></a>Inicializace dokumentů a zobrazení
Dokumenty jsou vytvořené v dvěma různými způsoby, takže dokumentové třídy musí podporovat obou směrech. První uživatel může vytvořit nového prázdného dokumentu se příkaz Nový soubor. V takovém případě inicializace dokumentu v přepsání systému [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) funkce člena třídy [CDocument](../mfc/reference/cdocument-class.md). Druhý uživatel může použít příkaz Otevřít v nabídce soubor vytvořit nový dokument, jejichž obsah se číst ze souboru. V takovém případě inicializace dokumentu v přepsání systému [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) funkce člena třídy **CDocument**. Pokud oba inicializacích jsou stejné, můžete volat běžné členské funkce z obou přepsání nebo `OnOpenDocument` můžete volat `OnNewDocument` k inicializaci čistou dokumentu a poté otevřete operaci dokončit.  
  
 Zobrazení jsou vytvořeny po vytvoření své dokumenty. Nyní můžete inicializovat zobrazení je po dokončení vytváření dokumentů, oken s rámečkem a zobrazení rozhraní. Zobrazení můžete inicializovat přepsáním [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) členské funkce [CView](../mfc/reference/cview-class.md). Pokud je potřeba znovu inicializovat nebo upravit nic každé změně dokumentu, můžete přepsat [OnUpdate](../mfc/reference/cview-class.md#onupdate).  
  
## <a name="see-also"></a>Viz také  
 [Inicializace a uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

