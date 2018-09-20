---
title: OLE – třídy kontejnerů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e17161340881bb53601bc04dce6f5e375f746b02
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404706"
---
# <a name="ole-container-classes"></a>OLE – třídy kontejnerů

Tyto třídy jsou používány aplikací typu kontejner. Obě `COleLinkingDoc` a `COleDocument` správu kolekcí `COleClientItem` objekty. Místo odvozování vaše dokumentové třídy z `CDocument`, bude odvozovat z `COleLinkingDoc` nebo `COleDocument`, v závislosti na tom, jestli potřebujete podporu pro odkazy na objekty vložené v dokumentu.

Použití `COleClientItem` objekt představující položky OLE v dokumentu, který je vložen z jiného dokumentu nebo odkaz do jiného dokumentu.

[Coledocobjectitem –](../mfc/reference/coledocobjectitem-class.md)<br/>
Podporuje zahrnutí aktivního dokumentu.

[Coledocument –](../mfc/reference/coledocument-class.md)<br/>
Používá se pro implementaci složeného dokumentu, jakož i podpora základní kontejnerů. Slouží jako kontejner pro třídy odvozené z `CDocItem`. Tato třída slouží jako základní třída pro kontejner dokumentů a je základní třídou pro `COleServerDoc`.

[Colelinkingdoc –](../mfc/reference/colelinkingdoc-class.md)<br/>
Třída odvozená z `COleDocument` , který poskytuje infrastrukturu pro propojení. Třídy dokumentů by měl být odvozen pro vaše aplikace typu kontejner z této třídy místo z `COleDocument` Pokud chcete, aby podporovaly odkazy na vložené objekty.

[Cricheditdoc –](../mfc/reference/cricheditdoc-class.md)<br/>
Udržuje seznam klientské položky OLE, které jsou v ovládacím prvku RichEdit. Použít s [cricheditview –](../mfc/reference/cricheditview-class.md) a [cricheditcntritem –](../mfc/reference/cricheditcntritem-class.md).

[Cdocitem –](../mfc/reference/cdocitem-class.md)<br/>
Abstraktní základní třída `COleClientItem` a `COleServerItem`. Objekty tříd odvozených z `CDocItem` představují části dokumentů.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Třída klienta položky, který představuje na straně klienta pro připojení k vložené nebo propojené položky OLE. Klientské položky odvozovat z této třídy.

[Cricheditcntritem –](../mfc/reference/cricheditcntritem-class.md)<br/>
Poskytuje přístup na straně klienta OLE položky uložené v ovládacím prvku RichEdit, při použití s `CRichEditView` a `CRichEditDoc`.

[Coleexception –](../mfc/reference/coleexception-class.md)<br/>
Výjimka vyplývající z chyby ve zpracování OLE. Tato třída se používá tak, že kontejnery a servery.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

