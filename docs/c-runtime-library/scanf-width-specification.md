---
title: Specifikace šířky scanf
ms.date: 11/04/2016
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 3b00996f3a17ab9298b1edba5a8e60826e19fdcc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957351"
---
# <a name="scanf-width-specification"></a>Specifikace šířky scanf

Tyto informace se vztahují na výklad řetězců formátu v `scanf` rodině funkcí, včetně zabezpečených verzí `scanf_s`, jako je. Tyto funkce obvykle předpokládají, že vstupní datový proud je rozdělen do posloupnosti tokenů. Tokeny jsou odděleny prázdnými znaky (mezera, tabulátor nebo nový řádek) nebo v případě číselných typů přirozeným koncem číselného datového typu, který je označen prvním znakem, který nelze převést na číselný text. Nicméně specifikace šířky může být použita k tomu, aby se analýza vstupu zastavila před přirozeným koncem tokenu.

Specifikace *šířky* se skládá ze znaků mezi `%` specifikátorem a polem typu, které mohou zahrnovat kladné celé číslo s názvem pole *Width* a jeden nebo více znaků, které označují velikost pole, což může být také považuje se za modifikátory typu pole, jako je například označení, zda je celočíselný typ **krátký** nebo **dlouhý**. Tyto znaky jsou označovány jako předpona velikosti.

## <a name="the-width-field"></a>Pole Šířka

Pole *Šířka* je kladné desítkové celé číslo, které řídí maximální počet znaků, které mají být pro dané pole přečteny. Nejsou převáděny a uloženy na odpovídajícím `argument`místě žádné znaky s více než *šířkou* . Je-li znak, který nelze převést na základě daného formátu, před dosažením *šířky* , lze načíst méně než znaků *šířky* .

Specifikace šířky je oddělená a odlišná od argumentu velikosti vyrovnávací paměti vyžadovaného zabezpečenými verzemi těchto funkcí (tj. `scanf_s`, `wscanf_s`, atd.). V následujícím příkladu je specifikace šířky 20, což značí, že ze vstupního streamu se mají číst až 20 znaků. Velikost vyrovnávací paměti je 21, což zahrnuje místo pro možné 20 znaků a ukončovací znak null:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Pokud se pole *Width* nepoužívá, `scanf_s` pokusí se načíst celý token do řetězce. Pokud zadaná velikost není dostatečně velká pro uložení celého tokenu, nebude do cílového řetězce nic zapsáno. Pokud je zadáno pole *Šířka* , pak budou znaky první *šířky* v tokenu zapsány do cílového řetězce spolu s ukončovacím znakem null.

## <a name="the-size-prefix"></a>Předpona velikosti

Volitelné předpony **h**, **l**, **ll**, **I64** `argument` a **l** označují velikost (dlouhého nebo krátkého bajtového znaku nebo samostatného znaku v závislosti na tom, který typ znaku upravuje). Tyto znaky specifikace formátu se používají s znaky typu v `scanf` nebo `wscanf` k určení interpretace argumentů, jak je znázorněno v následující tabulce. Předpona typu **I64** je rozšířením společnosti Microsoft a není kompatibilní se standardem ANSI. Znaky typu a jejich význam jsou popsány v tabulce "Type Characters for scanf Functions" (znaky [pole typu scanf](../c-runtime-library/scanf-type-field-characters.md)).

> [!NOTE]
> Předpony **h**, **l**a **l** jsou rozšířeními společnosti Microsoft, pokud se používají s daty `char`typu.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Předpony velikosti pro specifikátory typu scanf a wscanf formátu

|Zadání|Použít předponu|Se specifikátorem typu|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**, **e**, **f**, **g**nebo **g**|
|**Long Double** (stejné jako Double)|**L**|**e**, **e**, **f**, **g**nebo **g**|
|**dlouhé celé číslo**|**l**|**d**, **i**, **o**, **x**nebo **x**|
|**dlouhé celé číslo bez znaménka**|**l**|**u**|
|**Long Long**|**vše**|**d**, **i**, **o**, **x**nebo **x**|
|`short int`|**h**|**d**, **i**, **o**, **x**nebo **x**|
|**krátké celé číslo bez znaménka**|**h**|**u**|
|__**int64**|**I64**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|Jednobajtové znak s`scanf`|**h**|**c** nebo **c**|
|Jednobajtové znak s`wscanf`|**h**|**c** nebo **c**|
|Širší znak s`scanf`|**l**|**c** nebo **c**|
|Širší znak s`wscanf`|**l**|**c**nebo **c**|
|Řetězec s jedním bajtem a znakem`scanf`|**h**|**s** nebo **s**|
|Řetězec s jedním bajtem a znakem`wscanf`|**h**|**s** nebo **s**|
|Řetězec s velkým znakem s`scanf`|**l**|**s** nebo **s**|
|Řetězec s velkým znakem s`wscanf`|**l**|**s** nebo **s**|

Následující příklady používají **h** a **l** s `scanf_s` funkcemi a `wscanf_s` funkcemi:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Pokud používáte nezabezpečenou funkci v `scanf` rodině, vynechejte parametr size, který označuje délku vyrovnávací paměti předcházejícího argumentu.

## <a name="reading-undelimited-strings"></a>Čtení nevymezených řetězců

Pro čtení řetězců, které nejsou odděleny prázdnými znaky, lze pro znak typu **s** (String) nahradit sadu znaků v závorkách ( **[]** ). Sada znaků v závorkách je označována jako řídicí řetězec. Odpovídající vstupní pole je čteno s prvním znakem, který se nezobrazuje v řídicím řetězci. Pokud je první znak v sadě stříška ( **^** ), efekt je obrácený: Vstupní pole je čteno do prvního znaku, který se zobrazí ve zbývající části znakové sady.

Všimněte si, že **% [a-z]** a **% [z-a]** jsou interpretovány jako ekvivalent pro **% [abcde... z]** . Toto je společná `scanf` přípona funkce, ale standard ANSI je nepožaduje.

## <a name="reading-unterminated-strings"></a>Čtení neukončených řetězců

Chcete-li uložit řetězec bez uložení ukončujícího znaku null (' \ 0 '), použijte specifikaci **%** <em>n</em>**c** , kde *n* je desítkové celé číslo. V tomto případě znak typu **c** označuje, že argument je ukazatel na pole znaků. Následující *n* znaků je čten ze vstupního datového proudu do zadaného umístění a není připojen žádný znak null (' \ 0 '). Pokud není zadán parametr *n* , jeho výchozí hodnota je 1.

## <a name="when-scanf-stops-reading-a-field"></a>Když scanf zastaví čtení pole

`scanf` Funkce vyhledá každé vstupní pole znak po znaku. Před dosažením znaku mezery z nejrůznějších důvodů může přestat číst konkrétní vstupní pole:

- Byla dosažena zadaná šířka.

- Následující znak nelze převést na zadaný.

- Další znak je v konfliktu se znakem v řetězci ovládacího prvku, který by měl odpovídat.

- Další znak se neobjeví v dané znakové sadě.

Z jakéhokoli důvodu, když `scanf` funkce zastaví čtení vstupního pole, je další vstupní pole považováno za začínající na první nepřečtený znak. Konfliktní znak, pokud existuje, je považován za nepřečtený a je prvním znakem dalšího vstupního pole nebo prvním znakem v následných operacích čtení na vstupním datovém proudu.

## <a name="see-also"></a>Viz také:

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Pole specifikace formátu: funkce scanf a wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
