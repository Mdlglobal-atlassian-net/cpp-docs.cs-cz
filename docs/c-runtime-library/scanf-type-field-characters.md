---
title: scanf – znaky pole typu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50db1a8370a43b8b0c43c7c228c7b3acf9dd2c8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082872"
---
# <a name="scanf-type-field-characters"></a>Znaky pole typu scanf

Následující informace platí pro některý z `scanf` řadu funkcí, včetně bezpečné verze, jako například `scanf_s`.

`type` Znak, který je jediným povinná pole formátu, se zobrazí po všech polí volitelné formátu. `type` Znaků určuje, zda přidružený argument je interpretován jako znak, řetězec nebo číslo.

### <a name="type-characters-for-scanf-functions"></a>Znaky typu scanf – funkce

|Znak|Typ vstupu očekávání|Typ argumentu|Velikost argumentu v bezpečné verze?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|znak. Při použití s `scanf` funkce, určuje jednobajtový znak; při použití s `wscanf` funkce, určuje širokého znaku. Při čtení prázdných znaků, které se obvykle přeskočí `c` je zadán. Chcete-li si přečíst další prázdné znaky jednobajtový znak, použijte `%1s`; Pokud si chcete přečíst další-neprázdný široký znak, použijte `%1ws`.|Ukazatel na `char` při použití s `scanf` funkce, ukazatele na `wchar_t` při použití s `wscanf` funkce.|Požadováno. Velikost nezahrnuje prostor pro ukončovacího znaku null.|
|`C`|Opačný velikost znaků. Při použití s `scanf` funkce, určuje širokého znaku; při použití s `wscanf` funkce, určuje jednobajtový znak. Při čtení prázdných znaků, které se obvykle přeskočí `C` je zadán. Chcete-li si přečíst další prázdné znaky jednobajtový znak, použijte `%1s`; Pokud si chcete přečíst další-neprázdný široký znak, použijte `%1ws`.|Ukazatel na `wchar_t` při použití s `scanf` funkce, ukazatele na `char` při použití s `wscanf` funkce.|Požadováno. Velikost argumentu nezahrnuje prostor pro ukončovacího znaku null.|
|`d`|Desítkové celé číslo.|Ukazatel na `int`.|Ne.|
|`i`|Celé číslo. Šestnáctkové číslo, pokud vstupní řetězec začíná řetězcem "0 x" nebo "0 X", osmičkové, pokud řetězec začíná řetězcem "0", jinak decimal.|Ukazatel na `int`.|Ne.|
|`o`|Osmičkové celé číslo.|Ukazatel na `int`.|Ne.|
|`p`|Adresa ukazatele v šestnáctkové číslice. Maximální počet číslic, přečtěte si závisí na velikosti ukazatele (32 nebo 64 bitů), která závisí na architektuře počítače. "0 x" nebo "0 X" jsou přijímány jako předpony.|Ukazatel na `void*`.|Ne.|
|`u`|Desítkové celé číslo bez znaménka.|Ukazatel na `unsigned int`.|Ne.|
|`x`|Šestnáctkové celé číslo.|Ukazatel na `int`.|Ne.|
|`e`, `E`, `f`, `F`, `g`, `G`|S plovoucí desetinnou čárkou, který se skládá z volitelným znaménkem (+ nebo -), řadu jeden nebo více desítkových číslic obsahující desetinná čárka a volitelné exponent ("e" nebo "E"), za nímž následuje hodnotu volitelného znaménka.|Ukazatel na `float`.|Ne.|
|`a`, `A`|Který se skládá z řady jeden nebo více šestnáctkových číslic s volitelnou desetinnou čárkou a exponent ("p" nebo "P") za nímž následuje Desítková hodnota s plovoucí desetinnou čárkou.|Ukazatel na `float`.|Ne.|
|`n`|Žádný vstup číst z datového proudu nebo vyrovnávací paměti.|Ukazatel na `int`, do které je uložený počet znaků, které úspěšně načtena z datového proudu nebo uložit do vyrovnávací paměti až k danému bodu v aktuální volání `scanf` funkce nebo `wscanf` funkce.|Ne.|
|`s`|Řetězec, až do první prázdné znaky (mezera, kartu nebo nový řádek). Ke čtení řetězce není oddělená znaky mezery, použijte hranaté závorky (`[ ]`), jak je popsáno v [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s `scanf` funkce, označuje, že pole jednobajtový znak; při použití s `wscanf` funkce, označuje, že pole širokých znaků. V obou případech musí být dostatečně velký pro vstupní pole a ukončujícího znaku null, která se automaticky připojí pole znaků.|Požadováno. Velikost zahrnuje prostor pro ukončovacího znaku null.|
|`S`|Velikost opak řetězec znaků, až do první prázdné znaky (mezera, kartu nebo nový řádek). Ke čtení řetězce není oddělená znaky mezery, použijte hranaté závorky (`[ ]`), jak je popsáno v [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s `scanf` funkce, označuje, že pole širokého znaku; při použití s `wscanf` funkce, označuje, že pole bajtů. jedním znakem. V obou případech musí být dostatečně velký pro vstupní pole a ukončujícího znaku null, která se automaticky připojí pole znaků.|Požadováno. Velikost zahrnuje prostor pro ukončovacího znaku null.|


Argumenty velikosti v případě potřeby by měl předávat v seznamu parametrů ihned po argumentu, který se vztahují na. Například následující kód:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

načte řetězec s délkou maximálně 10 do `string1`a řetězec s maximální délkou 8 do `string2`. Velikost vyrovnávací paměti by měla být aspoň jeden více než specifikace šířky od místa musí být vyhrazen pro ukončovacího znaku null.

Řetězec formátu může zpracovávat vstup jednobajtové nebo široký znak bez ohledu na to, zda je použit jednobajtového znaku a širokoznaká verze funkce. Díky tomu se číst jednobajtové nebo široké znaky s `scanf` funkce a `wscanf` funkce, pomocí specifikátorů formátu následujícím způsobem.

|Ke čtení znaků jako|Pomocí této funkce|S tyto specifikátory formátu|
|--------------------------|-----------------------|----------------------------------|
|jeden bajt|`scanf` Funkce|`c`, `hc`, nebo `hC`|
|jeden bajt|`wscanf` Funkce|`C`, `hc`, nebo `hC`|
|široký|`wscanf` Funkce|`c`, `lc`, nebo `lC`|
|široký|`scanf` Funkce|`C`, `lc`, nebo `lC`|

Kontrola řetězce s `scanf` funkce, a `wscanf` funkcí, použijte výše uvedené tabulky s typem specifikátory formátu `s` a `S` místo `c` a `C`.

## <a name="see-also"></a>Viz také

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)