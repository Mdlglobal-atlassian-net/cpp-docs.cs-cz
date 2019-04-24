---
title: Třídy dokumentů
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: a7034a99bfefe8f4c11cdf8f99dc4b0c31fac10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219792"
---
# <a name="document-classes"></a>Třídy dokumentů

Objekty třídy dokumentu, vytvořené objekty šablony dokumentu, spravovat data aplikace. Třída pro dokumenty odvodí z jednoho z těchto tříd.

Objekty třídy dokumentu pracovat s objekty zobrazení. Zobrazit objekty představují klientské oblasti okna, zobrazení dat dokumentu a mít uživatelé povolenou interakci s ní. Dokumenty a zobrazeními vytvořila objekt šablony dokumentu.

[CDocument](../mfc/reference/cdocument-class.md)<br/>
Základní třída pro dokumenty specifické pro aplikaci. Odvození dokumentové třídy nebo třídy z `CDocument`.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Používá se pro implementaci složeného dokumentu, jakož i podpora základní kontejnerů. Slouží jako kontejner pro třídy odvozené z [cdocitem –](../mfc/reference/cdocitem-class.md). Tato třída slouží jako základní třída pro kontejner dokumentů a je základní třídou pro `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Třída odvozená z `COleDocument` , který poskytuje infrastrukturu pro propojení. Třídy dokumentů by měl být odvozen pro vaše aplikace typu kontejner z této třídy místo z `COleDocument` Pokud chcete, aby podporovaly odkazy na vložené objekty.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Udržuje seznam klientské položky OLE, které jsou v ovládacím prvku RichEdit. Použít s [cricheditview –](../mfc/reference/cricheditview-class.md) a [cricheditcntritem –](../mfc/reference/cricheditcntritem-class.md).

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Použít jako základní třída pro třídy dokumentu serverová aplikace. `COleServerDoc` objekty poskytují hromadné podpora serveru prostřednictvím interakce s [odvozenou třídu COleServerItem](../mfc/reference/coleserveritem-class.md) objekty. Vizuální úpravy funkce je poskytována architekturu document/view knihovny tříd pomocí.

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
Poskytuje, s [CHtmlEditView](../mfc/reference/chtmleditview-class.md), funkce úprav platformy WebBrowser HTML v rámci kontextu architektury zobrazení dokumentu MFC.

## <a name="related-classes"></a>Související třídy

Objekty třídy dokumentu může být trvalé – jinými slovy, můžete zapsat do úložiště média jejich stav a číst zpět. Knihovna MFC poskytuje `CArchive` třída usnadňuje přenášení dat dokumentu do úložiště média.

[CArchive](../mfc/reference/carchive-class.md)<br/>
Spolupracuje s [cfile –](../mfc/reference/cfile-class.md) objektu pro implementaci trvalého úložiště pro objekty prostřednictvím serializace (viz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

Dokumenty mohou také obsahovat objekty OLE. `CDocItem` je základní třídou položek serveru a klienta.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstraktní základní třída [COleClientItem](../mfc/reference/coleclientitem-class.md) a [odvozenou třídu COleServerItem](../mfc/reference/coleserveritem-class.md). Objekty tříd odvozených z `CDocItem` představují části dokumentů.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
