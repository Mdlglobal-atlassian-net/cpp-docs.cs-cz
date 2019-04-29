---
title: Komentáře (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: a90d9d37e69cb2e8be4ab18f77026fdce1221307
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399171"
---
# <a name="comments-c"></a>Komentáře (C++)

Komentář je text, který kompilátor ignoruje, ale je užitečný pro programátory. Komentáře se obvykle používají pro popis kódu pro pozdější použití. Kompilátor je zpracovává jako prázdné znaky. Můžete použít komentáře při testování nastavit některé řádky kódu jako neaktivní; ale `#if` / `#endif` direktivy preprocesoru fungují lépe, protože je možné ohraničit kód, který obsahuje komentáře, ale komentáře nelze vnořovat.

Komentář v jazyce C++ je zapsán některým z následujících způsobů:

- Znaky `/*` (lomítko, hvězdička) následované libovolnou posloupností znaků (včetně nových řádků) jsou následovány znaky `*/`. Tato syntaxe je stejná jako standard ANSI C.

- Znaky `//` (dvě lomítka) jsou následovány libovolnou posloupností znaků. Nový řádek, kterému bezprostředně nepředchází zpětné lomítko, ukončí tento typ komentáře. Proto se běžně nazývá „jednořádkový komentář“.

Znaky komentáře (`/*`, `*/` a `//`) nemají žádný zvláštní význam v rámci znakové konstanty, textového literálu ani komentáře. Komentáře zapsané pomocí první syntaxe proto nelze vnořovat.

## <a name="see-also"></a>Viz také:

[Lexikální konvence](../cpp/lexical-conventions.md)