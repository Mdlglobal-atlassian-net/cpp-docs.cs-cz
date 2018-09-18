---
title: Závažná chyba nástroje NMAKE U1033 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7492e5fd77f8e88b2191174f84c298c6166d8d89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066375"
---
# <a name="nmake-fatal-error-u1033"></a>Závažná chyba nástroje NMAKE U1033

Chyba syntaxe: "string" neočekávaný

Řetězec není součástí platné syntaxe souboru pravidel.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Pokud uzavírací nastavit ostrých závorek (**<<**) pro vloženého souboru nejsou na začátku řádku, dojde k následující chybě:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Pokud definice makra v souboru pravidel obsažené znaménko rovná se (**=**) bez předchozí název nebo pokud definovaného názvu je makro, které se rozbaluje prázdné, dojde k následující chybě:

    ```
    syntax error : '=' unexpected
    ```

1. Pokud středník (**;**) na řádku komentář v NÁSTROJÍCH. INI není na začátku řádku, dojde k následující chybě:

    ```
    syntax error : ';' unexpected
    ```

1. Pokud soubor pravidel je formátován pomocí textového editoru, může dojít k následující chybě:

    ```
    syntax error : ':' unexpected
    ```