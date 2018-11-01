---
title: OLE – třídy serveru
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 610a69204e5cb66f2129351ab2a04bb0915a1b4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451685"
---
# <a name="ole-server-classes"></a>OLE – třídy serveru

Tyto třídy jsou používány serverových aplikací. Dokumenty na serveru jsou odvozeny z `COleServerDoc` spíše než z `CDocument`. Upozorňujeme, že `COleServerDoc` je odvozen z `COleLinkingDoc`, dokumenty na serveru může být také kontejnery, které podporují propojování.

`COleServerItem` Třída představuje dokument nebo část dokumentu, který může být vložený do jiného dokumentu nebo propojené s.

`COleIPFrameWnd` a `COleResizeBar` podporují místní úpravy. Pokud je objekt v kontejneru a `COleTemplateServer` podporuje vytváření dokumentů/zobrazení dvojice, takže lze upravovat objekty OLE z jiných aplikací.

[Coleserverdoc –](../mfc/reference/coleserverdoc-class.md)<br/>
Použít jako základní třída pro třídy dokumentu serverová aplikace. `COleServerDoc` objekty poskytují hromadné podpora serveru prostřednictvím interakce s `COleServerItem` objekty. Vizuální úpravy funkce je poskytována architekturu document/view knihovny tříd pomocí.

[Cdocitem –](../mfc/reference/cdocitem-class.md)<br/>
Abstraktní základní třída `COleClientItem` a `COleServerItem`. Objekty tříd odvozených z `CDocItem` představují části dokumentů.

[Coleserveritem –](../mfc/reference/coleserveritem-class.md)<br/>
Reprezentuje rozhraní OLE `COleServerDoc` položky. Je obvykle `COleServerDoc` objektu, který reprezentuje vložený část dokumentu. Na serverech, které podporují odkazy na části dokumentů, může být mnoho `COleServerItem` objektů, z nichž každý představuje odkaz na část dokumentu.

[Coleipframewnd –](../mfc/reference/coleipframewnd-class.md)<br/>
Pokud dokument na serveru je upravována v místě, poskytuje okno rámce pro zobrazení.

[Coleresizebar –](../mfc/reference/coleresizebar-class.md)<br/>
Poskytuje standardní uživatelské rozhraní pro změnu velikosti na místě. Objekty této třídy jsou vždy používá ve spojení s `COleIPFrameWnd` objekty.

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Slouží k vytváření dokumentů pomocí architektury dokument/zobrazení rozhraní framework. A `COleTemplateServer` deleguje většinu práce na přiřazený objekt `CDocTemplate` objektu.

[Coleexception –](../mfc/reference/coleexception-class.md)<br/>
Výjimka vyplývající z chyby ve zpracování OLE. Tato třída se používá tak, že kontejnery a servery.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

