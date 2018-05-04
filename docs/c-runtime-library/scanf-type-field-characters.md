---
title: Znaky pole typu scanf | Microsoft Docs
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
ms.openlocfilehash: eb4c1c25c5b45fc967954ea78a35a9420b712f81
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="scanf-type-field-characters"></a>Znaky pole typu scanf
Následující informace platí pro žádné z `scanf` řadu funkcí, včetně zabezpečené verze, jako například `scanf_s`.  
  
 `type` Znak, který je jediným požadovaný formát pole; se zobrazí po všechna pole volitelné formátu. `type` Znak určuje, zda přidružené argument interpretována jako znak, řetězec nebo číslo.  
  
### <a name="type-characters-for-scanf-functions"></a>Pro funkce scanf – znaky typu  
  
|Znak|Typ vstupu očekávání|Typ argumentu|Argumentem velikosti v zabezpečené verzi?|  
|---------------|----------------------------|----------------------|--------------------------------------|  
|`c`|Znak. Při použití s `scanf` funkce, určuje znakovou; při použití s `wscanf` funkce, určuje široká znaková. Prázdné znaky, které jsou normálně přeskočeny při čtení `c` je zadán. Chcete-li si přečíst další znak jednobajtové prázdné znaky, použijte `%1s`; chcete přečíst další bez prázdného místa celý znak, použijte `%1ws`.|Ukazatel na `char` při použití s `scanf` funkce, ukazatel na `wchar_t` při použití s `wscanf` funkce.|Požadováno. Velikost nezahrnuje prostor pro zakončením hodnotu null.|  
|`C`|Opačným velikost znak. Při použití s `scanf` funkce, určuje široká znaková; při použití s `wscanf` funkce, určuje znakovou. Prázdné znaky, které jsou normálně přeskočeny při čtení `C` je zadán. Chcete-li si přečíst další znak jednobajtové prázdné znaky, použijte `%1s`; chcete přečíst další bez prázdného místa celý znak, použijte `%1ws`.|Ukazatel na `wchar_t` při použití s `scanf` funkce, ukazatel na `char` při použití s `wscanf` funkce.|Požadováno. Argument velikost nezahrnuje prostor pro zakončením hodnotu null.|  
|`d`|Desetinné číslo.|Ukazatel na `int`.|Ne.|  
|`i`|Celé číslo. Hexadecimální Pokud vstupní řetězec začíná řetězcem "0 x" nebo "0 X", osmičková, pokud řetězec začíná řetězcem "0", jinak decimal.|Ukazatel na `int`.|Ne.|  
|`o`|Osmičkové celé číslo.|Ukazatel na `int`.|Ne.|  
|`p`|Ukazatel adresa v šestnáctkové číslice. Maximální počet číslic, přečtěte si závisí na velikosti ukazatele (32 nebo 64 bitů), což závisí na architektuře počítače. "0 x" nebo "0 X", bude přijato jako předpony.|Ukazatel na `void*`.|Ne.|  
|`u`|Decimal celé číslo bez znaménka.|Ukazatel na `unsigned int`.|Ne.|  
|`x`|Hexadecimální celé číslo.|Ukazatel na `int`.|Ne.|  
|`e`, `E`, `f`, `F`, `g`, `G`|Skládající se z volitelné přihlášení s plovoucí desetinnou čárkou (+ nebo -), řadu jeden nebo více desetinných číslic obsahující desetinné čárky a volitelné exponent ("e" nebo "E"), za nímž následuje volitelně podepsaný celočíselnou hodnotu.|Ukazatel na `float`.|Ne.|  
|`a`, `A`|Který se skládá z řady jeden nebo více šestnáctkových číslic obsahující volitelné desetinné čárky a exponent ("p" nebo "P") následuje desítkové číslo s plovoucí desetinnou čárkou.|Ukazatel na `float`.|Ne.|  
|`n`|Žádný vstup číst z datového proudu nebo vyrovnávací paměti.|Ukazatel na `int`, do které uložené počet znaků je úspěšně číst z datového proudu nebo ukládat do vyrovnávací paměti až tento bod v aktuálním volání `scanf` funkce nebo `wscanf` funkce.|Ne.|  
|`s`|Řetězec, až do první prázdné znaky (místa, karta nebo nový řádek). Číst řetězce není oddělená mezery, použijte sadu hranaté závorky (`[ ]`), jak je popsáno v [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s `scanf` funkce, označuje, že pole znakovou; při použití s `wscanf` funkce, označuje, že široká charakterová pole. V obou případech musí být dostatečně velký pro vstupní pole a ukončující prázdný znak, který se automaticky připojí pole znaků.|Požadováno. Velikost zahrnuje místa pro zakončením hodnotu null.|  
|`S`|Velikost opak řetězec znaků, až do první prázdné znaky (místa, karta nebo nový řádek). Číst řetězce není oddělená mezery, použijte sadu hranaté závorky (`[ ]`), jak je popsáno v [specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md).|Při použití s `scanf` funkce, označuje, že pole široká charakterová; při použití s `wscanf` funkce, označuje, že jedním znaková pole. V obou případech musí být dostatečně velký pro vstupní pole a ukončující prázdný znak, který se automaticky připojí pole znaků.|Požadováno. Velikost zahrnuje místa pro zakončením hodnotu null.|  
  
  
 Velikost argumenty, v případě potřeby by měl v seznamu parametrů okamžitě následující argument, které se vztahují na předán. Například následující kód:  
  
```  
char string1[11], string2[9];  
scanf_s("%10s %8s", string1, 11, string2, 9);  
```  
  
 načte řetězec s délkou maximálně 10 do `string1`a řetězec s délkou maximálně 8 do `string2`. Velikost vyrovnávací paměti by měla být alespoň jeden více než specifikace šířky od místa musí být vyhrazeno pro ukončení hodnotu null.  
  
 Řetězec formátu dokáže zpracovat vstup jednobajtové nebo široké znak bez ohledu na to, zda je použit znakovou nebo široká charakterová verze funkce. Proto číst jednobajtové nebo široké znaky s `scanf` funkce a `wscanf` funkcí, použití specifikátorů formátu následujícím způsobem.  
  
|Číst znak jako|Tuto funkci můžete používat|Pomocí těchto specifikátory formátu|  
|--------------------------|-----------------------|----------------------------------|  
|jeden bajt|`scanf` Funkce|`c`, `hc`, nebo `hC`|  
|jeden bajt|`wscanf` Funkce|`C`, `hc`, nebo `hC`|  
|široký|`wscanf` Funkce|`c`, `lc`, nebo `lC`|  
|široký|`scanf` Funkce|`C`, `lc`, nebo `lC`|  
  
 Kontrola řetězce s `scanf` funkce, a `wscanf` funkce, pomocí typu specifikátory formátu v výše uvedené tabulce `s` a `S` místo `c` a `C`.  
  
## <a name="see-also"></a>Viz také  
 [scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)