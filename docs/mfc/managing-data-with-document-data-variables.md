---
title: "Správa dat s použitím datových proměnných dokumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: af24c461d579ee784487697cc376d9e8f0816643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="managing-data-with-document-data-variables"></a>Správa dat s použitím datových proměnných dokumentu
Data vašeho dokumentu implementujte jako členské proměnné dokumentové třídy. Například Scribble program deklaruje člena typu `CObList` – odkazovaného seznamu, která ukládá ukazatele na `CObject` objekty. Tento seznam slouží k uložení pole bodů, které tvoří od ruky kreslení čáry.  
  
 Jak implementovat data člena vašeho dokumentu závisí na povaze vaší aplikace. Můžete si MFC poskytuje skupinu "kolekce třídy" – pole, seznamy a mapy (slovník), včetně kolekce založené na šablonách C++ – spolu s třídy, které zapouzdřit škálu běžné typy dat, jako `CString`, `CRect`, `CPoint`, `CSize`, a `CTime`. Další informace o těchto tříd naleznete v tématu [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.  
  
 Když definujete data člena vašeho dokumentu, obvykle přidáte členské funkce k třídě dokumentu nastavit a získat data položky a provést další užitečné operace na ně.  
  
 Zobrazení přistupovat k objektu dokumentu pomocí zobrazení ukazatele v dokumentu, nainstalovaná v zobrazení v okamžiku vytvoření. Ukazatel this v členské funkce zobrazení můžete získat pomocí volání `CView` – členská funkce **GetDocument**. Ujistěte se, že přetypovat tento ukazatel na vlastní typ dokumentu. Potom můžete přistupovat dokumentu veřejné členy prostřednictvím ukazatele.  
  
 Pokud přenos dat často vyžaduje přímý přístup, nebo chcete použít neveřejní členové třídy dokumentů, můžete vytvořit zobrazení třídy friend (v C++ podmínky) třídy dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Použití dokumentů](../mfc/using-documents.md)
