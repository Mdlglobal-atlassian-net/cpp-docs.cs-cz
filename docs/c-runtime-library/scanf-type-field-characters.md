---
title: Znaky pole typu scanf
ms.date: 11/04/2016
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: 86b57aff9cba5065c7c8053dc26e63e3c0cae169
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957835"
---
# <a name="scanf-type-field-characters"></a>Znaky pole typu scanf

Následující informace platí pro kteroukoli `scanf` rodinu funkcí, včetně zabezpečených verzí, `scanf_s`jako je například.

`type` Znak je jediné požadované pole formátu, zobrazuje se za libovolnými volitelnými formátovacími poli. `type` Znak určuje, zda je přidružený argument interpretován jako znak, řetězec nebo číslo.

### <a name="type-characters-for-scanf-functions"></a>Znaky typů pro funkce scanf

|Znak|Očekával se typ vstupu.|Typ argumentu|Velikost argumentu v zabezpečené verzi?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Optické. Při použití s `scanf` funkcemi, určuje jednobajtové znak; při použití s `wscanf` funkcemi určuje velký znak. Prázdné znaky, které jsou obvykle přeskočeny, jsou čteny `c` při zadání. Pro čtení dalšího neprázdného znaku s jedním bajtem, použijte `%1s`; pro čtení dalšího neprázdného znaku v širším prostoru, použijte. `%1ws`|Ukazatel na `char` , pokud se `scanf` používá s funkcemi, `wchar_t` ukazatel na při `wscanf` použití s funkcemi.|Povinný parametr. Velikost neobsahuje mezeru pro ukončovací znak null.|
|`C`|Opačný znak velikosti Při použití s `scanf` funkcemi, určuje velký znak; při použití s `wscanf` funkcemi určuje znak s jedním bajtem. Prázdné znaky, které jsou obvykle přeskočeny, jsou čteny `C` při zadání. Pro čtení dalšího neprázdného znaku s jedním bajtem, použijte `%1s`; pro čtení dalšího neprázdného znaku v širším prostoru, použijte. `%1ws`|Ukazatel na `wchar_t` , pokud se `scanf` používá s funkcemi, `char` ukazatel na při `wscanf` použití s funkcemi.|Povinný parametr. Argument Size neobsahuje mezeru pro ukončovací znak null.|
|`d`|Desítkové celé číslo.|Ukazatel na `int`.|Ne.|
|`i`|Celé číslo. Šestnáctková, pokud vstupní řetězec začíná na "0x" nebo "0X", osmičkové, pokud řetězec začíná "0", jinak Desítková.|Ukazatel na `int`.|Ne.|
|`o`|Osmičkové celé číslo.|Ukazatel na `int`.|Ne.|
|`p`|Adresa ukazatele v hexadecimálních číslech. Maximální počet čtených číslic závisí na velikosti ukazatele (32 nebo 64 bitů), což závisí na architektuře počítače. "0x" nebo "0X" jsou přijímány jako předpony.|Ukazatel na `void*`.|Ne.|
|`u`|Celé číslo bez znaménka.|Ukazatel na `unsigned int`.|Ne.|
|`x`|Hexadecimální celé číslo.|Ukazatel na `int`.|Ne.|
|`e`, `E`, `f`, `F`, `g`, `G`|Hodnota s plovoucí desetinnou čárkou skládající se z volitelného znaménka (+ nebo-), řady jedné nebo více desítkových číslic, které obsahují desetinnou čárku, a volitelné exponent ("e" nebo "E") následovaný volitelnou celočíselnou hodnotou.|Ukazatel na `float`.|Ne.|
|`a`, `A`|Hodnota s plovoucí desetinnou čárkou skládající se z řady jednoho nebo více hexadecimálních číslic, které obsahují volitelnou desetinnou čárku, a exponent ("p" nebo "P") následovaný desítkovou hodnotou.|Ukazatel na `float`.|Ne.|
|`n`|Žádný vstup čtení z datového proudu nebo vyrovnávací paměti.|Ukazatel na `int`, do kterého je uložený počet znaků úspěšně čten z datového proudu nebo vyrovnávací paměti do tohoto bodu v aktuálním `scanf` volání funkcí nebo `wscanf` funkcí.|Ne.|
|`s`|Řetězec, až do prvního prázdného znaku (mezera, tabulátor nebo nový řádek). Chcete-li číst řetězce neoddělené mezerami, použijte sadu hranatých závorek`[ ]`(), jak je popsáno v tématu [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s `scanf` funkcemi znamená jedno bajtové pole znaků; při použití s funkcemi znamená `wscanf` pole s velkým znakem. V obou případech musí být pole znaků dostatečně velké pro vstupní pole a ukončující znak null, který je automaticky připojen.|Povinný parametr. Velikost zahrnuje místo pro ukončovací znak null.|
|`S`|Textový řetězec s opačnou velikostí, až do prvního prázdného znaku (mezera, tabulátor nebo nový řádek). Chcete-li číst řetězce neoddělené mezerami, použijte sadu hranatých závorek`[ ]`(), jak je popsáno v tématu [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s `scanf` funkcemi znamená, že pole s velkým znakem; při použití `wscanf` s funkcemi znamená pole s jedním bytem znaku. V obou případech musí být pole znaků dostatečně velké pro vstupní pole a ukončující znak null, který je automaticky připojen.|Povinný parametr. Velikost zahrnuje místo pro ukončovací znak null.|

Argumenty velikosti, pokud je potřeba, by měly být předány v seznamu parametrů hned za argumentem, na který se vztahují. Například následující kód:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

přečte řetězec o maximální délce 10 `string1`znaků a řetězec s maximální délkou `string2`8 znaků. Velikost vyrovnávací paměti by měla být aspoň jedna než specifikace šířky, protože místo musí být rezervované pro ukončovací znak null.

Formátovací řetězec může zpracovat jednobajtové nebo stejné zadání znaků bez ohledu na to, zda je použita jednobajtové znak nebo verze s velkým znakem funkce. Proto pro čtení jednobajtových nebo znaků v `scanf` rámci funkcí a `wscanf` funkcí použijte specifikátory formátu následujícím způsobem.

|Čtení znaku jako|Tato funkce se používá|S těmito specifikátory formátu|
|--------------------------|-----------------------|----------------------------------|
|jeden bajt|`scanf` – funkce|`c`, `hc`nebo`hC`|
|jeden bajt|`wscanf` – funkce|`C`, `hc`nebo`hC`|
|široký|`wscanf` – funkce|`c`, `lc`nebo`lC`|
|široký|`scanf` – funkce|`C`, `lc`nebo`lC`|

Chcete-li kontrolovat `scanf` řetězce s funkcemi `wscanf` a funkcemi, použijte výše uvedenou tabulku se `c` specifikátory typu `s` formátu a `S` místo a `C`.

## <a name="see-also"></a>Viz také:

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
