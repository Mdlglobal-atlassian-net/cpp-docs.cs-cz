---
title: Null – příkaz
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
ms.openlocfilehash: 167a1e579c15fd59da1979efd9aa979184318115
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177804"
---
# <a name="null-statement"></a>Null – příkaz

"Příkaz null" je příkaz výrazu s chybějícím *výrazem* . Je užitečný, když syntaxe jazyka vyžaduje výraz, ale žádné vyhodnocení výrazu. Skládá se ze středníku.

Příkazy null se obvykle používají jako zástupné symboly v příkazech iterace nebo jako příkazy, na které chcete umístit popisky na konci složených příkazů nebo funkcí.

Následující fragment kódu ukazuje, jak zkopírovat jeden řetězec do druhého a zahrnuje příkaz null:

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>Viz také

[Příkaz výrazu](../cpp/expression-statement.md)
