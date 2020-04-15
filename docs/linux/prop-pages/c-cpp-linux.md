---
title: Vlastnosti C/C++ (Linux C++)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: 394cb501b4df6caed6a358ffa96ce0de5d187ae1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441470"
---
# <a name="cc-properties-linux-c"></a>Vlastnosti C/C++ (Linux C++)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Obecné

| Vlastnost | Popis | Choices |
|--|--|--|
| Další zahrnutí adresářů | Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí. Pomocí středníků oddělte více adresářů. (-I\[cesta]). |
| Formát informací o ladění | Určuje typ informací o ladění generovaných kompilátorem. | **None** - Nevytváří žádné informace o ladění, takže kompilace může být rychlejší.<br/>**Minimální informace o ladění** – vygenerujte minimální informace o ladění.<br/>**Úplné informace o ladění (DWARF2)** - Generovat informace o ladění DWARF2.<br/> |
| Název souboru objektu | Určuje název, který má přepsat název výchozího souboru objektu. Může to být název souboru nebo adresáře. (-o [jméno]). |
| Úroveň upozornění | Vybere, jak přísný má být kompilátor o chybách kódu.  Přidání dalších příznaků přímo do **dalších možností**. (/w, /Weverything). | **Vypnout všechna upozornění** – Zakáže všechna upozornění kompilátoru.<br/>**EnableAllWarnings** - Povolí všechna upozornění, včetně těch, která jsou ve výchozím nastavení zakázána.<br/> |
| Považovat upozornění za chyby | Považuje všechna upozornění kompilátoru za chyby. Pro nový projekt může být nejlepší použít /Werror ve všech kompilacích. Vyřešte všechna upozornění, abyste zajistili co nejméně chyb kódu, který je těžko k nalezení. |
| C Dodatečná varování | Definuje sadu dalších varovných zpráv. |
| C++ Další upozornění | Definuje sadu dalších varovných zpráv. |
| Povolit podrobný režim | Pokud je povolen režim Podrobné, vytiskne další informace k diagnostice sestavení. |
| Kompilátor C | Určuje program, který má být vyvolán během kompilace zdrojových souborů Jazyka C, nebo cestu k kompilátoru Jazyka C ve vzdáleném systému. |
| Kompilátor C++ | Určuje program, který má být vyvolán během kompilace zdrojových souborů jazyka C++ nebo cesta k kompilátoru jazyka C++ ve vzdáleném systému. |
| Časový čas kompilace | Časový čas vzdálené kompilace v milisekundách. |
| Kopírovat soubory objektů | Určuje, zda mají být soubory zkompilovaných objektů zkopírovány ze vzdáleného systému do místního počítače. |

## <a name="optimization"></a>Optimalizace

| Vlastnost | Popis | Choices |
|--|--|--|
| Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** – vlastní optimalizace.<br/>**Zakázáno** - Zakázat optimalizaci.<br/>**Minimalizovat velikost** - Optimalizovat pro velikost.<br/>**Maximalizovat rychlost** - Optimalizovat pro rychlost.<br/>**Úplná optimalizace** - Drahé optimalizace. |
| Přísné aliasování | Předpokládá nejpřísnější pravidla aliasingu.  Objekt jednoho typu se nikdy nepředpokládá, že má stejnou adresu jako objekt jiného typu. |
| Odvíjení smyček | Unrolls smyčky, aby se aplikace rychleji snížením počtu větví provedených, za cenu větší velikost kódu. |
| Optimalizace času propojení | Umožňuje interprocedurální optimalizace tím, že optimalizátor umožnit vyhledávání mezi objektové soubory ve vaší aplikaci. |
| Vynechat ukazatel rámce | Zakazuje vytváření ukazatelů na rámce v zásobníku volání. |
| Žádné společné bloky | Přidělí i neinicializované globální proměnné v datové části souboru objektu, místo aby je generoval jako běžné bloky. |

## <a name="preprocessor"></a>Preprocesor

| Vlastnost | Popis | Choices |
|--|--|--|
| Definice preprocesoru | Definuje symboly předběžného zpracování pro zdrojový soubor. (-D) |
| Nedefinovat definice preprocesoru | Určuje jeden nebo více nedefinuje jeden nebo více předprocesorových nedefinuje.  (-U \[makro]) |
| Zrušit definici všech preprocesorů | Undefines všechny dříve definované hodnoty preprocesoru.  (-undef) |
| Zobrazit zahrnuto | Generuje seznam zahrnutí souborů s výstupem kompilátoru.  (-H) |

## <a name="code-generation"></a>Vytvoření kódu

| Vlastnost | Popis | Choices |
|--|--|--|
| Kód nezávislý na pozici | Generuje kód nezávislý na poloze (PIC) pro použití ve sdílené knihovně. |
| Statika je bezpečná pro přístup z více vláken | Vyzařuje další kód pro použití rutiny zadané v C++ ABI pro inicializaci lokální statiky bezpečné pro přístup z více vláken. | **Ne** - Zakažte statickou elektřinu bezpečnou pro přístup z více vláken.<br/>**Ano** - Povolte statici bez přístupu k vláknům. |
| Optimalizace s plovoucí desetinnou tálič | Umožňuje optimalizaci s plovoucí desetinnou tázkem uvolněním dodržování předpisů IEEE-754. |
| Skryté inline metody | Pokud je tato možnost povolena, jsou deklarovány `private extern`předem zaúčtovací kopie vřádkových metod . |
| Symboly skryté ve výchozím nastavení | Všechny symboly `private extern` jsou deklarovány, `__attribute` pokud nejsou explicitně označeny pro export pomocí makra. |
| Povolit výjimky jazyka C++ | Určuje model zpracování výjimek používaný kompilátorem. | **Ne** - Zakázat zpracování výjimek.<br/>**Ano** – povolit zpracování výjimek. |

## <a name="language"></a>Jazyk

| Vlastnost | Popis | Choices |
|--|--|--|
| Povolit informace o typu běhu | Přidá kód pro kontrolu typů objektů jazyka C++ za běhu (informace o typu runtime).     (frtti, fno-rtti) |
| C Jazykový standard | Určuje standard jazyka C. | **Výchozí**<br/>**C89** - C89 Language Standard.<br/>**C99** - C99 Language Standard.<br/>**C11** - C11 Language Standard.<br/>**C99 (GNU Dialect)** - C99 (GNU Dialect) Language Standard.<br/>**C11 (DIALekt GNU)** - C11 (GNU Dialect) Language Standard. |
| Jazykový standard Jazyka C++ | Určuje jazykový standard jazyka C++. | **Výchozí**<br/>**C++03** - C++03 Language Standard.<br/>**C++11** - C++ 11 Language Standard.<br/>**C++14** - C++14 Language Standard.<br/>**C++03 (DIALekt GNU)** - C++03 (GNU Dialect) Language Standard.<br/>**C++11 (DIALekt GNU)** - C++11 (GNU Dialect) Language Standard.<br/>**C++14 (DIALekt GNU)** - C++14 (GNU Dialect) Language Standard. |

## <a name="advanced"></a>Upřesňující

| Vlastnost | Popis | Choices |
|--|--|--|
| Zkompilovat jako | Vybere možnost jazyka kompilace pro soubory C a CPP. (-x c, -x c++) | **Výchozí** - Rozpoznat na základě .c nebo .cpp rozšíření.<br/>**Zkompilovat jako kód C** - zkompilovat jako kód C.<br/>**Kompilace jako kód jazyka C++** – kompilace jako kód jazyka C++. |
| Vynucené zahrnutí souborů | Určuje jeden nebo více vynucených \[souborů zahrnutí (-include name]) |

::: moniker-end
