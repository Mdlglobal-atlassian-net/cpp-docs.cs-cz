---
title: Třídy související s rozhraním OLE | Dokumentace Microsoftu
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
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43dadaa4aaefa677106710d1adbcdf0e60be59d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411310"
---
# <a name="ole-related-classes"></a>Třídy související s rozhraním OLE

Tyto třídy poskytují celou řadou různých služeb, od výjimky pro vstup a výstup souborů.

[COleObjectFactory –](../mfc/reference/coleobjectfactory-class.md)<br/>
Umožňuje vytvořit položky při požadavku na z jiných kontejnerů. Tato třída slouží jako základní třída pro konkrétnější typy objektů pro vytváření, včetně `COleTemplateServer`.

[Colemessagefilter –](../mfc/reference/colemessagefilter-class.md)<br/>
Použít ke správě souběžnosti s OLE Lightweight vzdálené procedury volání (LRPC).

[Colestreamfile –](../mfc/reference/colestreamfile-class.md)<br/>
Používá COM `IStream` rozhraní k poskytování `CFile` přístup k složené soubory. Tato třída (odvozený od `CFile`) umožňuje MFC serializace za účelem použití OLE strukturované úložiště.

[Crecttracker –](../mfc/reference/crecttracker-class.md)<br/>
Používá k přesunutí, změna velikosti a přesměrování na místě položek.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

