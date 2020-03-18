---
title: scanf – specifikace šířky
ms.date: 10/22/2019
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: ea0b2728021e3093ab7818af17e60c598f73587f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444708"
---
# <a name="scanf-width-specification"></a>scanf – specifikace šířky

Tyto informace se vztahují na výklad řetězců formátu v `scanf` rodině funkcí, včetně zabezpečených verzí, jako je `scanf_s`. Tyto funkce obvykle předpokládají, že vstupní datový proud je rozdělen do posloupnosti tokenů. Tokeny jsou odděleny prázdným znakem (mezera, tabulátor nebo nový řádek) nebo pro číselné typy, a to přirozenému konci číselného datového typu, který je označen prvním znakem, který nelze převést na číselný text. Nicméně specifikace šířky může být použita k tomu, aby se analýza vstupu zastavila před přirozeným koncem tokenu.

Specifikace *šířky* se skládá ze znaků mezi `%` a specifikátorem pole typu, které mohou zahrnovat kladné celé číslo s názvem pole *Width* a jeden nebo více znaků, které označují velikost pole, které lze také považovat za modifikátory typu pole, například označení, zda je celočíselný typ **krátký** nebo **dlouhý**. Tyto znaky jsou označovány jako předpona velikosti.

## <a name="the-width-field"></a>Pole Šířka

Pole *Šířka* je kladné desítkové celé číslo, které určuje maximální počet znaků, které mají být pro dané pole čteny. Nepřevádí a ukládají se do odpovídajících `argument`žádné znaky s více než *šířkou* . Pokud je před dosažením *šířky* prázdné znaky nebo znak, který nelze převést podle daného formátu, je možné číst méně než znaků *šířky* .

Specifikace šířky je oddělená a odlišná od argumentu velikosti vyrovnávací paměti vyžadovaného zabezpečenými verzemi těchto funkcí (například `scanf_s`, `wscanf_s`a tak dále). V následujícím příkladu je specifikace šířky 20, což značí, že ze vstupního streamu se mají číst až 20 znaků. Velikost vyrovnávací paměti je 21, což zahrnuje místo pro možné 20 znaků a ukončovací znak null:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Pokud se pole *Šířka* nepoužívá, `scanf_s` se pokusí přečíst celý token do řetězce. Pokud zadaná velikost není dostatečně velká pro uložení celého tokenu, nezapíše se do cílového řetězce nic. Pokud je zadáno pole *Šířka* , pak se znaky první *šířky* v tokenu zapisují do cílového řetězce spolu s ukončovacím znakem null.

## <a name="the-size-prefix"></a>Předpona velikosti

Volitelné předpony **h**, **HH**, **l**, **ll**, **I64**a **l** označují velikost `argument` (dlouhý nebo krátký, jednobajtové znak nebo velký znak v závislosti na tom, který typ znaku upravuje). Tyto znaky specifikace formátu se používají s znaky typu v `scanf` nebo `wscanf` funkce k určení interpretace argumentů, jak je znázorněno v následující tabulce. Předpona typu **I64** je rozšířením společnosti Microsoft a není kompatibilní se standardem C. Znaky typu a jejich význam jsou popsány v tabulce "Type Characters for scanf Functions" (znaky [pole typu scanf](../c-runtime-library/scanf-type-field-characters.md)).

> [!NOTE]
> Předpony **h**, **l**a **l** jsou rozšířeními společnosti Microsoft, pokud se používají s daty typu **char**.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Předpony velikosti pro specifikátory typu scanf a wscanf formátu

|Zadání|Použít předponu|Se specifikátorem typu|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**, **e**, **f**, **g**nebo **g**|
|**Long Double** (totéž jako Double)|**L**|**e**, **e**, **f**, **g**nebo **g**|
|**dlouhé celé číslo**|**l**|**d**, **i**, **o**, **x**nebo **x**|
|**dlouhé celé číslo bez znaménka**|**l**|**h**|
|**Long Long**|**vše**|**d**, **i**, **o**, **x**nebo **x**|
|**krátké celé číslo**|**y**|**d**, **i**, **o**, **x**nebo **x**|
|**krátké celé číslo bez znaménka**|**y**|**h**|
|**char**|**HH**|**d**, **i**, **o**, **x**nebo **x**|
|**znak bez znaménka**|**HH**|**h**|
|**Int64**|**I64**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|Jednobajtové znak s `scanf`|**y**|**c** nebo **c**|
|Jednobajtové znak s `wscanf`|**y**|**c** nebo **c**|
|Širší znak s `scanf`|**l**|**c** nebo **c**|
|Širší znak s `wscanf`|**l**|**c**nebo **c**|
|Řetězec znaků s jedním bajtem s `scanf`|**y**|**s** nebo **s**|
|Řetězec znaků s jedním bajtem s `wscanf`|**y**|**s** nebo **s**|
|Řetězec s velkým znakem s `scanf`|**l**|**s** nebo **s**|
|Řetězec s velkým znakem s `wscanf`|**l**|**s** nebo **s**|

Následující příklady používají **h** a **l** s `scanf_s` funkcí a `wscanf_s` funkcí:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Pokud používáte nezabezpečenou funkci v `scanf` rodině, vynechejte parametr size, který označuje délku vyrovnávací paměti předcházejícího argumentu.

## <a name="reading-undelimited-strings"></a>Čtení nevymezených řetězců

Pro čtení řetězců, které nejsou odděleny prázdnými znaky, lze pro znak typu **s** (String) nahradit sadu znaků v závorkách ( **[]** ). Sada znaků v závorkách je označována jako *řídicí řetězec*. Odpovídající vstupní pole je čteno do prvního znaku, který se nezobrazuje v řídicím řetězci. Pokud je první znak v sadě stříška ( **^** ), efekt je obrácený: vstupní pole je čteno na první znak, který se zobrazí ve zbývající části znakové sady.

**% [A-z]** i **% [z-a]** jsou interpretovány jako ekvivalent pro **% [abcde... z]** . Jedná se o běžné rozšíření `scanf` funkce, ale není vyžadováno standardem C.

## <a name="reading-unterminated-strings"></a>Čtení neukončených řetězců

Chcete-li uložit řetězec bez uložení ukončujícího znaku null (' \ 0 '), použijte specifikaci `%Nc`, kde *N* je desítkové celé číslo. V tomto případě znak typu **c** označuje, že argument je ukazatel na pole znaků. Následující *N* znaků je čten ze vstupního datového proudu do zadaného umístění a není připojen žádný znak null (' \ 0 '). Pokud není zadán *N* , jeho výchozí hodnota je 1.

## <a name="when-scanf-stops-reading-a-field"></a>Když scanf zastaví čtení pole

Funkce `scanf` kontroluje každé vstupní pole, znak po znaku. Před dosažením znaku mezery v jednom z několika důvodů může přestat číst konkrétní vstupní pole:

- Byla dosažena zadaná šířka.

- Následující znak nelze převést na zadaný.

- Další znak je v konfliktu se znakem v řetězci ovládacího prvku, který by měl odpovídat.

- Další znak se neobjeví v dané znakové sadě.

Z jakéhokoli důvodu, když funkce `scanf` zastaví čtení vstupního pole, je další vstupní pole považováno za začínající na první nepřečtený znak. Konfliktní znak, pokud existuje, je považován za nepřečtený. Je to první znak dalšího vstupního pole nebo první znak v následných operacích čtení na vstupním datovém proudu.

## <a name="see-also"></a>Viz také

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Pole specifikace formátu: funkce scanf a wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
