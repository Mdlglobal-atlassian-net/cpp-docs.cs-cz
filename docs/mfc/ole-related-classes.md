---
title: Třídy související s rozhraním OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 7d58072d133b9348558804b848ecfda4497931e1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263764"
---
# <a name="ole-related-classes"></a>Třídy související s rozhraním OLE

Tyto třídy poskytují celou řadou různých služeb, od výjimky pro vstup a výstup souborů.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Umožňuje vytvořit položky při požadavku na z jiných kontejnerů. Tato třída slouží jako základní třída pro konkrétnější typy objektů pro vytváření, včetně `COleTemplateServer`.

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Použít ke správě souběžnosti s OLE Lightweight vzdálené procedury volání (LRPC).

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Používá COM `IStream` rozhraní k poskytování `CFile` přístup k složené soubory. Tato třída (odvozený od `CFile`) umožňuje MFC serializace za účelem použití OLE strukturované úložiště.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Používá k přesunutí, změna velikosti a přesměrování na místě položek.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
