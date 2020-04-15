---
title: Vlastnosti linkeru (Linux C++)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 934e639199d663cba391c9913b067f32e5e32165
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441280"
---
# <a name="linker-properties-linux-c"></a>Vlastnosti linkeru (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Obecné

| Vlastnost | Popis | Choices |
|--|--|--|
| Výstupní soubor | Tato možnost přepíše výchozí název a umístění programu, který propojovací program vytvoří. (-o) |
| Zobrazit průběh | Vytiskne zprávy o průběhu propojovacího programu. |
| Version | Možnost -version říká propojovacímu programu umístit číslo verze do záhlaví spustitelného souboru. |
| Povolit podrobný výstup | -verbose možnost informuje propojovací ho výstupu podrobné zprávy pro ladění. |
| Trasování | Volba --trace informuje propojovací zařízení k výstupu vstupních souborů tak, jak jsou zpracovány. |
| Vektorové symboly | Vytiskněte seznam souborů, ve kterých se symbol zobrazí. (--trace-symbol=symbol) |
| Vytisknout mapu | Volba --print-map informuje propojovací zařízení k výstupu mapy propojení. |
| Nahlásit nevyřešené odkazy na symboly | Tato možnost, pokud je povolena, bude vykazovat nevyřešené odkazy na symboly. |
| Optimalizovat pro využití paměti | Optimalizujte využití paměti podle potřeby opětovným čtením tabulek symbolů. |
| Cesta hledání sdílené knihovny | Umožňuje uživateli naplnit cestu hledání sdílené knihovny. (-rpath-link=cesta) |
| Další adresáře knihovny | Umožňuje uživateli přepsat cestu knihovny prostředí. (-L). |
| Linker | Určuje program, který má být vyvolán během propojení, nebo cestu k propojovacímu programu ve vzdáleném systému. |
| Časový čas propojení | Časový rozsah vzdáleného propojení v milisekundách. |
| Kopírovat výstup | Určuje, zda se má zkopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače. |

## <a name="input"></a>Vstup

| Vlastnost | Popis | Choices |
|--|--|--|
| Ignorovat konkrétní výchozí knihovny | Určuje jeden nebo více názvů výchozích knihoven, které chcete ignorovat. (--exclude-libs lib,lib) |
| Ignorovat výchozí knihovny | Ignorujte výchozí knihovny a pouze explicitně zadané knihovny pro vyhledávání. |
| Vynutit nedefinované odkazy na symboly | Vynutit zadání symbolu do výstupního souboru jako nedefinovaný symbol. (-u symbol --undefined=symbol) |
| Závislosti knihovny | Tato možnost umožňuje zadat další knihovny, které mají být přidány do příkazového řádku linkeru. Další knihovna bude přidána na konec příkazového řádku linkeru s předponou "lib" a zakončena příponou '.a'.  (-lFILE) |
| Další závislosti | Určuje další položky, které mají být přidejte do příkazového řádku propojení. |

## <a name="debugging"></a>Ladění

| Vlastnost | Popis | Choices |
|--|--|--|
| Informace o symbolu ladicího programu | Informace o symbolu ladicího programu z výstupního souboru. | **Zahrnout vše**<br>**Vynechat pouze informace o symbolu ladicího programu**<br>**Vynechat všechny informace o symbolech**<br> |
| Název mapového souboru | Možnost Mapovat informuje propojovací systém k vytvoření souboru mapy s uživatelským jménem. (-Mapa=) |

## <a name="advanced"></a>Upřesňující

| Vlastnost | Popis | Choices |
|--|--|--|
| Označit proměnné jen pro čtení po přemístění | Tato možnost označí proměnné jen pro čtení po přemístění. |
| Povolit okamžitou vazbu funkcí | Tato možnost označí objekt pro okamžitou vazbu funkce. |
| Nevyžadovat spustitelný zásobník | Tato možnost označí výstup jako nevyžadující spustitelný zásobník. |
| Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí. |

::: moniker-end
