---
title: Specifikace šířky scanf | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e236f323d882ddc7091655d944f0ed78bdeac28
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203385"
---
# <a name="scanf-width-specification"></a>Specifikace šířky scanf

Tyto informace platí pro interpretaci formátovací řetězce v `scanf` řadu funkcí, včetně bezpečné verze, jako například `scanf_s`. Tyto funkce obvykle předpokládají, že vstupní datový proud je rozdělen do sekvence tokenů. Tokeny jsou odděleny mezer (místo, tabulátor nebo nový řádek), nebo v případě číselné typy, přirozené end typu číselných dat podle prvního znaku, který nelze převést na číselnou text. Specifikace šířky lze však způsobit parsování vstupu zastavit před ukončením přirozené tokenu.

*Šířka* specifikace se skládá ze znaků mezi `%` a specifikátor typu pole, které mohou obsahovat kladné celé číslo, volá se *šířka* pole a jeden nebo více znaků určující velikost pole, které lze považovat také jako modifikátory typu pole, jako je například údaj o tom, jestli je celočíselný typ **krátký** nebo **dlouhé**. Tyto znaky se označují jako předpona velikosti.

## <a name="the-width-field"></a>Šířka pole

*Šířka* kladné desítkové celé číslo řízení maximální počet znaků ke čtení pro toto pole je pole. Více než *šířka* znaky jsou převést a uložit na odpovídající `argument`. Méně než *šířka* znaky mohou být přečíst, pokud znak mezery (místo, tabulátor nebo nový řádek) nebo znak, který nelze převést podle v daném formátu předchází *šířka* je dosaženo.

Specifikace šířky je oddělená a odlišná od argumentu velikost vyrovnávací paměti vyžadované bezpečné verze těchto funkcí (například `scanf_s`, `wscanf_s`atd.). V následujícím příkladu je specifikace šířky 20, což indikuje, že až 20 znaků jsou ke čtení ze vstupního datového proudu. Délka vyrovnávací paměti je 21, která zahrnuje prostor pro možný 20 znaků plus ukončovacího znaku null:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Pokud *šířka* se pole nepoužívá, `scanf_s` se pokusí přečíst celý token do řetězce. Pokud zadaná velikost není dostatečně velký pro umístění celé token, nic se zapíšou do cílového řetězce. Pokud *šířka* pole není zadán, pak první *šířka* znaků v tokenu se zapíšou do cílového řetězce podél bez ukončovacího znaku null.

## <a name="the-size-prefix"></a>Velikost předpony

Volitelné předpony **h**, **l**, **ll**, **I64**, a **L** určení velikosti `argument`(long nebo short, jednobajtový znak nebo široký znak, v závislosti na typu znak, který mění). Tyto znaky specifikace formátu se používají s znaky typu v `scanf` nebo `wscanf` funkce zadejte interpretaci argumentů tak, jak je znázorněno v následující tabulce. Zadejte předponu **I64** je rozšířením společnosti Microsoft, který není ANSI kompatibilní. Znaky typů a jejich význam jsou popsané v tabulce "Zadejte pro funkce scanf – znaky" v [scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> **h**, **l**, a **L** předpony, které jsou rozšíření společnosti Microsoft při použití s daty typu `char`.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Předpony velikosti pro scanf a wscanf specifikátory formátu

|Chcete-li určit|Použijte předponu|Pomocí specifikátoru typu|
|----------------|----------------|-------------------------|
|**double**|**l**|**elektronické**, **E**, **f**, **g**, nebo **G**|
|**long double** (stejně jako double)|**L**|**elektronické**, **E**, **f**, **g**, nebo **G**|
|**Long int**|**l**|**d**, **můžu**, **o**, **x**, nebo **X**|
|**Long unsigned int**|**l**|**u**|
|**Long long**|**Vše**|**d**, **můžu**, **o**, **x**, nebo **X**|
|`short int`|**h**|**d**, **můžu**, **o**, **x**, nebo **X**|
|**krátký int bez znaménka**|**h**|**u**|
|__**int64**|**I64**|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|Jednobajtový znak s `scanf`|**h**|**c** nebo **C**|
|Jednobajtový znak s `wscanf`|**h**|**c** nebo **C**|
|Široký znak s `scanf`|**l**|**c** nebo **C**|
|Široký znak s `wscanf`|**l**|**c**, nebo **C**|
|Jednobajtové - řetězec znaků se `scanf`|**h**|**s** nebo **S**|
|Jednobajtové - řetězec znaků se `wscanf`|**h**|**s** nebo **S**|
|Širokoznaký řetězec s `scanf`|**l**|**s** nebo **S**|
|Širokoznaký řetězec s `wscanf`|**l**|**s** nebo **S**|

Následující příklady používají **h** a **l** s `scanf_s` funkce a `wscanf_s` funkce:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Pokud používáte nezabezpečené funkce v `scanf` řady, vynechejte parametr velikosti identifikující délku vyrovnávací paměti předchozí argumentu.

## <a name="reading-undelimited-strings"></a>Čtení Undelimited řetězce

Ke čtení řetězce není odděleny mezer znaky, sady znaků v hranatých závorkách (**[] č.**) mohou být nahrazeny **s** – znak typu (string). Množinu znaků v závorkách se označuje jako řetězec ovládacího prvku. Odpovídající vstupní pole je přečtěte si na první znak, který se nezobrazí v řetězci ovládacího prvku. Pokud je první znak v sadě stříšky (**^**), je obrácený efekt: vstupní pole je přečtěte si na první znak, který se zobrazí ve zbývající části znakovou sadu.

Všimněte si, že **% [-z]** a **% [z-a]** jsou interpretovány jako ekvivalentní **%[abcde...z]**. Toto je běžný `scanf` rozšíření funkce, ale Všimněte si, že standardu ANSI nevyžaduje.

## <a name="reading-unterminated-strings"></a>Neukončený čtení řetězce

Pro uložení řetězce bez uložení ukončující znak null ('\0'), použijte specifikaci **%** <em>n</em>**c** kde *n* je desítkové celé číslo. V takovém případě **c** – znak typu označuje, že argument je ukazatel na pole znaků. Další *n* znaky jsou čtení ze vstupního datového proudu do zadaného umístění a je připojena žádná znak null ('\0'). Pokud *n* není zadán, výchozí hodnota je 1.

## <a name="when-scanf-stops-reading-a-field"></a>Když scanf zastaví čtení pole

`scanf` Funkce zkontroluje každý vstupní pole znak po znaku. Může systém přestat čtení konkrétní vstupní pole předtím, než dosáhne znak mezery pro celou řadu důvodů:

- Byla dosažena zadaná šířka.

- Nelze převést na další znak uvedené.

- Na další znak je v konfliktu s znak v řetězci ovládací prvek, který by měl odpovídat.

- Další znak se nedaří se zobrazí v danou znakovou sadu.

Z jakéhokoli důvodu když `scanf` funkce zastaví čtení vstupního pole, další vstupní pole je považován za začít u prvního znaku nepřečtené. Konfliktní znak, pokud existuje, je považován za nepřečtené a je první znak další vstupní pole nebo první znak v další operacích čtení vstupního datového proudu.

## <a name="see-also"></a>Viz také

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Pole specifikace formátu: funkce scanf a wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
