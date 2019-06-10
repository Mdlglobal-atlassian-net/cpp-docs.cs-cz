---
title: Vlastnosti C/C++ (C++ pro Linux)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: b5be7582970c45e25f1e2c90971d587c19eac2a0
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821331"
---
# <a name="cc-properties-linux-c"></a>Vlastnosti C/C++ (C++ pro Linux)

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Další adresáře souborů k zahrnutí | Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí. K oddělení více adresářů, použijte středníky. (-I\[cesta]).
Formát ladicích informací | Určuje typ ladicích informací generovaných kompilátorem. | **Žádný** -nevytváří žádné ladicí informace, takže kompilace může být rychlejší.<br/>**Minimální informace o ladění** -generovat minimální informace o ladění.<br/>**Úplné informace o ladění (DWARF2)** -ladicí informace DWARF2 generovat.<br/>
Název souboru objektů | Určuje název, který má přepsat výchozí název souboru objektů. Může být název souboru nebo adresáře. (-o [název]).
Úroveň upozornění | Vybere, jak přísně má kompilátor, aby se informace o kódu chyby.  Přidat přímo do nastavení další příznaky **další možnosti**. (/ w, / weverything). | **Vypnout všechna upozornění** – zakáže všechna upozornění kompilátoru.<br/>**EnableAllWarnings** – umožňuje všechna upozornění včetně těch, které jsou ve výchozím nastavení zakázané.<br/>
Zpracovávat upozornění jako chyby | Zpracuje všechna upozornění kompilátoru jako chyby. Pro nový projekt může být vhodné použít werror při všech kompilacích. Vyřešte všechna upozornění zajistit nejmíň vad kódu možné obtížné najít.
Další upozornění C | Definuje množinu zpráv dalších upozornění.
Další upozornění C++ | Definuje množinu zpráv dalších upozornění.
Povolíte režim s komentářem | Když je povolený režim s komentářem, vytiskne Další informace pro diagnostiku sestavení.
Kompilátor jazyka C | Určuje program, který se má volat během kompilování zdrojových souborů C, nebo cestu ke kompilátoru C ve vzdáleném systému.
Kompilátor C++ | Určuje program, který se má volat během kompilování zdrojových souborů C++, nebo cestu ke kompilátoru C++ ve vzdáleném systému.
Časový limit kompilace | Časový limit vzdálené kompilace, v milisekundách.
Kopírovat soubory objektů | Určuje, jestli se má kopírovat zkompilované soubory objektů ze vzdáleného systému do místního počítače.

## <a name="optimization"></a>Optimalizace

Vlastnost | Popis | Možnosti
--- | ---| ---
Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** – vlastní optimalizace.<br/>**Zakázané** – zakáže optimalizaci.<br/>**Minimální velikost** -optimalizovat pro velikost.<br/>**Maximalizovat rychlost** -optimalizovat rychlost.<br/>**Plná optimalizace** – nákladné optimalizace.
Striktní aliasy | Předpokládá nejpřísnější pravidla pro aliasy.  Objekt jednoho typu nikdy se předpokládá, že má stejné adrese jako objekt jiného typu.
Rozvinutí smyček | Unrolls smyček urychlí aplikaci snížením počtu provedených rozvětvení na, úkor větší velikosti kódu.
Optimalizace v době propojování | Umožňuje meziprocedurální optimalizaci tím, že Optimalizátor hledání napříč soubory objektů ve vaší aplikaci.
Vypustit ukazatel na rámec | Zakazuje vytváření ukazatelů na rámce v zásobníku volání.
Žádné společné bloky | Alokuje i neinicializované globální proměnné v datové sekci souboru objektu, nikoli Generovat jako společné bloky.

## <a name="preprocessor"></a>Preprocesor

Vlastnost | Popis | Možnosti
--- | ---| ---
Definice preprocesoru | Definuje symboly předzpracování pro zdrojový soubor. (-D)
Zrušit Definice preprocesoru | Určuje že jeden nebo více nedefinovaných hodnot preprocesoru.  (-U \[– makro])
Zrušit všechny definice preprocesoru | Nedefinovaných hodnot všech dříve definovaných hodnot preprocesoru.  (-undef)
Zobrazit soubory k zahrnutí | Generuje seznam vložených souborů s výstupem kompilátoru.  (-H)

## <a name="code-generation"></a>Vytvoření kódu

Vlastnost | Popis | Možnosti
--- | ---| ---
Pozičně nezávislý kód | Generuje kód nezávislý na pozici (PIC) pro použití ve sdílené knihovně.
Jsou vláknově bezpečné | Generuje kód navíc používající rutiny určené v C++ ABI pro vláknově bezpečné inicializace místních statik. | **Ne** – zakáže vláknově bezpečné pro vlákna.<br/>**Ano** -povolit vláknově bezpečné pro vlákna.
Optimalizace plovoucí desetinné čárky | Umožňuje optimalizace plovoucí desetinné čárky volnějším IEEE 754 dodržování předpisů.
Skrytí inline metod | Pokud povolená, jsou deklarované mimo řádek kopie inline metod `private extern`.
Ve výchozím nastavení skryje symboly | Všechny symboly se deklarují jako `private extern` Pokud nejsou explicitně označené pro export s použitím `__attribute` – makro.
Povolit výjimky jazyka C++ | Určuje model zpracování výjimek, které kompilátor použije. | **Ne** – zakáže zpracování výjimek.<br/>**Ano** -povolit zpracování výjimek.

## <a name="language"></a>Jazyk

Vlastnost | Popis | Možnosti
--- | ---| ---
Povolit informace běhového typu | Přidává kód pro kontrolu typů objektů jazyka C++ za běhu (informace typu za běhu).     (frtti, fno-rtti)
Standard jazyka C | Určuje standard jazyka C. | **Default**<br/>**C89** – Standard jazyka C89.<br/>**C99** – Standard jazyka C99.<br/>**C11** – Standard jazyka C11.<br/>**C99 (dialekt GNU)** – Standard jazyka C99 (dialekt GNU).<br/>**C11 (dialekt GNU)** – Standard jazyka C11 (dialekt GNU).
Standard jazyka C++ | Určuje standard jazyka C++. | **Default**<br/>**C ++ 03** – Standard C ++ 03 jazyka.<br/>**C ++ 11** – Standard C ++ 11 jazyka.<br/>**C ++ 14** – Standard C ++ 14 jazyka.<br/>**C ++ 03 (dialekt GNU)** – C ++ 03 (dialekt GNU) Standard jazyka.<br/>**C ++ 11 (dialekt GNU)** – C ++ 11 (dialekt GNU) Standard jazyka.<br/>**C ++ 14 (dialekt GNU)** – C ++ 14 (dialekt GNU) Standard jazyka.

## <a name="advanced"></a>Upřesnit

Vlastnost | Popis | Možnosti
--- | ---| ---
Kompilovat jako | Vybere možnost jazyka kompilace pro soubory .c a .cpp. (-x c, -x c++) | **Výchozí** – zjišťování na základě přípony .c nebo .cpp.<br/>**Kompilovat jako kód jazyka C** -kompilovat jako kód jazyka C.<br/>**Zkompiluje kód jako C++ kód** – zkompiluje kód jako C++ kódu.
Nuceně zahrnuté soubory | Určuje jeden nebo více vynucených soubory k zahrnutí (-zahrnují \[název])

::: moniker-end
