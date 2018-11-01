---
title: Použití zdrojových souborů MFC
ms.date: 11/04/2016
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: 40decb64914167061f6538df36d086347f52e1b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659287"
---
# <a name="using-the-mfc-source-files"></a>Použití zdrojových souborů MFC

Knihovny Microsoft Foundation Class (MFC) poskytuje úplný zdrojový kód. Soubory hlaviček (.h) jsou v adresáři \atlmfc\include. implementace soubory (.cpp) jsou v adresáři \atlmfc\src\mfc.

Tato řada článků popisuje konvence, které knihovna MFC používá vyjádřit různé části každá třída významu těchto komentářů a co byste měli očekávat v každé části. Průvodce Visual C++ používá podobné konvence pro třídy, které vytvoří za vás a pravděpodobně zjistíte Tato konvence užitečné pro váš vlastní kód.

Se mohli seznámit **veřejné**, **chráněné**, a **privátní** klíčová slova jazyka C++. Při hledání v souborech hlaviček knihovny MFC, zjistíte, že každá třída může mít několik každý z těchto. Například veřejné členské proměnné a funkce mohou být v rámci více než jednoho **veřejné** – klíčové slovo. Je to proto MFC odděluje členské proměnné a funkce založené na jejich použití, ne podle typu přístup povolený. Knihovna MFC používá **privátní** střídmě; i položky považovány za podrobnosti implementace jsou obecně chráněné a v mnoha případech jsou veřejné. I když se nedoporučuje přístup k podrobnosti implementace, MFC ponechá rozhodnutí pro vás.

Ve zdrojových souborech MFC a soubory, které vytvoří Průvodce aplikací MFC zjistíte komentáře obdobné uvnitř deklarací třídy (obvykle v tomto pořadí):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Obsahuje následující témata v této řadě článků:

- [Příklad komentářů](../mfc/an-example-of-the-comments.md)

- [/ / Komentář k implementaci](../mfc/decrement-implementation-comment.md)

- [/ / Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)

- [/ / Atributy komentář](../mfc/decrement-attributes-comment.md)

- [/ / Komentář k operacím](../mfc/decrement-operations-comment.md)

- [/ / Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)

