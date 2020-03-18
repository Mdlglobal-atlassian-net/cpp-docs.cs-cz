---
title: C/C++ vlastnosti (Linux C++)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: 394cb501b4df6caed6a358ffa96ce0de5d187ae1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441470"
---
# <a name="cc-properties-linux-c"></a>C/C++ vlastnosti (Linux C++)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Obecné

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Další adresáře k zahrnutí | Určuje jeden nebo více adresářů, které mají být přidány do cesty include. K oddělení více adresářů použijte středníkem. (-I\[cesta]). |
| Formát ladicích informací | Určuje typ ladicích informací generovaných kompilátorem. | **None** – nevytváří žádné ladicí informace, takže kompilace může být rychlejší.<br/>**Minimální informace o ladění** – vygenerují minimální ladicí informace.<br/>**Úplné ladicí informace (DWARF2)** – vygeneruje informace o ladění DWARF2.<br/> |
| Název souboru objektu | Určuje název, který má přepsat výchozí název souboru objektu. Může se jednat o název souboru nebo adresáře. (-o [název]). |
| Úroveň upozornění | Vybírá, jak striktní má kompilátor být o chybách kódu.  Přidejte další příznaky přímo k **dalším možnostem**. (/w,/Weverything). | Vypnout **všechna upozornění** – zakáže všechna upozornění kompilátoru.<br/>**Povolit všechna upozornění** – povolí všechna upozornění, včetně těch, která jsou ve výchozím nastavení zakázaná.<br/> |
| Zpracovávat upozornění jako chyby | Zpracovává všechna upozornění kompilátoru jako chyby. Pro nový projekt může být nejvhodnější používat/Werror ve všech kompilacích. Vyřešte všechna upozornění, abyste zajistili nejmenší možné nedostatky v obtížném hledání kódu. |
| Další upozornění (C) | Definuje sadu dalších zpráv s upozorněními. |
| C++Další upozornění | Definuje sadu dalších zpráv s upozorněními. |
| Zapnout režim podrobného výpisu | Pokud je zapnutý režim verbose, vypíše Další informace k diagnostice sestavení. |
| Kompilátor jazyka C | Určuje program, který se má volat během kompilování zdrojových souborů C, nebo cestu ke kompilátoru C ve vzdáleném systému. |
| Kompilátor C++ | Určuje program, který se má volat během C++ kompilování zdrojových souborů, nebo cestu k C++ kompilátoru na vzdáleném systému. |
| Časový limit kompilace | Časový limit vzdálené kompilace v milisekundách |
| Kopírovat soubory objektů | Určuje, zda se mají kopírovat zkompilované soubory objektů ze vzdáleného systému do místního počítače. |

## <a name="optimization"></a>Optimalizace

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** optimalizace.<br/>**Zakázáno** – zakázat optimalizaci.<br/>**Minimalizovat velikost** – optimalizovat pro velikost<br/>**Maximalizujte rychlost** – Optimalizujte rychlost.<br/>**Úplná optimalizace** – nákladné optimalizace |
| Striktní aliasy | Předpokládá pravidla pro přísnější aliasy.  U objektu jednoho typu se nikdy nepředpokládá, že má stejnou adresu jako objekt jiného typu. |
| Odvalení smyček | Umožňuje uvolnit smyčky, aby se aplikace rychleji snížila tím, že se sníží počet spuštěných větví za cenu větší velikosti kódu. |
| Optimalizace času propojení | Umožňuje optimalizaci mezi procesními soubory tím, že umožňuje Optimalizátoru prohledat v aplikacích objekty v aplikaci. |
| Vynechat ukazatel na rámec | Zakazuje vytváření ukazatelů na rámce v zásobníku volání. |
| Žádné společné bloky | Přiděluje dokonce neinicializované globální proměnné v datové sekci souboru objektu, spíše než je vygeneruje jako běžné bloky. |

## <a name="preprocessor"></a>Preprocesor

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Definice preprocesoru | Definuje symboly předzpracování pro zdrojový soubor. (-D) |
| Zrušit Definice preprocesoru | Určuje jeden nebo více zrušení definujících preprocesoru.  (-U \[makro]) |
| Zrušit definici všech definic preprocesoru | Zruší definici všech dříve definovaných hodnot preprocesoru.  (-undef) |
| Zobrazit zahrnutí | Generuje seznam souborů k zahrnutí s výstupem kompilátoru.  (-H) |

## <a name="code-generation"></a>Vytvoření kódu

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Pozice nezávislého kódu | Generuje kód nezávislý na poloze (PIC) pro použití ve sdílené knihovně. |
| Statické objekty jsou vláknově bezpečné. | Vygeneruje dodatečný kód pro použití rutin určených v C++ ABI pro inicializaci místních statických proměnných pro vlákny. | **Ne** – zakažte statické objekty bezpečné pro přístup z více vláken.<br/>**Ano** – povolí statické objekty bezpečné pro přístup z více vláken. |
| Optimalizace plovoucí desetinné čárky | Povolí optimalizace plovoucí desetinné čárky podle požadavků dodržování předpisů IEEE-754. |
| Skryté metody vložených | Je-li povoleno, jsou uvedeny nepřesné kopie vložených metod, které jsou deklarovány `private extern`. |
| Ve výchozím nastavení jsou symboly skryté. | Všechny symboly jsou deklarovány `private extern`, pokud nejsou explicitně označeny pro export pomocí makra `__attribute`. |
| Povolit C++ výjimky | Určuje model zpracování výjimek používaný kompilátorem. | **Bez** zákazu zpracování výjimek.<br/>**Ano** – povolí zpracování výjimek. |

## <a name="language"></a>Jazyk

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Povolit informace běhového typu | Přidá kód pro kontrolu C++ typů objektů v době běhu (informace o typu modulu runtime).     (frtti, fno-rtti) |
| Standard jazyka C | Určuje standard jazyka C. | **Výchozí**<br/>Standard jazyka **c89** -c89.<br/>Standard jazyka **C99** -C99.<br/>Standard jazyka **C11** -C11.<br/>**C99 (DIALEKT GNU)** – Standard jazyka C99 (dialekt GNU)<br/>**C11 (DIALEKT GNU)** – Standard jazyka C11 (dialekt GNU) |
| C++Standardní jazyk | Určuje standardní C++ jazyk. | **Výchozí**<br/>**C++ 03** – Standard jazyka c++ 03.<br/>**C++** 11 – Standard jazyka c++ 11.<br/>**C++** 14 – Standard jazyka c++ 14.<br/>**C++ 03 (DIALEKT GNU)** – Standard jazyka c++ 03 (dialekt GNU)<br/>**C++ 11 (DIALEKT GNU)** – Standard jazyka c++ 11 (dialekt GNU)<br/>**C++ 14 (DIALEKT GNU)** – Standard jazyka c++ 14 (dialekt GNU) |

## <a name="advanced"></a>Upřesňující

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Kompilovat jako | Vybere možnost jazyka kompilace pro soubory. c a. cpp. (-x c, -x c++) | **Výchozí** – rozpoznat podle přípony. c nebo. cpp.<br/>**Kompilovat jako kód jazyka c** – kompilovat jako kód jazyka c.<br/>**Kompilovat jako C++**  kód – kompilovat jako C++ kód. |
| Vynucené vložené soubory | Určuje jeden nebo více souborů s vynuceným zahrnutím (-include \[název]). |

::: moniker-end
