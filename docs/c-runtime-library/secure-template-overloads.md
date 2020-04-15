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
ms.openlocfilehash: 6dba60b57616a1656b2791958e460f0268eaa7fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361123"
---
# <a name="secure-template-overloads"></a>Přetížení zabezpečení šablony

Společnost Microsoft zastarala mnoho funkcí knihovny C Runtime (CRT) ve prospěch verzí s rozšířeným zabezpečením. Například `strcpy_s` je bezpečnější náhrada `strcpy`za . Zastaralé funkce jsou běžnými zdroji chyb zabezpečení, protože nebrání operacím, které mohou přepsat paměť. Ve výchozím nastavení kompilátor vytvoří upozornění na vyřazení při použití jedné z těchto funkcí. CRT poskytuje přetížení šablony Jazyka C++ pro tyto funkce, které usnadňují přechod na bezpečnější varianty.

Například tento fragment kódu generuje upozornění, `strcpy` protože je zastaralé:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Upozornění na vyřazení je k dispozici, aby vám řekl, že váš kód může být nebezpečné. Pokud jste ověřili, že váš kód nemůže přepsat paměť, máte několik možností. Můžete se rozhodnout ignorovat upozornění, můžete `_CRT_SECURE_NO_WARNINGS` definovat symbol před include příkazy pro hlavičky CRT potlačit upozornění, nebo můžete aktualizovat kód použít `strcpy_s`:

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Přetížení šablony poskytují další možnosti. Pokud definujete `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` na 1, to umožňuje přetížení šablony standardní crt funkce, které volají bezpečnější varianty automaticky. Pokud `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je 1, pak jsou nutné žádné změny kódu. Na pozadí `strcpy` volání změní volání `strcpy_s` s argumentem velikost i s argumentem velikosti, který je zadán automaticky.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` nemá vliv na funkce, které berou `strncpy`počet, například . Chcete-li povolit přetížení šablony `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` pro funkce počítání, definujte na 1. Než tak však učiníte, ujistěte se, že váš kód předává počet znaků, nikoli velikost vyrovnávací paměti (běžná chyba). Také kód, který explicitně zapíše zakončení null na konci vyrovnávací paměti po volání funkce je zbytečné, pokud je volána zabezpečená varianta. Pokud potřebujete zkrácení chování, viz [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
> Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` vyžaduje, `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` aby byl také definován jako 1. Pokud `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` je definován `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 a je definován jako 0, aplikace nebude provádět žádné přetížení šablony.

Když definujete `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` na 1, umožňuje přetížení šablony zabezpečené varianty (názvy končící na "_s"). V tomto případě, pokud `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` je 1, musí být provedena jedna malá změna původního kódu:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Je třeba změnit pouze název funkce (přidáním "_s"); přetížení šablony se postará o poskytnutí argumentu velikosti.

Ve výchozím `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` nastavení a jsou definovány `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` jako 0 (zakázáno) a je definovánjako 1 (povoleno).

Všimněte si, že tyto šablony přetížení pracovat pouze pro statická pole. Dynamicky přidělené vyrovnávací paměti vyžadují další změny zdrojového kódu. Přehodnocení výše uvedených příkladů:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; you have to change it to
                       // strcpy_s(szBuf, 10, "test");
```

A tohle:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>Viz také

[Funkce zabezpečení v crt](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
