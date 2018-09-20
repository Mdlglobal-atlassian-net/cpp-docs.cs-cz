---
title: --Komentář k Přepisovatelným | Dokumentace Microsoftu
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
ms.openlocfilehash: d50fb62767f2130e89cb75df5d66f8c18ce2a097
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428054"
---
# <a name="-overridables-comment"></a>// Komentář k přepisovatelným

`// Overridables` Část deklarace třídy knihovny MFC obsahuje virtuální funkce, které můžete přepsat v odvozené třídě. Pokud chcete změnit chování základní třídy. Jsou obvykle nazývají počínaje "On", přestože to není nezbytně nutné. Funkce Zde jsou navrženy k přepsat a často implementovat nebo zadejte nějaký druh "zpětné volání" nebo "připojení". Obvykle jsou chráněny těchto členů.

V prostředí MFC sama jsou čistě virtuální funkce vždy umístěny v této části. Čistě virtuální funkce v jazyce C++ je jedním z formuláře:

`virtual void OnDraw( ) = 0;`

V ukázce výpis z třídy `CStdioFile`v [příklad, komentáře](../mfc/an-example-of-the-comments.md), patří k přepisovatelným oddíl. Třída `CDocument`, na druhé straně jsou uvedeny přibližně 10 přepisovatelné členské funkce.

V některých tříd, může se zobrazit také komentáře `// Advanced Overridables`. Toto jsou funkce, které pouze rozšířené programátoři má pokusit o přepsání. Musíte se pravděpodobně nikdy k jejich přepsání.

> [!NOTE]
>  Konvence popsaných v tomto článku je možné použít také, obecně pro Automation (dříve označované jako automatizace OLE) metody a vlastnosti. Automatizace metody jsou podobné operacím knihovny MFC. Vlastnosti automatizace se podobají atributy knihovny MFC. Přepisovatelné členské funkce MFC podobají událostí automatizace (podporovaných pro ovládací prvky ActiveX, dřív označované jako ovládací prvky OLE).

## <a name="see-also"></a>Viz také

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Příklad komentářů](../mfc/an-example-of-the-comments.md)<br/>
[/ / Implementační komentář](../mfc/decrement-implementation-comment.md)<br/>
[/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)<br/>
[Komentář k atributům](../mfc/decrement-attributes-comment.md)<br/>
[Komentář k operacím](../mfc/decrement-operations-comment.md)

