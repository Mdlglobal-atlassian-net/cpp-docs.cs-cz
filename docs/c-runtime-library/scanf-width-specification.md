---
title: Specifikace šířky scanf | Microsoft Docs
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
ms.openlocfilehash: f0052f4b270366b2f3aa1e1550f790efcb860597
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418195"
---
# <a name="scanf-width-specification"></a>Specifikace šířky scanf
Tyto informace platí pro interpretaci řetězce formátu v `scanf` řadu funkcí, včetně zabezpečené verze, jako například `scanf_s`. Tyto funkce normálně předpokládají, že vstupní datový proud je rozdělené do pořadí tokenů. Tokeny jsou oddělené prázdné znaky (mezera, tabulátor nebo nový řádek), nebo v případě číselné typy přirozené konec číselný datový typ podle prvního znaku, který nelze převést na číselné text. Specifikace šířky lze však způsobit analýza vstupu k zastavení před přirozené koncem token.  
  
 *Šířka* specifikace obsahuje znaky mezi `%` a specifikátor typu pole, které mohou zahrnovat kladné celé číslo volat *šířka* pole a jeden nebo více znaků označující velikost pole, které mohou být považovány také modifikátory typ pole, jako je například údaj o tom, jestli je typ integer **krátké** nebo **dlouho**. Tyto znaky se označují jako předponu velikost.  
  
## <a name="the-width-field"></a>Šířka pole  
 *Šířka* pole je celé kladné desetinné číslo řízení maximální počet znaků čtení pro toto pole. Více než *šířka* znaky jsou převést a uložit na odpovídající `argument`. Méně než *šířka* znaky mohou být přečíst, pokud prázdný znak (mezera, tabulátor nebo nový řádek) nebo znak, který nelze převést podle dané formát dojde před *šířka* je dosaženo.  
  
 Specifikace šířky je zvláštní a odlišný od argumentu velikost vyrovnávací paměti vyžaduje bezpečné verze těchto funkcí (tj, `scanf_s`, `wscanf_s`atd.). V následujícím příkladu je specifikace šířky 20, což indikuje, že až 20 znaků jsou čtení ze vstupního datového proudu. Délka vyrovnávací paměti je 21, která zahrnuje prostor pro možný 20 znaků plus null ukončení:  
  
```  
char str[21];  
scanf_s("%20s", str, 21);  
```  
  
 Pokud *šířka* pole se nepoužívá, `scanf_s` se pokusí přečíst celou token do řetězce. Pokud zadaná velikost není dostatečně velký pro uložení celé token, nic se zapíšou do cílový řetězec. Pokud *šířka* pole je zadán, pak první *šířka* znaků v tokenu se zapíšou do cílový řetězec spolu s hodnotou null ukončení.  
  
## <a name="the-size-prefix"></a>Předpona velikost  
 Volitelné předpony **h**, **l**, **udou**, **I64**, a **L** znamenat velikost `argument`(dlouhé nebo krátké, znakovou nebo široká znaková, v závislosti na typu znak, který se upravit). Tyto specifikace formátu znaky se používají s znaky typu v `scanf` nebo `wscanf` funkce k určení výklad argumenty, jak je znázorněno v následující tabulce. Zadejte předponu **I64** je rozšíření Microsoft a není ANSI kompatibilní. Znaky typu a jejich významy jsou popsané v tabulce "Typ znaků pro funkce scanf" v [znaky pole typu scanf](../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  **h**, **l**, a **L** jsou předpony rozšíření Microsoft při použití s daty typu `char`.  
  
### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Velikost předpon pro scanf a wscanf specifikátory typ formátu  
  
|Chcete-li určit|Použijte předponu|Pomocí specifikace typu|  
|----------------|----------------|-------------------------|  
|**double**|**l**|**e**, **E**, **f**, **g**, nebo **G**|  
|**long double** (stejné jako dvojité)|**L**|**e**, **E**, **f**, **g**, nebo **G**|  
|**dlouhé int**|**l**|**d**, **i**, **o**, **x**, nebo **X**|  
|**int dlouho bez znaménka**|**l**|**u**|  
|**dlouhé dlouho**|**Le**|**d**, **i**, **o**, **x**, nebo **X**|  
|`short int`|**h**|**d**, **i**, **o**, **x**, nebo **X**|  
|**krátká celočíselná bez znaménka**|**h**|**u**|  
|__**int64**|**I64**|**d**, **i**, **o**, **u**, **x**, nebo **X**|  
|Znakovou s `scanf`|**h**|**c** nebo **C**|  
|Znakovou s `wscanf`|**h**|**c** nebo **C**|  
|Široká znaková s `scanf`|**l**|**c** nebo **C**|  
|Široká znaková s `wscanf`|**l**|**c**, nebo **C**|  
|Jednobajtové - řetězec znaků se `scanf`|**h**|**s** nebo **S**|  
|Jednobajtové - řetězec znaků se `wscanf`|**h**|**s** nebo **S**|  
|Široká charakterová řetězec s `scanf`|**l**|**s** nebo **S**|  
|Široká charakterová řetězec s `wscanf`|**l**|**s** nebo **S**|  
  
 Následující příklady použití **h** a **l** s `scanf_s` funkce a `wscanf_s` funkce:  
  
```  
scanf_s("%ls", &x, 2);     // Read a wide-character string  
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character  
```  
  
 Pokud používáte nezabezpečená funkce v `scanf` rodiny, vynechejte parametr velikost označující délka vyrovnávací paměti předchozí argumentu.  
  
## <a name="reading-undelimited-strings"></a>Čtení Undelimited řetězce  
 Číst řetězce není oddělená prázdné znaky, sadu znaků do hranatých závorek (**[]**) můžete nahradit **s** – znak typu (string). Sadu znaků v závorkách se označuje jako řetězec ovládacího prvku. Odpovídající vstupní pole je zobrazeno na první znak, který se nenachází v řetězci ovládacího prvku. Pokud je první znak v sadě šipka nahoru (**^**), je obrácený účinek: vstupní pole je ke čtení na první znak, který se zobrazí ve zbývající části znaková sada.  
  
 Všimněte si, že **% [-z]** a **% [z-a]** , jsou považovány za ekvivalentní **%[abcde...z]**. Toto je společného `scanf` rozšíření funkce, ale Všimněte si, že standardu ANSI nevyžaduje ho.  
  
## <a name="reading-unterminated-strings"></a>Čtení neukončený řetězce  
 Chcete-li uložit řetězec bez ukládání ukončující znak hodnoty null ('\0'), použijte specifikace `%` *n *** c** kde *n* desetinné číslo. V takovém případě **c** – znak typu označuje, že je argumentem ukazatel na pole znaků. Další *n* znaků se načítají z vstupního datového proudu do zadaného umístění a je připojeno žádné znak hodnoty null ('\0'). Pokud *n* není určena, výchozí hodnota je 1.  
  
## <a name="when-scanf-stops-reading-a-field"></a>Když se zastaví čtení pole scanf  
 `scanf` Funkce kontroluje každý vstupní pole po znacích. Může zastavit, čtení konkrétní vstupní pole, než dorazí do místa znak z různých důvodů:  
  
-   Nastavená šířka byl dosažen.  
  
-   Nelze převést na další znak uvedené.  
  
-   Pro další znak v konfliktu s znak v řetězci ovládací prvek, který by měl odpovídat.  
  
-   Další znak se nedaří se zobrazí v daném znakovou sadu.  
  
 Z jakéhokoliv důvodu když `scanf` funkce zastaví čtení vstupního pole, další vstupní pole považuje zahájíte u prvního znaku nepřečtená. Konfliktní znaku, pokud je jedna, je považován za nepřečtená a první znak další vstupní pole nebo první znak v následných operací čtení na vstupního datového proudu.  
  
## <a name="see-also"></a>Viz také  
 [scanf, _scanf_l –, wscanf, _wscanf_l –](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [Pole Specifikace formátu: funkce scanf a wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)   
 [scanf – znaky pole typu](../c-runtime-library/scanf-type-field-characters.md)