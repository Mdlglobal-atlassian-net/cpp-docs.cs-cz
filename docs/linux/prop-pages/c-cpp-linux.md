---
title: Vlastnosti C/C++ (Linux C++) | Microsoft Docs
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
ms.openlocfilehash: 1978c566dab949093f0ddbd2aa1aa37ad0942808
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cc-properties-linux-c"></a>Vlastnosti C/C++ (Linux C++)

## <a name="general"></a>Obecné
Vlastnost | Popis | Možnosti
--- | ---| ---
Další zahrnuté adresáře | Určuje jeden nebo více adresáře, které chcete přidat do cesty zahrnutí; oddělit pomocí středníky, pokud je více než jeden. (-I[path]).
Ladění formátu informací | Určuje typ ladicí informace generované kompilátorem. | **Žádný** -vytvoří žádné informace o ladění, takže kompilace může být rychlejší.<br>**Minimální informace ladění** -generovat informace o minimální ladění.<br>**Úplné informace o ladění (DWARF2)** -DWARF2 Generovat ladicí informace.<br>
Název souboru objektů | Určuje název přepsat výchozí název objektu souboru; může být název souboru nebo adresáře. (-o [name]).
Úroveň upozornění | Vyberte, jak striktní chcete kompilátoru být o kódu chyby.  Nastavení další příznaky musí být přidaní přímo k další možnosti. (/ w, /Weverything). | **Vypnout všech upozornění** – zakáže všech upozornění kompilátoru.<br>**EnableAllWarnings** -povolí všechny výstrahy, včetně těch, které ve výchozím nastavení zakázaná.<br>
Zpracovávat upozornění jako chyby | Zpracovává všechny kompilátoru upozornění jako chyby. Pro nový projekt může být nejvhodnější použít /Werror v všechny kompilace; vyřešení všech upozornění bude zajištěno, že nejmenší počet defektů možné pevný najít kódu.
Další upozornění C | Definuje sadu další zprávy upozornění.
Další upozornění pro C++ | Definuje sadu další zprávy upozornění.
Povolit podrobné režim | Pokud je povoleno podrobné režimu, by tento nástroj vytiskněte Další informace, pro diagnostikování sestavení.
Kompilátor jazyka C | Určuje program, který má být vyvolán při kompilaci zdrojové soubory C nebo cestu ke kompilátor jazyka C ve vzdáleném systému.
Kompilátor C++ | Určuje program, který má být vyvolán při kompilaci C++ zdrojové soubory nebo cesty k C++ compiler ve vzdáleném systému.
Kompilace vypršení časového limitu | Časový limit vzdálené kompilace, v milisekundách.
Zkopírujte soubory objektů | Určuje, zda chcete zkopírovat soubory kompilované objektů ze vzdáleného systému v místním počítači.

## <a name="optimization"></a>Optimalizace
Vlastnost | Popis | Možnosti
--- | ---| ---
Optimalizace | Určuje úroveň optimalizace pro aplikaci. | **Vlastní** – vlastní optimalizace.<br>**Zakázané** -zakázat optimalizace.<br>**Minimální velikost** -optimalizovat pro velikost.<br>**Maximalizovat rychlost** -optimalizovat pro rychlost.<br>**Úplná optimalizace** -nákladné optimalizace.<br>
Striktní aliasy | Předpokládejme nejpřísnějším pravidla pro aliasy.  Objekt jednoho typu se nikdy se předpokládá, že jsou umístěny na stejnou adresu jako objekt jiného typu.
Nezobrazovaly smyčky | Nezobrazovaly smyčky, aby aplikace rychlejší snížením počtu větví proveden za cenu větší velikosti kódu.
Optimalizace času odkaz | Povolte mezi procedurální optimalizace tím, že Optimalizátor Hledat v souborech objektu ve vaší aplikaci.
Vynechat ukazatel na rámec | Zakazuje vytváření ukazatelů na rámce v zásobníku volání.
Žádné společné bloky | Přidělit i unintialized globální proměnné v datové části souboru objektu místo pak je generování jako běžné bloky

## <a name="preprocessor"></a>Preprocesor
Vlastnost | Popis | Možnosti
--- | ---| ---
Definice preprocesoru | Definuje předběžného zpracování symboly pro zdrojový soubor. (-D)
Nedefinované Definice preprocesoru | Určuje, že jeden nebo více preprocesor undefines.  (-U [makro])
Nedefinované všechny definice preprocesoru | Nedefinované všechny dříve definované preprocesoru hodnoty.  (-undef)
Obsahuje zobrazení | Vygeneruje seznam zahrnout soubory s výstupu kompilátoru.  (-H).

## <a name="code-generation"></a>Vytvoření kódu
Vlastnost | Popis | Možnosti
--- | ---| ---
Pozice nezávislé kódu | Generovat pozice nezávislé kódu (PIC) pro použití ve sdílené knihovně.
Statické objekty jsou bezpečné pro přístup z více vláken | Emitování navíc kódu pro použití rutin, které jsou zadané v C++ ABI pro přístup z více vláken bezpečné inicializaci místní statické objekty. | **Ne** -zakázat statické objekty bezpečný přístup z více vláken.<br>**Ano** -povolit statické objekty bezpečný přístup z více vláken.<br>
Plovoucí bodu optimalizace | Umožňuje plovoucí bodu optimalizace podle uvolnit IEEE 754 dodržování předpisů.
Vložené metody skryté | Když je povolené, se na řádek kopie vložené metody jsou deklarovány 'privátní extern'.
Symbol Hiddens ve výchozím nastavení | Všechny symboly jsou deklarovány 'privátní extern' explicitně označena export použití makra '__attribute'.
Povolit výjimky jazyka C++ | Určuje model zpracování má být používána kompilátor výjimek. | **Ne** -zakázat zpracování výjimek.<br>**Ano** -povolit zpracování výjimek.<br>

## <a name="language"></a>Jazyk
Vlastnost | Popis | Možnosti
--- | ---| ---
Povolit informace běhového typu | Přidá kód pro kontrolu typy objektů C++ v době běhu (informace o běhu programu typ).     (frtti, fno rtti)
Jazyk C – Standard | Určuje standard jazyka C. | **Default**<br>**Kompilátorem C89** -Standard kompilátorem C89 Language.<br>**C99** -C99 Language Standard.<br>**C11** -C11 Language Standard.<br>**C99 (GNU dialekt)** -C99 Standard Language (GNU dialekt).<br>**C11 (GNU dialekt)** -C11 Standard Language (GNU dialekt).<br>
Standard jazyka C++ | Určuje standard jazyka C++. | **Default**<br>**C ++ 03** -03 jazyk standardu C ++.<br>**C ++ 11** -C ++ 11 jazyk Standard.<br>**C ++ 14** -C ++ 14 jazyk Standard.<br>**C ++ 03 (GNU dialekt)** – C ++ 03 Standard Language (GNU dialekt).<br>**C ++ 11 (GNU dialekt)** – C ++ 11 Standard Language (GNU dialekt).<br>**C ++ 14 (GNU dialekt)** – C ++ 14 Standard Language (GNU dialekt).<br>

## <a name="advanced"></a>Upřesnit
Vlastnost | Popis | Možnosti
--- | ---| ---
Kompilace jako | Vyberte možnost kompilace jazyka .c a sada souborů.  "Výchozí" zjistí na základě .c nebo sada rozšíření. (-x - x c, c ++) | **Výchozí** -výchozí.<br>**Kompilace jako kód C** -zkompilovat jako C – kód jazyka.<br>**Kompilace jako C++ – kód** -zkompilovat jako C++ – kód.<br>
Vynutit vložené soubory | Jeden nebo více vynutit zahrnout soubory (-zahrnují [name])

## <a name="additional-options"></a>Další možnosti 
