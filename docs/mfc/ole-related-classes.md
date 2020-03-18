---
title: Třídy související s rozhraním OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: dfcc07b3fbd0c5badce8e397f4d52bc7d8d3028c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447602"
---
# <a name="ole-related-classes"></a>Třídy související s rozhraním OLE

Tyto třídy poskytují různé služby, od výjimek až po vstup a výstup souborů.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Slouží k vytváření položek, pokud se požadují z jiných kontejnerů. Tato třída slouží jako základní třída pro více specifických typů továrn, včetně `COleTemplateServer`.

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Používá se ke správě souběžnosti s nezjednodušenými vzdálenými procedurami volání OLE (LRPC).

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
K poskytnutí `CFile` přístupu ke složeným souborům používá `IStream` rozhraní COM. Tato třída (odvozená z `CFile`) umožňuje serializaci knihovny MFC k použití strukturovaného úložiště OLE.

[CRectTracker –](../mfc/reference/crecttracker-class.md)<br/>
Slouží k povolení přesouvání, změny velikosti a přeorientaci místních položek.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
