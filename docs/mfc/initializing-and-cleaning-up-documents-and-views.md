---
title: "Inicializace a Uklízení dokumentů a zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0546bfc0a5226c6cd22497acae1bb364ceba107b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializace a uklízení dokumentů a zobrazení
Pomocí následujících pokynů pro inicializace a Uklízení po dokumentů a zobrazení:  
  
-   Rozhraní MFC framework inicializuje dokumentů a zobrazení; je-li inicializovat data, která přidáte do nich.  
  
-   Rozhraní framework vyčistí jako dokumenty a zobrazení zavřete; musíte navrátit všechny paměti, které jste přidělili v haldě z v rámci členské funkce těchto dokumentů a zobrazení.  
  
> [!NOTE]
>  Odvolat tuto inicializace pro celou aplikaci se nejlépe provádí v přepsání z [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) funkce člena třídy `CWinApp`, a čištění pro celou aplikaci se nejlépe provádí v vaší přepsání `CWinApp`– členská funkce [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).  
  
 Životní cyklus dokumentu (a její oken s rámečkem a zobrazení nebo zobrazení) MDI aplikace je následující:  
  
1.  Během dynamické vytváření volání konstruktoru dokumentu.  
  
2.  Pro každý nový dokument, dokument na [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) nebo [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) je volána.  
  
3.  Uživatel pracuje s dokumentem v celé jeho životnosti. Obvykle k tomu dojde, protože uživatel pracuje na dokument data prostřednictvím zobrazení, výběr a upravovat data. Zobrazení předá změny k dokumentu pro úložiště a aktualizaci dalšími zobrazeními. Během této doby může zpracovávat příkazy dokumentů a zobrazení.  
  
4.  Volání framework [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) k odstranění dat, které jsou specifické pro dokument.  
  
5.  Je volána destruktor dokumentu.  
  
 V aplikaci SDI krok 1 provádí po prvním vytvoření dokumentu. Kroky 2 až 4 pak opakovaně se pokaždé, když je otevřen nový dokument. Nový dokument opětovně používá existující objekt dokumentu. Krok 5 se nakonec provádí při ukončení aplikace.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Inicializace dokumentů a zobrazení](../mfc/initializing-documents-and-views.md)  
  
-   [Uklízení dokumentů a zobrazení](../mfc/cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)

