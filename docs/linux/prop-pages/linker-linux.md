---
title: Vlastnosti linkerů (Linux C++)
ms.date: 9/26/2017
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 2e5c3446d8daeeb052937b5e172fc9fa4b6ad302
ms.sourcegitcommit: d441305fb19131afbd7fc259d8cda63ea26f2343
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678337"
---
# <a name="linker-properties-linux-c"></a>Vlastnosti linkerů (Linux C++)

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní soubor | Tato možnost přepíše výchozí název a umístění programu, který vytvoří linker. (-o).
Zobrazit průběh | Vytiskne zprávy o průběhu Linkeru.
Version | -Version přikáže linkeru, aby vložil číslo verze v záhlaví spustitelného souboru.
Povolit podrobný výstup | -Verbose – možnost dá linkeru pokyn, do výstupu vypisoval podrobné zprávy pro ladění.
Trasování | --Trace možnost přikazuje linkeru, aby se po zpracování výstupu ze vstupních souborů.
Symboly trasování | Vytiskne seznam souborů, ve kterých se objeví symbol. (--trace-symbol = symbol)
Tisknout mapu | --Print-map přikazuje linkeru, výstup v podobě mapy odkazu.
Hlásit nevyřešené odkazy na symboly | Povolení této možnosti budou hlásit nevyřešené odkazy na symboly.
Optimalizovat využití paměti | Optimalizujte využití paměti opětovným čtením tabulek symbolů podle potřeby.
Sdílené cesty pro hledání knihovny | Umožňuje uživateli naplnit cestu hledání sdílené knihovny. (- rpath - link = path)
Další adresáře knihoven | Umožňuje uživateli přepsat cestu ke knihovně prostředí. (-L složka).
Linker | Určuje program, který se má volat během propojování, nebo cestu k linkeru ve vzdáleném systému.
Časový limit propojování | Časový limit vzdáleného propojování, v milisekundách.
Kopírovat výstup | Určuje, jestli se má kopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače.

## <a name="input"></a>Vstup

Vlastnost | Popis | Možnosti
--- | ---| ---
Ignorovat konkrétní výchozí knihovny | Určuje jeden nebo více názvů výchozích knihoven k ignorování. (--exclude-libs lib, lib)
Ignorovat výchozí knihovny | Ignorovat výchozí knihovny a hledá jenom explicitně zadané knihovny.
Vynutit nedefinované odkazy na symboly | Vynutit zapsání symbolu do výstupního souboru jako nedefinovaného symbolu. (- u symbol--undefined = symbol)
Závislé položky knihoven | Tato možnost umožňuje zadat další knihovny, které mají být přidány do příkazového řádku linkeru. Další knihovna bude přidána na konec příkazového řádku linkeru s předponou "lib" a končit příponou ".a".  (-lFILE)
Další závislosti | Určuje další položky pro přidání do příkazového řádku propojení.

## <a name="debugging"></a>Ladění

Vlastnost | Popis | Možnosti
--- | ---| ---
Informace o symbolech ladicího programu | Ladicí program informace o symbolech z výstupního souboru. | **Zahrnout všechny**<br>**Vynechat informace o symbolech ladicího programu pouze**<br>**Vynechat všechny informace o symbolech**<br>
Název souboru mapy | Možnost Map přikazuje linkeru, aby vytvořil soubor mapy s uživatelsky definovaným názvem. (-Map =)

## <a name="advanced"></a>Upřesnit

Vlastnost | Popis | Možnosti
--- | ---| ---
Označit jen pro čtení proměnné po přemístění | Tato možnost označí proměnné jen pro čtení po přemístění.
Povolit okamžité vázání funkcí | Tato možnost označí objekt pro okamžité vázání funkcí.
Nevyžadují žádná spustitelný zásobník | Tato možnost určí, že výstup nevyžaduje spustitelný zásobník.
Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí.
