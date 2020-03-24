---
title: Závažná chyba nástroje NMAKE U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 4511b15c84479c3531a3bea85964e2768de0181f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173384"
---
# <a name="nmake-fatal-error-u1033"></a>Závažná chyba nástroje NMAKE U1033

Chyba syntaxe: Neočekávaný řetězec

Řetězec není součástí platné syntaxe souboru pravidel.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Pokud uzavírací sada lomených závorek ( **<<** ) pro vložený soubor není na začátku řádku, dojde k následující chybě:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Pokud definice makra v souboru pravidel obsahuje symbol rovná se ( **=** ) bez předchozího názvu nebo pokud je definovaný název makro, které se rozšíří na Nothing, dojde k následující chybě:

    ```
    syntax error : '=' unexpected
    ```

1. V případě, že je středník ( **;** ) v řádku poznámky v nástroji. INI není na začátku řádku, dojde k následující chybě:

    ```
    syntax error : ';' unexpected
    ```

1. Pokud byl soubor pravidel zformátován pomocí textového procesoru, může dojít k následující chybě:

    ```
    syntax error : ':' unexpected
    ```
