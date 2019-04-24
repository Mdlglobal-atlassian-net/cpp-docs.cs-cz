---
title: --Komentář k atributům
ms.date: 11/04/2016
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
ms.openlocfilehash: a74d0f9d6ffb0bd2d057cf46f7308d8b6a81f98c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241497"
---
# <a name="-attributes-comment"></a>// Komentář k atributům

`// Attributes` Deklarace třídy knihovny MFC obsahuje veřejné atributy (nebo vlastností) objektu. Obvykle se jedná členské proměnné nebo funkce Get/Set. Funkce "Get" a "Set" může nebo nemusí být virtuální. Funkce "Get" jsou obvykle **const**, protože ve většině případů nemají vedlejší účinky. Tyto členy jsou obvykle veřejné; atributy chráněného a privátní se většinou nacházejí v oddílu implementace.

V ukázce výpis z třídy `CStdioFile`v části [příklad, komentáře](../mfc/an-example-of-the-comments.md), seznam obsahuje jednu členskou proměnnou *m_pStream*. Třída `CDC` uvádí skoro 20 členové pod tento komentář.

> [!NOTE]
>  Velké třídy, jako například `CDC` a `CWnd`, může mít mnoho členů, které jednoduše výpis všechny atributy v jedné skupině nepřispěl k vyšší moc k nejasnostem. V takových případech knihovny tříd pomocí jiných komentáře jako záhlaví další od sebe odděluje členy. Například `CDC` používá `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`a provádění dalších akcí. Skupiny, které reprezentují atributy bude následovat běžné syntaxi popsané výše. Mnoho OLE – třídy mají implementaci části `// Interface Maps`.

## <a name="see-also"></a>Viz také:

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Příklad komentářů](../mfc/an-example-of-the-comments.md)<br/>
[/ / Implementační komentář](../mfc/decrement-implementation-comment.md)<br/>
[/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)<br/>
[Komentář k operacím](../mfc/decrement-operations-comment.md)<br/>
[Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)
