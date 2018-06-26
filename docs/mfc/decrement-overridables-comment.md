---
title: – Komentář k Přepisovatelným | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a1b9b04647717fc5892421f2b45947ebd079a0c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928724"
---
# <a name="-overridables-comment"></a>// Komentář k přepisovatelným
`// Overridables` Obsahuje deklarace tříd MFC virtuální funkce, které můžete přepsat v odvozené třídě, když potřebujete změnit chování základní třídy. Že jsou obvykle s názvem počínaje "Na", ačkoli to není nezbytně nutné. Funkce tady jsou navrženy pro přepsat a často implementovat nebo zadejte nějaká "zpětného volání" nebo "připojit". Obvykle jsou chráněny tito členové.  
  
 V prostředí MFC samotné jsou vždy umístěny čistý virtuální funkce v této části. Čistou virtuální funkci v jazyce C++ je jedním z formuláře:  
  
 `virtual void OnDraw( ) = 0;`  
  
 V ukázce výpis z třídy `CStdioFile`v [příklad komentářů](../mfc/an-example-of-the-comments.md), seznam obsahuje žádnou část k přepisovatelným. Třída `CDocument`, na druhé straně zobrazí přibližně 10 přepisovatelné členské funkce.  
  
 V některých tříd, může se také zobrazit komentář `// Advanced Overridables`. Toto jsou funkce, které pouze pokročilé programátory pokuste se přepsat. Musíte pravděpodobně nikdy nepřepíšete.  
  
> [!NOTE]
>  Konvence popsané v tomto článku použít také, obecně vlastností a metod automatizace (dříve označované jako automatizace OLE). Automatizace metody jsou podobná MFC operace. Vlastnosti automatizace jsou podobná MFC atributy. Události automatizace (podporuje pro ovládací prvky ActiveX, dřív označované jako ovládací prvky OLE) jsou podobná MFC přepisovatelné členské funkce.  
  
## <a name="see-also"></a>Viz také  
 [Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)   
 [Příklad komentářů](../mfc/an-example-of-the-comments.md)   
 [Implementační komentář](../mfc/decrement-implementation-comment.md)   
 [/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)   
 [Komentář k atributům](../mfc/decrement-attributes-comment.md)   
 [Komentář k operacím](../mfc/decrement-operations-comment.md)

