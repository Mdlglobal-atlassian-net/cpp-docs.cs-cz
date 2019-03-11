---
title: Inkrementace a dekrementace ukazatelů
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: cdaee3d13a8ceab47f62100953a0eb6e51bfc255
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746796"
---
# <a name="incrementing-and-decrementing-pointers"></a>Inkrementace a dekrementace ukazatelů

Použijte následující tipy:

- Přejděte na úvodní bajty, ne na druhý bajt. Je obvykle bezpečné s ukazatelem na druhý bajt. Obvykle je bezpečnější kontrolovat řetězec vpřed spíše než v opačném pořadí.

- Existuje funkce Inkrementace a dekrementace ukazatelů a makra, které přesouvají přes celý znak:

    ```cpp
    sz1++;
    ```

   změní:

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   `_mbsinc` a `_mbsdec` funkce správně zvýší a sníží v `character` jednotky, bez ohledu na velikost znaků.

- Sníží musíte ukazatel na začátek řetězce, viz následující příklad:

    ```cpp
    sz2--;
    ```

   změní:

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   Alternativně může být hlavního ukazatele na platný znak v řetězci, tak, aby:

    ```cpp
    sz2Head < sz2
    ```

   Musíte mít ukazatel na známé platné vedoucí bajt.

- Můžete chtít zachovat ukazatel na předchozí znak pro rychlejší volání `_mbsdec`.

## <a name="see-also"></a>Viz také:

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Bajtové indexy](../text/byte-indices.md)
