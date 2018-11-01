---
title: Přetížení zabezpečení šablony
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: a1747102b53febfe20b76d6de05e71d5b19aad19
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603538"
---
# <a name="secure-template-overloads"></a>Přetížení zabezpečení šablony

Microsoft má zastaralé mnoho funkcí C Runtime knihovny (CRT) a verze se zdokonaleným zabezpečením. Například `strcpy_s` je bezpečnější náhradou `strcpy`. Zastaralé funkce jsou běžné zdroje chyb zabezpečení, protože nebrání operace, které můžete přepsat paměti. Ve výchozím nastavení kompilátor vytvoří upozornění zastarání při použití jedné z těchto funkcí. CRT poskytuje C++ přetížení šablon pro tyto funkce, abychom vám přechod na bezpečnější variant.

Například tento fragment kódu vygeneruje upozornění, protože `strcpy` je zastaralý:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Upozornění na vyřazení existuje říct, že váš kód může nebezpečné. Pokud jste ověřili, že váš kód nelze přepsat paměti, máte několik možností. Můžete rozhodnout ignorovat upozornění, můžete definovat symbol `_CRT_SECURE_NO_WARNINGS` před příkazy include pro CRT záhlaví pro potlačení varování, nebo můžete aktualizovat kód Refaktorovat pro použití `strcpy_s`:

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Přetížení šablon poskytují další možnosti. Pokud definujete `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` na hodnotu 1, díky přetížení šablon standardní funkce CRT, které automaticky volají bezpečnější variant. Pokud `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je 1, pak nejsou potřebné žádné změny kódu. Na pozadí, volání `strcpy` se změní na volání `strcpy_s` s argumentem velikosti automaticky zadané.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` neovlivňuje funkcí, které přijímají počet, jako například `strncpy`. Chcete-li povolit přetížení šablon pro funkce count, definujte `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` na hodnotu 1. Než tak učiníte, ale ujistěte se, že váš kód předá počet znaků, nikoli velikost vyrovnávací paměti (častou). Kromě toho kód, který explicitně zapíše null zakončení na konci vyrovnávací paměť po volání funkce je nutný, pokud se nazývá zabezpečené variant. Pokud potřebujete zkrácení chování, přečtěte si [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
>  Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` vyžaduje, aby `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je také definováno jako 1. Pokud `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` je definována jako 1 a `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je definováno jako 0, aplikace nebude provádět žádné přetížení šablon.

Při definování `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` na hodnotu 1, umožňuje přetížení šablon zabezpečené variant (jména končící na "_Malá"). V takovém případě pokud `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` je 1, pak jeden menší změnu, třeba do původního kódu:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Název funkce je potřeba změnit (tak, že přidáte "_Malá"); šablony přetížení se postará o poskytování velikost argumentu.

Ve výchozím nastavení `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` a `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` jsou definované jako 0 (zakázáno) a `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` je definována jako 1 (povoleno).

Všimněte si, že tyto šablony přetížení funkční pouze pro statické pole. Dynamicky přidělené vyrovnávací paměti vyžadovat změny další zdrojového kódu. Přehodnocení výše uvedených příkladech:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; you have to change it to
                       // strcpy_s(szBuf, 10, "test");
```

A to:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>Viz také

[Funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)