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
ms.openlocfilehash: e0d02af016a0c7bfb0869b7cdd30fe0db2975102
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265805"
---
# <a name="-constructors-comment"></a>// Komentář ke konstruktorům

`// Constructors` Části deklarace třídy knihovny MFC deklaruje konstruktory (ve smyslu C++), stejně jako všechny funkce inicializace vyžaduje k opravdu pomocí objektu. Například `CWnd::Create` je v části konstruktory, protože před použitím `CWnd` objektu, se musí být "plně zkonstruovaný" nejdřív voláním konstruktoru C++ a následným voláním `Create` funkce. Tyto členy jsou obvykle veřejné.

Například třída `CStdioFile` tři konstruktory, z nichž jeden je uveden v seznamu pod [příklad, komentáře](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Viz také:

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[/ / Implementační komentář](../mfc/decrement-implementation-comment.md)<br/>
[Komentář k atributům](../mfc/decrement-attributes-comment.md)<br/>
[Komentář k operacím](../mfc/decrement-operations-comment.md)<br/>
[Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)
