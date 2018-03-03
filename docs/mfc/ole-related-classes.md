---
title: "Třídy související s rozhraním OLE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4cb40e237eb6197dfe7e0cf944f12d25ca0e28e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

