---
title: Znaky pole typu scanf
ms.date: 11/04/2016
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: dbc6142a87bee00b130589fef5ab92a44f189864
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444747"
---
# <a name="scanf-type-field-characters"></a>Znaky pole typu scanf

Následující informace se vztahují na kteroukoli `scanf`ovou rodinu funkcí, včetně zabezpečených verzí, jako je například `scanf_s`.

Znak `type` je jediné požadované pole formátu. Zobrazuje se po všech volitelných polích formátu. `type` znak určuje, zda je přidružený argument interpretován jako znak, řetězec nebo číslo.

### <a name="type-characters-for-scanf-functions"></a>Znaky typů pro funkce scanf

|Znak|Očekával se typ vstupu.|Typ argumentu|Velikost argumentu v zabezpečené verzi?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Optické. Při použití s funkcemi `scanf` určuje jednobajtové znak; Při použití s funkcí `wscanf` Určuje široce velký znak. Prázdné znaky, které jsou obvykle přeskočeny, jsou čteny při zadání `c`. Pro čtení dalšího neprázdného znaku s jedním bajtem použijte `%1s`; Chcete-li si přečíst další neprázdný znak v širším prostoru, použijte `%1ws`.|Ukazatel na `char` při použití s funkcemi `scanf`, ukazatel na `wchar_t`, pokud se používá s `wscanf` Functions.|Povinná hodnota. Velikost neobsahuje mezeru pro ukončovací znak null.|
|`C`|Opačný znak velikosti Při použití s funkcemi `scanf` určuje šířku znaků; Při použití s funkcí `wscanf` určuje jednobajtové znak. Prázdné znaky, které jsou obvykle přeskočeny, jsou čteny při zadání `C`. Pro čtení dalšího neprázdného znaku s jedním bajtem použijte `%1s`; Chcete-li si přečíst další neprázdný znak v širším prostoru, použijte `%1ws`.|Ukazatel na `wchar_t` při použití s funkcemi `scanf`, ukazatel na `char`, pokud se používá s `wscanf` Functions.|Povinná hodnota. Argument Size neobsahuje mezeru pro ukončovací znak null.|
|`d`|Desítkové celé číslo.|Ukazatel na `int`.|Ne.|
|`i`|Celé číslo. Šestnáctková, pokud vstupní řetězec začíná na "0x" nebo "0X", osmičkové, pokud řetězec začíná "0", jinak Desítková.|Ukazatel na `int`.|Ne.|
|`o`|Osmičkové celé číslo.|Ukazatel na `int`.|Ne.|
|`p`|Adresa ukazatele v hexadecimálních číslech. Maximální počet čtených číslic závisí na velikosti ukazatele (32 nebo 64 bitů), což závisí na architektuře počítače. "0x" nebo "0X" jsou přijímány jako předpony.|Ukazatel na `void*`.|Ne.|
|`u`|Celé číslo bez znaménka.|Ukazatel na `unsigned int`.|Ne.|
|`x`|Hexadecimální celé číslo.|Ukazatel na `int`.|Ne.|
|`e`, `E`, `f`, `F`, `g``G`|Hodnota s plovoucí desetinnou čárkou skládající se z volitelného znaménka (+ nebo-), řady jedné nebo více desítkových číslic, které obsahují desetinnou čárku, a volitelné exponent ("e" nebo "E") následovaný volitelnou celočíselnou hodnotou.|Ukazatel na `float`.|Ne.|
|`a`, `A`|Hodnota s plovoucí desetinnou čárkou skládající se z řady jednoho nebo více hexadecimálních číslic, které obsahují volitelnou desetinnou čárku, a exponent ("p" nebo "P") následovaný desítkovou hodnotou.|Ukazatel na `float`.|Ne.|
|`n`|Žádný vstup čtení z datového proudu nebo vyrovnávací paměti.|Ukazatel na `int`, do kterého je uložený počet znaků úspěšně čten z datového proudu nebo vyrovnávací paměti do tohoto bodu v aktuálním volání funkcí `scanf` Functions nebo `wscanf` Functions.|Ne.|
|`s`|Řetězec, až do prvního prázdného znaku (mezera, tabulátor nebo nový řádek). Chcete-li číst řetězce neoddělené mezerami, použijte sadu hranatých závorek (`[ ]`), jak je popsáno v tématu [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s funkcí `scanf` označuje jednobajtové znakové pole; Při použití s funkcí `wscanf` označuje pole s velkým znakem. V obou případech musí být pole znaků dostatečně velké pro vstupní pole a ukončující znak null, který je automaticky připojen.|Povinná hodnota. Velikost zahrnuje místo pro ukončovací znak null.|
|`S`|Textový řetězec s opačnou velikostí, až do prvního prázdného znaku (mezera, tabulátor nebo nový řádek). Chcete-li číst řetězce neoddělené mezerami, použijte sadu hranatých závorek (`[ ]`), jak je popsáno v tématu [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s funkcemi `scanf` znamená, že pole s velkým znakem; Při použití s funkcemi `wscanf` označuje jedno bajtové pole znaků. V obou případech musí být pole znaků dostatečně velké pro vstupní pole a ukončující znak null, který je automaticky připojen.|Povinná hodnota. Velikost zahrnuje místo pro ukončovací znak null.|

Argumenty velikosti, pokud je potřeba, by měly být předány v seznamu parametrů hned za argumentem, na který se vztahují. Například následující kód:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

přečte řetězec s maximální délkou 10 do `string1`a řetězec s maximální délkou 8 do `string2`. Velikost vyrovnávací paměti by měla být aspoň jedna než specifikace šířky, protože místo musí být rezervované pro ukončovací znak null.

Formátovací řetězec může zpracovat jednobajtové nebo stejné zadání znaků bez ohledu na to, zda je použita jednobajtové znak nebo verze s velkým znakem funkce. Proto pro čtení jednoduchých nebo velkých znaků pomocí funkcí `scanf` a `wscanf` funkcí použijte specifikátory formátu následujícím způsobem.

|Čtení znaku jako|Tato funkce se používá|S těmito specifikátory formátu|
|--------------------------|-----------------------|----------------------------------|
|jeden bajt|`scanf` – funkce|`c`, `hc`nebo `hC`|
|jeden bajt|`wscanf` – funkce|`C`, `hc`nebo `hC`|
|široký|`wscanf` – funkce|`c`, `lc`nebo `lC`|
|široký|`scanf` – funkce|`C`, `lc`nebo `lC`|

Chcete-li kontrolovat řetězce pomocí funkcí `scanf` a `wscanf` Functions, použijte výše uvedenou tabulku se specifikátory typu formátu `s` a `S` namísto `c` a `C`.

## <a name="see-also"></a>Viz také

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
