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
ms.openlocfilehash: 6f23f792f750e4352494bf3e4bde08f0fe360439
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980494"
---
# <a name="using-the-mfc-source-files"></a>Použití zdrojových souborů MFC

Knihovna Microsoft Foundation Class (MFC) poskytuje úplný zdrojový kód. Soubory hlaviček (. h) jsou v adresáři \atlmfc\include; implementační soubory (. cpp) jsou v adresáři \atlmfc\src\mfc.

Tato rodina článků vysvětluje konvence, které knihovna MFC používá ke komentování různých částí každé třídy, co tyto komentáře znamenají a co byste měli očekávat v jednotlivých oddílech. Vizuální C++ průvodci používají podobné konvence pro třídy, které vytvoří za vás, a pravděpodobně budete chtít, aby tyto konvence byly užitečné pro vlastní kód.

Můžete znát klíčová slova **Public**, **Protected**a **Private** C++ . V hlavičkových souborech knihovny MFC najdete každou třídu, která může mít několik z nich. Například veřejné proměnné členů a funkce mohou být ve více než jednom klíčovém slově **Public** . Je to proto, že knihovna MFC odděluje členské proměnné a funkce na základě jejich použití, nikoli podle typu povoleného přístupu. MFC používá **soukromě** . Dokonce i položky považované za podrobnosti oimplementaci jsou často chráněny a mnohokrát jsou **veřejné**. I když se přístup k podrobnostem implementace nedoporučuje, knihovna MFC toto rozhodnutí ponechá.

Ve zdrojových souborech knihovny MFC a hlavičkových souborech, které Průvodce aplikací MFC vytvoří, najdete v deklaracích třídy komentáře, jako jsou ty, které jsou v deklaracích tříd (obvykle v tomto pořadí):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Témata zahrnutá v této rodině článků zahrnují:

- [Příklad komentářů](../mfc/an-example-of-the-comments.md)

- [Komentář k implementaci](../mfc/decrement-implementation-comment.md)

- [Komentář k konstruktorům//](../mfc/decrement-constructors-comment.md)

- [Komentář k atributům//](../mfc/decrement-attributes-comment.md)

- [Komentář k operacím](../mfc/decrement-operations-comment.md)

- [Komentář k K přepisovatelným](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Viz také:

[Obecná témata MFC](../mfc/general-mfc-topics.md)
