---
title: Třídy související s rozhraním OLE | Microsoft Docs
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
ms.openlocfilehash: baa4ec3de21ce91e0d8723ad0e4debb39a26b3cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348512"
---
# <a name="ole-related-classes"></a>Třídy související s rozhraním OLE
Tyto třídy poskytují několik různých služeb, od výjimky do souboru vstup a výstup.  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 Použít k vytvoření položky vyžádání z jiných kontejnerů. Tato třída slouží jako základní třída pro další specifické typy objektů Factory, včetně `COleTemplateServer`.  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 Používá ke správě souběžnosti s OLE Lightweight vzdálené procedury volání (LRPC).  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Používá modelu COM `IStream` rozhraní zajistit `CFile` přístup k složené soubory. Tato třída (odvozený z `CFile`) umožňuje MFC serializace používání OLE strukturovaná úložiště.  
  
 [Crecttracker –](../mfc/reference/crecttracker-class.md)  
 Použít pro povolení přesunutí, změny velikosti a přesměrování na místě položky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

