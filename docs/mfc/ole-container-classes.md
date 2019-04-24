---
title: OLE – třídy kontejnerů
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 87db824e5ab4daec15870b245ea8341be7442109
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186007"
---
# <a name="ole-container-classes"></a>OLE – třídy kontejnerů

Tyto třídy jsou používány aplikací typu kontejner. Obě `COleLinkingDoc` a `COleDocument` správu kolekcí `COleClientItem` objekty. Místo odvozování vaše dokumentové třídy z `CDocument`, bude odvozovat z `COleLinkingDoc` nebo `COleDocument`, v závislosti na tom, jestli potřebujete podporu pro odkazy na objekty vložené v dokumentu.

Použití `COleClientItem` objekt představující položky OLE v dokumentu, který je vložen z jiného dokumentu nebo odkaz do jiného dokumentu.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Podporuje zahrnutí aktivního dokumentu.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Používá se pro implementaci složeného dokumentu, jakož i podpora základní kontejnerů. Slouží jako kontejner pro třídy odvozené z `CDocItem`. Tato třída slouží jako základní třída pro kontejner dokumentů a je základní třídou pro `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Třída odvozená z `COleDocument` , který poskytuje infrastrukturu pro propojení. Třídy dokumentů by měl být odvozen pro vaše aplikace typu kontejner z této třídy místo z `COleDocument` Pokud chcete, aby podporovaly odkazy na vložené objekty.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Udržuje seznam klientské položky OLE, které jsou v ovládacím prvku RichEdit. Použít s [cricheditview –](../mfc/reference/cricheditview-class.md) a [cricheditcntritem –](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstraktní základní třída `COleClientItem` a `COleServerItem`. Objekty tříd odvozených z `CDocItem` představují části dokumentů.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Třída klienta položky, který představuje na straně klienta pro připojení k vložené nebo propojené položky OLE. Klientské položky odvozovat z této třídy.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Poskytuje přístup na straně klienta OLE položky uložené v ovládacím prvku RichEdit, při použití s `CRichEditView` a `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Výjimka vyplývající z chyby ve zpracování OLE. Tato třída se používá tak, že kontejnery a servery.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
