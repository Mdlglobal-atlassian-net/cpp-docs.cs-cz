---
title: --Komentář k operacím
ms.date: 11/04/2016
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
ms.openlocfilehash: 6b84da721bd22723d0eb5a0b520462cd8a4613e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653192"
---
# <a name="-operations-comment"></a>// Komentář k operacím

`// Operations` Část deklarace třídy knihovny MFC obsahuje členské funkce, které můžete volat na objekt, který chcete usnadnit všechno nebo provádět akce (provádět operace). Tyto funkce jsou obvykle non -**const** protože obvykle mají vedlejší účinky. Mohou být virtuální i nevirtuální podle potřeb třídy. Tyto členy jsou obvykle veřejné.

V ukázce výpis z třídy `CStdioFile`v [příklad, komentáře](../mfc/an-example-of-the-comments.md), seznam obsahuje dva členské funkce v rámci tento komentář: `ReadString` a `WriteString`.

Stejně jako u atributů, může být dále rozdělená operace.

## <a name="see-also"></a>Viz také

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Příklad komentářů](../mfc/an-example-of-the-comments.md)<br/>
[/ / Implementační komentář](../mfc/decrement-implementation-comment.md)<br/>
[/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)<br/>
[Komentář k atributům](../mfc/decrement-attributes-comment.md)<br/>
[Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

