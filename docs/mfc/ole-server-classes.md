---
title: "OLE – třídy serveru | Microsoft Docs"
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
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bfac148696a40fcb8b8d054e7ce8d7da7e0daf15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-server-classes"></a>OLE – třídy serveru
Tyto třídy jsou používány serverových aplikací. Dokumenty na serveru jsou odvozeny od `COleServerDoc` spíše než z **CDocument**. Všimněte si, že protože `COleServerDoc` je odvozený od `COleLinkingDoc`, dokumenty na serveru může být také kontejnery, které podporují propojení.  
  
 `COleServerItem` Třída reprezentuje dokument nebo část dokumentu, která se dá vložené do jiného dokumentu nebo propojen.  
  
 `COleIPFrameWnd`a `COleResizeBar` podporovat úpravy v místě, pokud je objekt v kontejneru a `COleTemplateServer` podporuje vytvoření dvojic document/view –, takže lze upravovat objekty OLE z jiných aplikací.  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Použít jako základní třída pro třídy dokumentů serverových aplikací. `COleServerDoc`objekty poskytují hromadným podpora serveru prostřednictvím interakce s `COleServerItem` objekty. Visual úpravy funkce je k dispozici pomocí architektury dokument/zobrazení knihovny tříd.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstraktní základní třídu `COleClientItem` a `COleServerItem`. Objekty třídy odvozené od `CDocItem` představují částí dokumentů.  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 Představuje rozhraní OLE `COleServerDoc` položky. Je obvykle jedna `COleServerDoc` objekt, který reprezentuje část vloženého dokumentu. Na serverech, které podporují odkazy na části dokumentů, může být mnoho `COleServerItem` objekty, z nichž každý představuje odkaz pro část dokumentu.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Poskytuje okně s rámečkem pro zobrazení, pokud server dokumentu upravována na místě.  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 Poskytuje standardní uživatelské rozhraní pro změnu velikosti na místě. Objekty této třídy jsou vždy používá ve spojení s `COleIPFrameWnd` objekty.  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 Použít k vytvoření dokumentů pomocí rozhraní framework document/view – architektura. A `COleTemplateServer` objekt deleguje většinu práce na přiřazený `CDocTemplate` objektu.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Výsledkem chyba ve zpracování OLE výjimku. Tato třída se používá kontejnery a servery.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)
