---
title: --Komentář k operacím
ms.date: 11/04/2016
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
ms.openlocfilehash: 7e4d0549d3d77916df532f105dc58ed9e9f78af2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240597"
---
# <a name="-operations-comment"></a>// Komentář k operacím

`// Operations` Část deklarace třídy knihovny MFC obsahuje členské funkce, které můžete volat na objekt, který chcete usnadnit všechno nebo provádět akce (provádět operace). Tyto funkce jsou obvykle non -**const** protože obvykle mají vedlejší účinky. Mohou být virtuální i nevirtuální podle potřeb třídy. Tyto členy jsou obvykle veřejné.

V ukázce výpis z třídy `CStdioFile`v [příklad, komentáře](../mfc/an-example-of-the-comments.md), seznam obsahuje dva členské funkce v rámci tento komentář: `ReadString` a `WriteString`.

Stejně jako u atributů, může být dále rozdělená operace.

## <a name="see-also"></a>Viz také:

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Příklad komentářů](../mfc/an-example-of-the-comments.md)<br/>
[/ / Implementační komentář](../mfc/decrement-implementation-comment.md)<br/>
[/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)<br/>
[Komentář k atributům](../mfc/decrement-attributes-comment.md)<br/>
[Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)
