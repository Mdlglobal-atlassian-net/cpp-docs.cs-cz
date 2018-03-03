---
title: "Záhlaví a zápatí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7525cba7d05c4d04f0548bd2dc774503b284c220
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="headers-and-footers"></a>Záhlaví a zápatí
Tento článek vysvětluje postup přidání záhlaví a zápatí na tištěných dokument.  
  
 Když se podíváte na dokument na obrazovce, název dokumentu a vaše aktuální umístění v dokumentu se obvykle zobrazují v záhlaví okna a stavového řádku. Při vyhledávání na tištěných kopii dokumentu, je užitečné používat název a číslo stránky zobrazí v záhlaví nebo zápatí stránky. Toto je běžným způsobem, ve které WYSIWYG i programy se liší v tom, jak provést tisku a zobrazení na obrazovce.  
  
 [Při tisku](../mfc/reference/cview-class.md#onprint) – členská funkce je na příslušné místo tisknout záhlaví a zápatí stránky, protože je volána pro jednotlivé stránky, a protože je volat pouze pro tisk, ne pro zobrazení na obrazovce. Můžete definovat samostatné funkce Tisknout záhlaví nebo zápatí stránky a předejte ji kontextu zařízení tiskárny z `OnPrint`. Možná budete muset upravit okno původ nebo rozsah před voláním [OnDraw –](../mfc/reference/cview-class.md#ondraw) -li se vyhnout textu stránky překrývají záhlaví nebo zápatí stránky. Budete také muset upravit `OnDraw` vzhledem k tomu může snížit množství dokumentu, který nejlépe odpovídá na stránce.  
  
 Jedním ze způsobů, odpovídajícím způsobem pro oblasti provedenou záhlaví nebo zápatí je použití **m_rectDraw** členem [cprintinfo –](../mfc/reference/cprintinfo-structure.md). Pokaždé, když tisknout, tento člen je inicializován použitelné oblast stránky. Při tisku záhlaví nebo zápatí stránky před tiskem textu stránky, můžete snížit velikost obdélníku uložené v **m_rectDraw** k účtu pro oblast provedenou záhlaví nebo zápatí stránky. Potom `OnPrint` mohou odkazovat na **m_rectDraw** chcete zjistit, kolik oblast zůstane pro tisk textu stránky.  
  
 Nelze tisknout záhlaví, nebo cokoliv jiného, z [onpreparedc –](../mfc/reference/cview-class.md#onpreparedc), protože je volána před provedením `StartPage` členské funkce [CDC](../mfc/reference/cdc-class.md) byla volána. Kontext zařízení tiskárny v tomto bodě se považuje za hranice stránky. Můžete provést pouze z tisk `OnPrint` – členská funkce.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Tisk více dokumentů](../mfc/multipage-documents.md)  
  
-   [Přidělování prostředků GDI pro tisk](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Viz také  
 [Tisk](../mfc/printing.md)

