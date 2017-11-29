---
title: "Třídy dokumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.document
dev_langs: C++
helpviewer_keywords: document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9acba558a915b90e87490ecb993061effc3049a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="document-classes"></a>Třídy dokumentů
Objekty třídy dokumentu, vytvořené objekty šablony dokumentu, spravovat data aplikace. Pro vaše dokumenty budou odvození třídy z jedné z těchto tříd.  
  
 Objekty třídy dokumentu pracovat s objekty zobrazení. Objekty zobrazení představují klientské oblasti časového období, zobrazí data dokumentu a povolit uživatelům interakci s ním. Dokumenty a zobrazení jsou vytvořené pomocí objektu šablony dokumentu.  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 Základní třída pro dokumenty specifické pro aplikaci. Odvození dokumentové třídy nebo třídy z **CDocument**.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Použít pro implementaci složeného dokumentu, jakož i podpora základní kontejnerů. Slouží jako kontejner pro třídy odvozené od [CDocItem](../mfc/reference/cdocitem-class.md). Tato třída slouží jako základní třída pro kontejner dokumenty a je základní třídou pro `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Třída odvozená z `COleDocument` , poskytuje infrastrukturu pro propojení. Třídy dokumentů by měl být odvozen pro vaše aplikace kontejneru z této třídy místo z `COleDocument` Pokud chcete, aby podporovaly odkazy na vložené objekty.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Udržuje seznam položek OLE klienta, které jsou v ovládacím prvku RichEdit. Použít s [cricheditview –](../mfc/reference/cricheditview-class.md) a [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Použít jako základní třída pro třídy dokumentů serverových aplikací. `COleServerDoc`objekty poskytují hromadným podpora serveru prostřednictvím interakce s [COleServerItem](../mfc/reference/coleserveritem-class.md) objekty. Visual úpravy funkce je k dispozici pomocí architektury dokument/zobrazení knihovny tříd.  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 Poskytuje, s [CHtmlEditView](../mfc/reference/chtmleditview-class.md), funkce úpravy platformy WebBrowser HTML v kontextu architektury MFC zobrazení dokumentu.  
  
## <a name="related-classes"></a>Související třídy  
 Objekty třídy dokumentu může být trvalá – jinými slovy, můžete napsat jejich stavu do média, úložiště a přečtěte si ho zpátky. Poskytuje MFC `CArchive` třídy pro usnadnění přenosu dat dokumentu do paměťového média.  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 Spolupracuje s [cfile –](../mfc/reference/cfile-class.md) objektu k implementaci trvalého úložiště pro objekty prostřednictvím serializace (viz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 Dokumenty může také obsahovat objekty OLE. `CDocItem`je základní třída položek serveru a klienta.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstraktní základní třídu [COleClientItem](../mfc/reference/coleclientitem-class.md) a [COleServerItem](../mfc/reference/coleserveritem-class.md). Objekty třídy odvozené od `CDocItem` představují částí dokumentů.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)
