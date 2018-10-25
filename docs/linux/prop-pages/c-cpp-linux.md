---
title: Vlastnosti C/C++ (C++ pro Linux) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
author: mikeblome
ms.author: mblome
f1_keywords: []
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 78918acc70bddb25841b2bcaaf8f7cd7b627d63b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061557"
---
# <a name="cc-properties-linux-c"></a>Vlastnosti C/C++ (C++ pro Linux)

## <a name="general"></a>Obecné

Vlastnost | Popis | Možnosti
--- | ---| ---
Další adresáře souborů k zahrnutí | Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí; oddělte středníkem, pokud více než jeden. (-I[cesta]).
Formát ladicích informací | Určuje typ ladicích informací generovaných kompilátorem. | **Žádný** -nevytváří žádné ladicí informace, takže kompilace může být rychlejší.<br/>**Minimální informace o ladění** -generovat minimální informace o ladění.<br/>**Úplné informace o ladění (DWARF2)** -ladicí informace DWARF2 generovat.<br/>
Název souboru objektů | Určuje název, který má přepsat výchozí název souboru objektů; může být název souboru nebo adresáře. (-o [název]).
Úroveň upozornění | Vyberte, jak přísně má kompilátor, aby se informace o kódu chyby.  Další příznaky se přidávají přímo do další možnosti. (/ w, / weverything). | **Vypnout všechna upozornění** – zakáže všechna upozornění kompilátoru.<br/>**EnableAllWarnings** – povoluje všechna upozornění včetně těch, které ve výchozím nastavení zakázané.<br/>
Zpracovávat upozornění jako chyby | Zpracuje všechna upozornění kompilátoru jako chyby. Pro nový projekt může být nejlepší použít při všech kompilacích; werror vyřešením všech upozornění zajistíte, že nejmenším počtem vad kódu možné obtížné najít.
Další upozornění C | Definuje množinu zpráv dalších upozornění.
Další upozornění C++ | Definuje množinu zpráv dalších upozornění.
Povolíte režim s komentářem | Když je povolený režim s komentářem, tento nástroj by vytiskne Další informace, které při diagnostice sestavení.
Kompilátor jazyka C | Určuje program, který se má volat během kompilování zdrojových souborů C, nebo cestu ke kompilátoru C ve vzdáleném systému.
Kompilátor C++ | Určuje program, který se má volat během kompilování zdrojových souborů C++, nebo cestu ke kompilátoru C++ ve vzdáleném systému.
Časový limit kompilace | Časový limit vzdálené kompilace, v milisekundách.
Kopírovat soubory objektů | Určuje, jestli se má kopírovat zkompilované soubory objektů ze vzdáleného systému do místního počítače.

## <a name="optimization"></a>Optimalizace

Vlastnost | Popis | Možnosti
--- | ---| ---
Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** – vlastní optimalizace.<br/>**Zakázané** – zakáže optimalizaci.<br/>**Minimální velikost** -optimalizovat pro velikost.<br/>**Maximalizovat rychlost** -optimalizovat rychlost.<br/>**Plná optimalizace** – nákladné optimalizace.<br/>
Striktní aliasy | Předpokládejme nejpřísnější pravidla pro aliasy.  Objekt jednoho typu se nikdy být předpokládat, že na stejné adrese jako objekt jiného typu.
Rozvinutí smyček | Rozvinutí smyček urychlí aplikaci snížením počtu provedených rozvětvení na úkor větší velikosti kódu.
Optimalizace v době propojování | Povolte Meziprocedurální optimalizaci tím, že Optimalizátor hledání napříč soubory objektů ve vaší aplikaci.
Vypustit ukazatel na rámec | Zakazuje vytváření ukazatelů na rámce v zásobníku volání.
Žádné společné bloky | Přidělit i neinicializované globální proměnné v datové sekci souboru objektu, místo toho generovaly jako společné bloky.

## <a name="preprocessor"></a>Preprocesor

Vlastnost | Popis | Možnosti
--- | ---| ---
Definice preprocesoru | Definuje symboly předzpracování pro zdrojový soubor. (-D)
Zrušit Definice preprocesoru | Určuje že jeden nebo více nedefinovaných hodnot preprocesoru.  (-U [makro])
Zrušit všechny definice preprocesoru | Zruší definici všech dříve definovaných hodnot preprocesoru.  (-undef)
Zobrazit soubory k zahrnutí | Generuje seznam vložených souborů s výstupem kompilátoru.  (-H).

## <a name="code-generation"></a>Vytvoření kódu

Vlastnost | Popis | Možnosti
--- | ---| ---
Pozičně nezávislý kód | Generovat pozice nezávislý kód (PIC) pro použití ve sdílené knihovně.
Jsou vláknově bezpečné | Vytvoří kód navíc používající rutiny určené v C++ ABI pro bezpečné při inicializaci místních statik vlákna. | **Ne** – zakáže vláknově bezpečné statiky.<br/>**Ano** – povolí vláknově bezpečné.<br/>
Optimalizace plovoucí desetinné čárky | Umožní optimalizaci plovoucí čárky volnějším souladem IEEE 754.
Skrytí inline metod | Při povolení mimo řádek kopie inline metod jsou deklarovány "private extern".
Skrytí symbolů ve výchozím nastavení | Všechny symboly se deklarují jako "private extern", pokud nejsou explicitně označené pro export použitím makra "__attribute".
Povolit výjimky jazyka C++ | Určuje model zpracování výjimek pro použití kompilátorem. | **Ne** – zakáže zpracování výjimek.<br/>**Ano** -povolit zpracování výjimek.<br/>

## <a name="language"></a>Jazyk

Vlastnost | Popis | Možnosti
--- | ---| ---
Povolit informace běhového typu | Přidává kód pro kontrolu typů objektů jazyka C++ za běhu (informace typu za běhu).     (frtti, fno-rtti)
Standard jazyka C | Určuje standard jazyka C. | **Default**<br/>**C89** – Standard jazyka C89.<br/>**C99** – Standard jazyka C99.<br/>**C11** – Standard jazyka C11.<br/>**C99 (dialekt GNU)** – Standard jazyka C99 (dialekt GNU).<br/>**C11 (dialekt GNU)** – Standard jazyka C11 (dialekt GNU).<br/>
Standard jazyka C++ | Určuje standard jazyka C++. | **Default**<br/>**C ++ 03** – Standard C ++ 03 jazyka.<br/>**C ++ 11** – Standard C ++ 11 jazyka.<br/>**C ++ 14** – Standard C ++ 14 jazyka.<br/>**C ++ 03 (dialekt GNU)** – C ++ 03 (dialekt GNU) Standard jazyka.<br/>**C ++ 11 (dialekt GNU)** – C ++ 11 (dialekt GNU) Standard jazyka.<br/>**C ++ 14 (dialekt GNU)** – C ++ 14 (dialekt GNU) Standard jazyka.<br/>

## <a name="advanced"></a>Upřesnit

Vlastnost | Popis | Možnosti
--- | ---| ---
Kompilovat jako | Vyberte možnost jazyka kompilace pro soubory .c a .cpp.  "Výchozí" rozpozná na základě přípony .c nebo .cpp rozšíření. (-x c, - x c ++) | **Výchozí** – výchozí.<br/>**Kompilovat jako kód jazyka C** -kompilovat jako kód jazyka C.<br/>**Kompilovat jako kód jazyka C++** -kompilovat jako kód jazyka C++.<br/>
Nuceně zahrnuté soubory | Jeden nebo více vynucených k zahrnutí souborů (-include [název])

## <a name="additional-options"></a>Další možnosti
