---
title: Tisk | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7df782e3c30b9120fe7eb6728f1b622750d160f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348224"
---
# <a name="printing"></a>Tisk
Microsoft Windows implementuje zobrazení nezávislé na zařízení. V prostředí MFC, to znamená, že stejné kreslení volání v `OnDraw` funkce člena třídy zobrazení jsou zodpovědní za kreslení na zobrazení a na jiných zařízení, jako jsou tiskárny. Náhledu tisku cílové zařízení je simulované tiskový výstup do zobrazení.  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Vaše Role v tisku oproti Role rozhraní Framework  
 Zobrazení třídy má následující zodpovědnosti:  
  
-   Informujte rozhraní, kolik stránek se v dokumentu.  
  
-   Pokud budete vyzváni k zadané stránku vytisknout, kreslení část dokumentu.  
  
-   Přidělte a navrátit písem, nebo jiné grafiky zařízení rozhraní GDI prostředky potřebné pro tisk.  
  
-   V případě potřeby odesílat žádné řídicí kódy, které jsou potřebné ke změně režimu tiskárny před tiskem danou stránku, například, chcete-li změnit tisku orientaci na základě stránky.  
  
 Rozhraní framework odpovědnosti jsou následující:  
  
-   Zobrazení **tiskových** dialogové okno.  
  
-   Vytvoření [CDC](../mfc/reference/cdc-class.md) objekt pro tiskárny.  
  
-   Volání [zobrazující](../mfc/reference/cdc-class.md#startdoc) a [EndDoc](../mfc/reference/cdc-class.md#enddoc) členské funkce `CDC` objektu.  
  
-   Opakovaně volání [StartPage](../mfc/reference/cdc-class.md#startpage) členské funkce `CDC` objektu, informujte třídy zobrazení stránky, která má být vytištěn a volání [EndPage](../mfc/reference/cdc-class.md#endpage) členské funkce `CDC` objektu.  
  
-   Volání přepisovatelné funkce v zobrazení v příslušnou dobu.  
  
 Následující články popisují, jak rozhraní podporuje tisku a přehled tisku:  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Jak probíhá výchozí tisk](../mfc/how-default-printing-is-done.md)  
  
-   [Vícestránkové dokumenty](../mfc/multipage-documents.md)  
  
-   [Záhlaví a zápatí](../mfc/headers-and-footers.md)  
  
-   [Přidělování prostředků GDI pro tisk](../mfc/allocating-gdi-resources.md)  
  
-   [Náhled tisku](../mfc/print-preview-architecture.md)  
  
## <a name="see-also"></a>Viz také  
 [Tisk a náhled tisku](../mfc/printing-and-print-preview.md)

