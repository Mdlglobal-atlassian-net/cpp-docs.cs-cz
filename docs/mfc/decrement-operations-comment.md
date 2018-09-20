---
title: --Komentář k operacím | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73c4a7a70c9f2ed987337426793bd462c2a94309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372493"
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

