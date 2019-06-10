---
title: Linker Properties (Linux C++)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 01e8a9e45272ff55db6bbf738b48c75f4e1f6c48
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821290"
---
# <a name="linker-properties-linux-c"></a>Linker Properties (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní soubor | Tato možnost přepíše výchozí název a umístění programu, který vytvoří linker. (-o)
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
Název souboru mapy | Možnost Map přikazuje linkeru, aby vytvořil soubor mapy s uživatelsky definovaným názvem. (-Map=)

## <a name="advanced"></a>Upřesnit

Vlastnost | Popis | Možnosti
--- | ---| ---
Označit jen pro čtení proměnné po přemístění | Tato možnost označí proměnné jen pro čtení po přemístění.
Povolit okamžité vázání funkcí | Tato možnost označí objekt pro okamžité vázání funkcí.
Nevyžadují žádná spustitelný zásobník | Tato možnost určí, že výstup nevyžaduje spustitelný zásobník.
Celý archiv | Celý archiv používá veškerý kód ze zdrojů a dalších závislostí.

::: moniker-end
