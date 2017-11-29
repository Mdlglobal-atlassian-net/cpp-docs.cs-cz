---
title: "OLE – třídy kontejnerů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 212e9f67f699281bebd85506e895c22cf012b4be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-container-classes"></a>OLE – třídy kontejnerů
Tyto třídy jsou používány – aplikace typu kontejner. Obě `COleLinkingDoc` a `COleDocument` spravovat kolekce `COleClientItem` objekty. Místo odvozování třídě dokumentu z **CDocument**, budete odvozena z `COleLinkingDoc` nebo `COleDocument`, v závislosti na tom, jestli mají podporu odkazy na objekty vložené v dokumentu.  
  
 Použití `COleClientItem` objekt představující jednotlivé položky OLE odeslání dokumentu, který je vložený z jiného dokumentu nebo odkaz na další dokument.  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 Podporuje obsahování pro aktivní dokument.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Použít pro implementaci složeného dokumentu, jakož i podpora základní kontejnerů. Slouží jako kontejner pro třídy odvozené od `CDocItem`. Tato třída slouží jako základní třída pro kontejner dokumenty a je základní třídou pro `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Třída odvozená z `COleDocument` , poskytuje infrastrukturu pro propojení. Třídy dokumentů by měl být odvozen pro vaše aplikace kontejneru z této třídy místo z `COleDocument` Pokud chcete, aby podporovaly odkazy na vložené objekty.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Udržuje seznam položek OLE klienta, které jsou v ovládacím prvku RichEdit. Použít s [cricheditview –](../mfc/reference/cricheditview-class.md) a [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstraktní základní třídu `COleClientItem` a `COleServerItem`. Objekty třídy odvozené od `CDocItem` představují částí dokumentů.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 Třída položek klienta, která představuje na straně klienta pro připojení k vložené nebo propojené položky OLE. Klientské položky odvozovat z této třídy.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Poskytuje klientský přístup k OLE položky uložené v ovládacím prvku RichEdit při použití s `CRichEditView` a `CRichEditDoc`.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Výsledkem chyba ve zpracování OLE výjimku. Tato třída se používá kontejnery a servery.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)
