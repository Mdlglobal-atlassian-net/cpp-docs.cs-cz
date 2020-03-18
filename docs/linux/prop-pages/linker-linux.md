---
title: Vlastnosti linkeru ( C++Linux)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 934e639199d663cba391c9913b067f32e5e32165
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441280"
---
# <a name="linker-properties-linux-c"></a>Vlastnosti linkeru ( C++Linux)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Obecné

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Výstupní soubor | Možnost přepíše výchozí název a umístění programu, který vytvoří linker. (-o) |
| Zobrazit průběh | Zobrazí zprávy o průběhu linkeru. |
| Verze | Možnost-Version dá linkeru pokyn, aby vložil číslo verze do hlavičky spustitelného souboru. |
| Povolit podrobný výstup | Možnost-verbose dá linkeru pokyn, aby výstupem podrobných zpráv pro ladění. |
| Trasování | Možnost--Trace dá linkeru pokyn, aby výstupní vstupní soubory vypracovaly. |
| Symboly trasování | Vytiskne seznam souborů, ve kterých se zobrazí symbol. (--Trace-symbol = symbol) |
| Tisk mapy | Možnost--Print-map dá linkeru pokyn, aby vytiskl mapu odkazů. |
| Oznamovat nevyřešené odkazy na symboly | Tato možnost, pokud je povolená, bude hlásit nevyřešené odkazy na symboly. |
| Optimalizovat využití paměti | Optimalizuje využití paměti přečtením tabulek symbolů podle potřeby. |
| Cesta pro hledání sdílené knihovny | Umožňuje uživateli naplnit cestu pro hledání ve sdílené knihovně. (-rpath-Link = cesta) |
| Další adresáře knihoven | Umožňuje uživateli přepsat cestu ke knihovně prostředí. (-L složka). |
| Linker | Určuje program, který se má volat během propojování, nebo cestu k linkeru ve vzdáleném systému. |
| Časový limit propojení | Časový limit vzdáleného propojování v milisekundách. |
| Kopírovat výstup | Určuje, zda se má kopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače. |

## <a name="input"></a>Vstup

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Ignorovat specifické výchozí knihovny | Určuje jeden nebo více názvů výchozích knihoven, které se mají ignorovat. (--Exclude-knihovny LIB, lib) |
| Ignorovat výchozí knihovny | Ignoruje výchozí knihovny a explicitně zadáte jenom knihovny hledání. |
| Vynutit nedefinované odkazy na symboly | Vynutí zadání symbolu do výstupního souboru jako nedefinovaného symbolu. (-u symbol--undefined = symbol) |
| Závislosti knihoven | Tato možnost umožňuje zadat další knihovny, které mají být přidány do příkazového řádku linkeru. Další knihovna bude přidána na konec příkazového řádku linkeru s předponou lib a končit příponou. a.  (-lFILE) |
| Další závislosti | Určuje další položky, které se mají přidat do příkazového řádku propojení. |

## <a name="debugging"></a>Ladění

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Informace o symbolech ladicího programu | Informace o symbolech ladicího programu z výstupního souboru. | **Zahrnout vše**<br>**Vynechat jenom informace o symbolech ladicího programu**<br>**Vynechat všechny informace o symbolech**<br> |
| Název souboru mapy | Možnost map dá linkeru pokyn, aby vytvořil soubor mapy se zadaným uživatelským jménem. (-Map =) |

## <a name="advanced"></a>Upřesňující

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Označit proměnné jen pro čtení po přemístění | Tato možnost označí proměnné po přemístění jen pro čtení. |
| Povolit okamžitou vazbu funkcí | Tato možnost označí objekt pro okamžité vázání funkcí. |
| Nevyžadovat spustitelný zásobník | Tato možnost označuje výstup, který nevyžaduje spustitelný zásobník. |
| Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí. |

::: moniker-end
