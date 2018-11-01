---
title: --Komentář ke konstruktorům
ms.date: 11/04/2016
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
ms.openlocfilehash: ee36ad991f2a19211b494010d6ff0a5338b80557
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480701"
---
# <a name="-constructors-comment"></a>// Komentář ke konstruktorům

`// Constructors` Části deklarace třídy knihovny MFC deklaruje konstruktory (ve smyslu C++), stejně jako všechny funkce inicializace vyžaduje k opravdu pomocí objektu. Například `CWnd::Create` je v části konstruktory, protože před použitím `CWnd` objektu, se musí být "plně zkonstruovaný" nejdřív voláním konstruktoru C++ a následným voláním `Create` funkce. Tyto členy jsou obvykle veřejné.

Například třída `CStdioFile` tři konstruktory, z nichž jeden je uveden v seznamu pod [příklad, komentáře](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Viz také

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[/ / Implementační komentář](../mfc/decrement-implementation-comment.md)<br/>
[Komentář k atributům](../mfc/decrement-attributes-comment.md)<br/>
[Komentář k operacím](../mfc/decrement-operations-comment.md)<br/>
[Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

