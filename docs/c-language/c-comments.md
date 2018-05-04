---
title: Komentáře v jazyce C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3a6c2d32596aa8205d02ee5cddb28b5ba3c8166
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-comments"></a>Komentáře v jazyce C
"Komentář" je posloupnost znaků počínaje kombinaci dopředné lomítko/hvězdičky (<b>/\*</b>), je považován za jeden prázdný znak kompilátorem a v opačném případě je ignorováno. Komentář může obsahovat libovolnou kombinaci znaků z reprezentovat znaková sada, včetně znaky nového řádku, s výjimkou oddělovač "ukončení komentáře" (<b>\*/</b>). Komentáře mohou zaujímat více než jeden řádek, ale nelze je vnořovat.  
  
 Komentáře se mohou vyskytovat kdekoliv, kde je povolen prázdný znak. Protože kompilátor považuje komentáře za jeden prázdný znak, nelze komentáře zadávat v tokenech. Kompilátor ignoruje znaky v komentáři.  
  
 Komentáře lze použít k dokumentaci kódu. Tento příklad je komentář, který kompilátor přijímá:  
  
```  
/* Comments can contain keywords such as  
   for and while without generating errors. */  
```  
  
 Komentáře se mohou vyskytovat na stejném řádku, na kterém se vyskytuje příkaz kódu:  
  
```  
printf( "Hello\n" );  /* Comments can go here */  
```  
  
 Funkcím nebo modulům programu mohou předcházet popisné bloky komentáře:  
  
```  
/* MATHERR.C illustrates writing an error routine   
 * for math functions.   
 */   
```  
  
 Protože nemohou komentáře nemohou vnořené komentáře, tento příklad způsobí chybu:  
  
```  
/* Comment out this routine for testing   
  
   /* Open file */  
    fh = _open( "myfile.c", _O_RDONLY );  
    .  
    .  
    .  
 */  
```  
  
 K této chybě dochází, protože kompilátor rozpozná první znak `*/` za slovy `Open file` jako konec komentáře. Pokusí se zpracovat zbývající text a po nalezení znaku `*/` mimo komentář vygeneruje chybu.  
  
 Ačkoli lze komentáře použít k deaktivaci určitých řádků kódu za účelem testování, jsou užitečnou alternativou pro tento úkol direktivy preprocesoru `#if` a `#endif` a podmíněné kompilace. Další informace najdete v tématu [direktivy pro preprocesor](../preprocessor/preprocessor-directives.md) v *preprocesor odkaz*.  
  
 **Konkrétní Microsoft**  
  
 Kompilátor Microsoft také podporuje jeden řádek komentáře před sebou dvě lomítka (**//**). Je-li program kompilován s možností /Za (standard ANSI), vygenerují tyto komentáře chyby. Tyto komentáře nemohou přesahovat na druhý řádek.  
  
```  
// This is a valid comment  
```  
  
 Komentáře počínaje dvě lomítka (**//**) se ukončila příkazem další znak nového řádku, který není sebou řídicí znak. V dalším příkladu, znak nového řádku předchází zpětné lomítko (**\\**), vytváření "– řídicí sekvence." Díky této řídicí sekvenci kompilátor považuje další řádek za součást předchozího řádku. (Další informace najdete v tématu [řídicí sekvence](../c-language/escape-sequences.md).)  
  
```  
// my comment \  
    i++;   
```  
  
 Příkaz `i++;` je proto zakomentován.  
  
 Výchozí nastavení pro Microsoft C je, že jsou povolené rozšíření Microsoft. Chcete-li tato rozšíření zakázat, použijte možnost /Za.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Tokeny jazyka C](../c-language/c-tokens.md)
