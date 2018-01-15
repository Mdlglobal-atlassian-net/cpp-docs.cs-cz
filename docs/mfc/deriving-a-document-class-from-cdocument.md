---
title: "Odvození dokumentové třídy z objektu CDocument | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e5c128a2a2e32b5e4854725354ed484a335ab0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deriving-a-document-class-from-cdocument"></a>Odvození dokumentové třídy z objektu CDocument
Dokumenty obsahují a spravovat data aplikace. Použití třídy Průvodce aplikací knihovny MFC zadaný dokument, postupujte takto:  
  
-   Odvození třídy z **CDocument** pro každý typ dokumentu.  
  
-   Přidání členské proměnné k ukládání dat pro každý dokument.  
  
-   Přepsání **CDocument**na `Serialize` členské funkce ve třídě dokumentů. `Serialize`zapíše a čte data dokumentu do a z disku.  
  
## <a name="other-document-functions-often-overridden"></a>Často přepisované funkce jiných dokumentu  
 Můžete také přepsat dalších **CDocument** členské funkce. Konkrétně je často nutné přepsat [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) a [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) k chybě při inicializaci dokumentu datové členy a [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) zrušení dynamicky přidělené data. Informace o přepisovatelné členy najdete v tématu třídy [CDocument](../mfc/reference/cdocument-class.md) v *odkaz knihovny MFC*.  
  
## <a name="see-also"></a>Viz také  
 [Použití dokumentů](../mfc/using-documents.md)

