---
title: --/ Komentář ke konstruktorům | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f03a65c3f870b1e7648f03b70efe7242c35a21f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429352"
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

