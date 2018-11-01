---
title: Závažná chyba nástroje NMAKE U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 3b1df28e3cd7b27a9e7a130d9d71c1af68db9aec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445237"
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