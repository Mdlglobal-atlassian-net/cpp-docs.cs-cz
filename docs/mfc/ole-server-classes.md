---
title: OLE – třídy serveru
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 92dec514611dcce7d6c666fdd271843e69561637
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447590"
---
# <a name="ole-server-classes"></a>OLE – třídy serveru

Tyto třídy používají serverové aplikace. Dokumenty serveru jsou odvozeny z `COleServerDoc` spíše než z `CDocument`. Vzhledem k tomu, že `COleServerDoc` je odvozená od `COleLinkingDoc`, serverové dokumenty můžou být také kontejnery, které podporují propojování.

Třída `COleServerItem` představuje dokument nebo část dokumentu, která může být vložena do jiného dokumentu nebo propojena s.

`COleIPFrameWnd` a `COleResizeBar` podporu místních úprav, zatímco je objekt v kontejneru, a `COleTemplateServer` podporuje vytváření párů dokument/zobrazení, aby bylo možné upravovat objekty OLE z jiných aplikací.

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Slouží jako základní třída pro třídy dokumentu serverové aplikace. `COleServerDoc` objekty poskytují hromadnou podporu serveru prostřednictvím interakcí s objekty `COleServerItem`. Funkce úprav vizuálního prostředí je k dispozici pomocí architektury document/view knihovny tříd.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstraktní základní třída `COleClientItem` a `COleServerItem` Objekty tříd odvozených z `CDocItem` reprezentují části dokumentů.

[Odvozenou třídu COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
Slouží k reprezentaci rozhraní OLE pro `COleServerDoc` položek. K dispozici je obvykle jeden `COleServerDoc` objekt, který představuje vloženou část dokumentu. V serverech, které podporují odkazy na části dokumentů, může existovat mnoho `COleServerItem` objektů, z nichž každý představuje odkaz na část dokumentu.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Poskytuje okno rámce pro zobrazení při upravovaném dokumentu serveru.

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
Poskytuje standardní uživatelské rozhraní pro místní změnu velikosti. Objekty této třídy se vždycky používají ve spojení s `COleIPFrameWnd` objekty.

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Slouží k vytváření dokumentů pomocí architektury dokument/zobrazení rozhraní. Objekt `COleTemplateServer` deleguje většinu práce na přidružený objekt `CDocTemplate`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Výjimka způsobená selháním při zpracování OLE. Tato třída se používá v kontejnerech i serverech.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
