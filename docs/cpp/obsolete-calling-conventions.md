---
title: Zastaralé konvence volání
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188555"
---
# <a name="obsolete-calling-conventions"></a>Zastaralé konvence volání

**Specifické pro společnost Microsoft**

Konvence volání **__pascal**, **__fortran**a **__syscall** již nejsou podporovány. Jejich funkce lze simulovat pomocí jedné z podporovaných konvencí volání a vhodné možnosti linkeru.

\<Windows. h > teď podporuje makro WINAPI, které se překládá na příslušnou konvenci volání pro cíl. Použijte WINAPI, kde jste dříve použili PASCAL nebo **__far \__pascal**.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)
