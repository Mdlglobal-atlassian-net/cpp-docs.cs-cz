---
title: --Implementační komentář
ms.date: 11/04/2016
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
ms.openlocfilehash: 377997b66c5b9c005d1e1bee24890b756621b672
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240734"
---
# <a name="-implementation-comment"></a>// implementační komentář

`// Implementation` Oddíl je nejdůležitější část všechny deklarace tříd knihovny MFC.

V této části jsou uloženy všechny podrobnosti implementace. Členské proměnné a členské funkce mohou objevit v této části. Všechno pod tímto řádkem může změnit v budoucí verzi knihovny MFC. Pokud se nemůžete vyhnout, neměli byste tedy spoléhat na podrobnosti níže `// Implementation` řádku. Kromě toho nejsou uvedené členy deklarované pod řádkem implementace, i když některé implementace je podrobněji popsána technické poznámky. Přepsání virtuální funkce základní třídy se nacházejí v této části, bez ohledu na to, jaké části funkci základní třídy je definován v, protože skutečnost, že funkce přepíše implementaci základní třídy je považován za podrobnost implementace. Obvykle jsou chráněné tyto členy, ale ne vždy.

Všimněte si, že z `CStdioFile` výpis pod [příklad, komentáře](../mfc/an-example-of-the-comments.md) , že členy deklarované níže `// Implementation` komentář mohou být deklarovány jako **veřejné**, **chráněné**, nebo **privátní**. Tito členové by měl pouze používejte opatrně, protože může v budoucnu změnit. Deklarace skupiny členy jako **veřejné** mohou být nezbytné pro implementaci třídy knihovny fungovat správně. Ale to neznamená, že členy deklarované tak může bezpečně použít.

> [!NOTE]
>  Může být pro vás komentáře zbývající typy nad nebo pod `// Implementation` komentář. V obou případech se popisují typy členy deklarované pod nimi. Pokud se objeví pod `// Implementation` přidá komentář, byste měli předpokládat, že členové mohou v budoucnu měnit verze knihovny MFC.

## <a name="see-also"></a>Viz také:

[Použití zdrojových souborů MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Příklad komentářů](../mfc/an-example-of-the-comments.md)<br/>
[/ Komentář ke konstruktorům](../mfc/decrement-constructors-comment.md)<br/>
[Komentář k atributům](../mfc/decrement-attributes-comment.md)<br/>
[Komentář k operacím](../mfc/decrement-operations-comment.md)<br/>
[Komentář k Přepisovatelným](../mfc/decrement-overridables-comment.md)
