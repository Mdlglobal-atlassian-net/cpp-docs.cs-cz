---
title: Chyba při vyhodnocování výrazu CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 61646462eeba4918a4993b23f7f4b394083296ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195887"
---
# <a name="expression-evaluator-error-cxx0019"></a>Chyba při vyhodnocování výrazu CXX0019

chybné přetypování typu

Vyhodnocovací filtr výrazů jazyka C nemůže provést přetypování typu jako zapsaného.

Tato chyba je shodná s CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Zadaný typ není znám.

1. Existuje příliš mnoho úrovní typů ukazatelů. Například přetypování typu

    ```
    (char **)h_message
    ```

   nelze vyhodnotit pomocí vyhodnocení výrazu C.
