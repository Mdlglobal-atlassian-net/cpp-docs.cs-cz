---
title: OLE – třídy kontejnerů
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447664"
---
# <a name="ole-container-classes"></a>OLE – třídy kontejnerů

Tyto třídy jsou používány aplikacemi kontejnerů. `COleLinkingDoc` i `COleDocument` spravují kolekce objektů `COleClientItem`. Namísto odvození třídy dokumentu od `CDocument`ji odvozujete od `COleLinkingDoc` nebo `COleDocument`, a to v závislosti na tom, zda chcete podporovat odkazy na objekty vložené do dokumentu.

Použijte objekt `COleClientItem` pro reprezentaci každé položky OLE v dokumentu, která je vložena z jiného dokumentu nebo je odkazem na jiný dokument.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Podporuje zahrnutí aktivního dokumentu.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Používá se pro implementaci složených dokumentů a také pro základní podporu kontejneru. Slouží jako kontejner pro třídy odvozené od `CDocItem`. Tato třída se dá použít jako základní třída pro dokumenty kontejneru a je základní třídou pro `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Třída odvozená od `COleDocument`, která poskytuje infrastrukturu pro propojování. Třídy dokumentů pro aplikace typu kontejner byste měli odvodit z této třídy místo z `COleDocument`, pokud chcete, aby podporovaly odkazy na vložené objekty.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Udržuje seznam položek klienta OLE, které jsou v ovládacím prvku Rich Edit. Používá se s [CRichEditView –](../mfc/reference/cricheditview-class.md) a [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstraktní základní třída `COleClientItem` a `COleServerItem` Objekty tříd odvozených z `CDocItem` reprezentují části dokumentů.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Třída klientské položky, která představuje stranu klienta připojení k vložené nebo propojené položce OLE. Odvodit klientské položky z této třídy.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Poskytuje přístup na straně klienta k položce OLE uložené v ovládacím prvku s bohatou úpravou při použití s `CRichEditView` a `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Výjimka způsobená selháním při zpracování OLE. Tato třída se používá v kontejnerech i serverech.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
