---
title: Doporučení k výběru mezi funkcemi a makry
ms.date: 11/04/2016
f1_keywords:
- c.functions
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
ms.openlocfilehash: 234fcd8a0439240bc7585414254c5687dcb8f21b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335723"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Doporučení k výběru mezi funkcemi a makry

Většina rutin Microsoft knihovny run-time jsou zkompilovány nebo týkajícím se této funkce, ale některé rutiny jsou implementovány jako makra. Pokud soubor hlaviček deklaruje funkce i makra verzi rutinu, definici makra přednost, vzhledem k tomu, že se zobrazí vždy po deklaraci funkce. Při vyvolání rutinu, která je implementována jako funkce i makra lze vynutit na kompilátoru používat funkce verze dvěma způsoby:

- Uvést název rutiny v závorkách.

    ```C
    #include <ctype.h>
    a = _toupper(a);    // Use macro version of toupper.
    a = (_toupper)(a);  // Force compiler to use
                        // function version of toupper.
    ```

- "Zrušit" definici makra pomocí `#undef` – direktiva:

    ```C
    #include <ctype.h>
    #undef _toupper
    ```

Pokud je potřeba zvolit funkce a makro provádění rutiny knihoven, vezměte v úvahu následující nevýhody:

- **Rychlost a velikost** rychlejší doba provádění je hlavní výhodou použití maker. Během předběžného zpracování provádějí makra rozbalen (podle její definice nahrazená) vložené pokaždé, když se používá. Volat pouze jednou, bez ohledu na to, kolikrát se dojde k definici funkce. Makra může zvýšit velikost kódu, ale nemají režii spojenou s voláním funkcí.

- **Vyhodnocení funkce** funkce vyhodnotí na adresu; makro nepodporuje. V kontextech, které vyžadují ukazatele proto nelze použít název makra. Například je možné deklarovat ukazatel na funkci, ale nikoli ukazatel na uživatelské makro.

- **Kontrola typu** při deklaraci funkce kompilátoru můžete zkontrolovat typy argumentů. Protože nelze deklarovat makra, kompilátor nemůže zkontrolovat typy argumentů makra; i když ho můžete zkontrolovat počet argumentů, které můžete předat makra.

## <a name="see-also"></a>Viz také:

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
