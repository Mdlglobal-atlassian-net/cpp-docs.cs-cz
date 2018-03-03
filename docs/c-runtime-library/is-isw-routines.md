---
title: "je, isw – rutiny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- isw
- is
dev_langs:
- C++
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa1cc76bf925a334b78e5f15565c089081cfe9d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="is-isw-routines"></a>is, isw – rutiny
|||  
|-|-|  
|[isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|  
|[isalpha, iswalpha, _isalpha_l, _iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|  
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower, iswlower, _islower_l, _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|  
|[isblank, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint, iswprint, _isprint_l, _iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|  
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|  
|[iscsym –, iscsymf –, __iscsym –, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l –](../c-runtime-library/reference/iscsym-functions.md)|[isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|  
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|  
|[isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|  
  
## <a name="remarks"></a>Poznámky  
 Tyto rutiny test znaků pro zadaných podmínek.  
  
 **Je** rutiny vytvořit smysluplný výsledky pro některý argument celé číslo od -1 (`EOF`) k **uchar_max –** (0xFF), včetně. Typ očekávaný argument je `int`.  
  
> [!CAUTION]
>  Pro **je** rutiny, předáním argumentu typu `char` mohou vést k neočekávaným výsledkům. Jednobajtové znak SBCS nebo MBCS typu `char` s hodnotou vyšší než 0x7F je záporná. Pokud `char` je předán, kompilátor může převést hodnotu přihlášeni `int` nebo přihlášeni **dlouho**. Tato hodnota může být rozšířeny kompilátorem s neočekávaným výsledkům.  
  
 **Isw** rutiny vytvořit smysluplný výsledky pro jakékoli celé číslo od - 1 (**weof –**) k 0xFFFF (včetně). **Wint_t –** datový typ je definována v WCHAR. H jako **nepodepsané prostě**; může uchovávat všechny wide znak nebo na široká charakterová koncoví souboru (**weof –**) hodnotu.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná.  
  
 V národním prostředí "C", test podmínky pro **je** rutiny jsou následující:  
  
 `isalnum`  
 Alfanumerické znaky (A – Z, a - z nebo 0 - 9).  
  
 `isalpha`  
 Abecední znaky (A - Z nebo a - z).  
  
 `__isascii`  
 Znaků ASCII (0x00 – 0x7F).  
  
 `isblank`  
 Vodorovné nebo mezerou znak (0x09 nebo 0x20).  
  
 `iscntrl`  
 Řízení znak (0x00-0x1F nebo 0x7F).  
  
 `__iscsym`  
 Písmeno, podtržítko nebo číslice.  
  
 `__iscsymf`  
 Písmenem nebo podtržítkem.  
  
 **IsDigit –**  
 Desítková číslice (0 - 9).  
  
 `isgraph`  
 Tisknutelná znaku kromě (místa).  
  
 `islower`  
 Malé písmeno (a – ž).  
  
 `isprint`  
 Tisknutelná znak včetně znaků (0x20 - 0x7E).  
  
 `ispunct`  
 Interpunkční znaménko.  
  
 `isspace`  
 Prázdné znaky (0x09-0x0D nebo 0x20).  
  
 `isupper`  
 Velké písmeno (A – Ž).  
  
 `isxdigit`  
 Šestnáctková číslice (A - F, a - f, nebo 0 - 9).  
  
 Pro **isw** rutiny, výsledkem testu pro zadanou podmínku je nezávislé na národním prostředí. Test podmínky pro **isw** funkce jsou následující:  
  
 `iswalnum`  
 `iswalpha`nebo `iswdigit`.  
  
 `iswalpha`  
 Všechny wide znak, který je jedním z sadu definované implementací, pro které žádný z `iswcntrl`, `iswdigit`, `iswpunct`, nebo `iswspace` nenulový. `iswalpha`vrátí nenulovou hodnotu pouze pro široké znaky pro kterou `iswupper` nebo `iswlower` nenulový.  
  
 `iswascii`  
 Široká charakterová reprezentace znaků ASCII (0x0000 - 0x007F).  
  
 `iswblank`  
 Celý znak, odpovídá standardní znak nebo je jedním z definované implementací sadu široké znaky, pro kterou `iswalnum` je false. Standardní prázdné znaky jsou místa (L "") a vodorovné karty (L "\t").  
  
 `iswcntrl`  
 Široká znaková ovládacího prvku.  
  
 **__iswcsym –**  
 Všechny wide znak, pro který **isalnum –** hodnotu true, nebo je znak "_".  
  
 **__iswcsymf –**  
 Všechny wide znak, pro který `iswalpha` hodnotu true, nebo je znak "_".  
  
 `iswctype`  
 Znak má vlastnost určeného `desc` argument. Pro každý platná hodnota `desc` argument `iswctype`, jak je znázorněno v následující tabulce je rutiny ekvivalentní široká charakterová klasifikace:  
  
 **Ekvivalence (iswctype –**   
 ***c, desc* ) do jiné isw – rutiny testování**  
  
|Hodnota *desc* argument|iswctype – ( *c, desc* ) ekvivalentní|  
|------------------------------|----------------------------------------|  
|**ÚROVNĚ _ALPHA**|**iswalpha – (** `c` **)**|  
|**ÚROVNĚ _ALPHA** &#124; **_DIGIT**|**iswalnum – (** `c` **)**|  
|**_BLANK**|**iswblank (** `c` **)**|  
|**_CONTROL**|**iswcntrl – (** `c` **)**|  
|**_DIGIT**|**iswdigit – (** `c` **)**|  
|**ÚROVNĚ _ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph – (** `c` **)**|  
|**_LOWER**|**iswlower – (** `c` **)**|  
|**ÚROVNĚ _ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint – (** `c` **)**|  
|**_PUNCT**|**iswpunct – (** `c` **)**|  
|**_BLANK**|**iswblank (** `c` **)**|  
|**_SPACE**|**iswspace – (** `c` **)**|  
|**_UPPER**|**iswupper – (** `c` **)**|  
|**_HEX**|**iswxdigit – (** `c` **)**|  
  
 `iswdigit`  
 Široká znaková odpovídající znaku desetinných číslic.  
  
 `iswgraph`  
 Tisknutelná široké znaku kromě místa celý znak (L "").  
  
 `iswlower`  
 Malé písmeno, nebo jeden z definované implementací sadu široké znaky pro které žádný z `iswcntrl`, `iswdigit`, `iswpunct`, nebo `iswspace` nenulový. `iswlower`vrátí nenulovou hodnotu pouze pro široké znaky, které odpovídají na malá písmena.  
  
 `iswprint`  
 Tisknutelná široká znaková, včetně místa celý znak (L "").  
  
 `iswpunct`  
 Tisknutelná široké znak, který je ani místa celý znak (L ".) ani celý znak, pro kterou `iswalnum` nenulový.  
  
 `iswspace`  
 Celý znak, odpovídá standardní prázdný znak nebo je jedním z definované implementací sadu široké znaky pro kterou `iswalnum` je false. Standardní prázdné znaky jsou: místa (L ""), formfeed (L '\f'), nový řádek (L '\n'), CR (L '\r'), vodorovné karta (L "\t") a vertikální tabulátor (L '\v').  
  
 `iswupper`  
 Celý znak, je velká nebo je jedním z definované implementací sadu široké znaky, pro které žádný z `iswcntrl`, `iswdigit`, `iswpunct`, nebo `iswspace` nenulový. `iswupper`vrátí nenulovou hodnotu pouze pro široké znaky, které odpovídají na velká písmena.  
  
 `iswxdigit`  
 Široká znaková, která odpovídá znak hexadecimální číslice.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_isfam.c  
/* This program tests all characters between 0x0  
 * and 0x7F, then displays each character with abbreviations  
 * for the character-type codes that apply.  
 */  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   for( ch = 0; ch <= 0x7F; ch++ )  
   {  
      printf( "%.2x  ", ch );  
      printf( " %c", isprint( ch )  ? ch   : ' ' );  
      printf( "%4s", isalnum( ch )  ? "AN" : "" );  
      printf( "%3s", isalpha( ch )  ? "A"  : "" );  
      printf( "%3s", __isascii( ch )  ? "AS" : "" );  
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );  
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );  
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );  
      printf( "%3s", isdigit( ch )  ? "D"  : "" );  
      printf( "%3s", isgraph( ch )  ? "G"  : "" );  
      printf( "%3s", islower( ch )  ? "L"  : "" );  
      printf( "%3s", ispunct( ch )  ? "PU" : "" );  
      printf( "%3s", isspace( ch )  ? "S"  : "" );  
      printf( "%3s", isprint( ch )  ? "PR" : "" );  
      printf( "%3s", isupper( ch )  ? "U"  : "" );  
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );  
      printf( ".\n" );  
   }  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
00            AS  C                              .  
01            AS  C                              .  
02            AS  C                              .  
03            AS  C                              .  
04            AS  C                              .  
05            AS  C                              .  
06            AS  C                              .  
07            AS  C                              .  
08            AS  C                              .  
09            AS  C                    S         .  
0a            AS  C                    S         .  
0b            AS  C                    S         .  
0c            AS  C                    S         .  
0d            AS  C                    S         .  
0e            AS  C                              .  
0f            AS  C                              .  
10            AS  C                              .  
11            AS  C                              .  
12            AS  C                              .  
13            AS  C                              .  
14            AS  C                              .  
15            AS  C                              .  
16            AS  C                              .  
17            AS  C                              .  
18            AS  C                              .  
19            AS  C                              .  
1a            AS  C                              .  
1b            AS  C                              .  
1c            AS  C                              .  
1d            AS  C                              .  
1e            AS  C                              .  
1f            AS  C                              .  
20            AS                       S PR      .  
21   !        AS              G    PU    PR      .  
22   "        AS              G    PU    PR      .  
23   #        AS              G    PU    PR      .  
24   $        AS              G    PU    PR      .  
25   %        AS              G    PU    PR      .  
26   &        AS              G    PU    PR      .  
27   '        AS              G    PU    PR      .  
28   (        AS              G    PU    PR      .  
29   )        AS              G    PU    PR      .  
2a   *        AS              G    PU    PR      .  
2b   +        AS              G    PU    PR      .  
2c   ,        AS              G    PU    PR      .  
2d   -        AS              G    PU    PR      .  
2e   .        AS              G    PU    PR      .  
2f   /        AS              G    PU    PR      .  
30   0  AN    AS   CS      D  G          PR     X.  
31   1  AN    AS   CS      D  G          PR     X.  
32   2  AN    AS   CS      D  G          PR     X.  
33   3  AN    AS   CS      D  G          PR     X.  
34   4  AN    AS   CS      D  G          PR     X.  
35   5  AN    AS   CS      D  G          PR     X.  
36   6  AN    AS   CS      D  G          PR     X.  
37   7  AN    AS   CS      D  G          PR     X.  
38   8  AN    AS   CS      D  G          PR     X.  
39   9  AN    AS   CS      D  G          PR     X.  
3a   :        AS              G    PU    PR      .  
3b   ;        AS              G    PU    PR      .  
3c   <        AS              G    PU    PR      .  
3d   =        AS              G    PU    PR      .  
3e   >        AS              G    PU    PR      .  
3f   ?        AS              G    PU    PR      .  
40   @        AS              G    PU    PR      .  
41   A  AN  A AS   CS CSF     G          PR  U  X.  
42   B  AN  A AS   CS CSF     G          PR  U  X.  
43   C  AN  A AS   CS CSF     G          PR  U  X.  
44   D  AN  A AS   CS CSF     G          PR  U  X.  
45   E  AN  A AS   CS CSF     G          PR  U  X.  
46   F  AN  A AS   CS CSF     G          PR  U  X.  
47   G  AN  A AS   CS CSF     G          PR  U   .  
48   H  AN  A AS   CS CSF     G          PR  U   .  
49   I  AN  A AS   CS CSF     G          PR  U   .  
4a   J  AN  A AS   CS CSF     G          PR  U   .  
4b   K  AN  A AS   CS CSF     G          PR  U   .  
4c   L  AN  A AS   CS CSF     G          PR  U   .  
4d   M  AN  A AS   CS CSF     G          PR  U   .  
4e   N  AN  A AS   CS CSF     G          PR  U   .  
4f   O  AN  A AS   CS CSF     G          PR  U   .  
50   P  AN  A AS   CS CSF     G          PR  U   .  
51   Q  AN  A AS   CS CSF     G          PR  U   .  
52   R  AN  A AS   CS CSF     G          PR  U   .  
53   S  AN  A AS   CS CSF     G          PR  U   .  
54   T  AN  A AS   CS CSF     G          PR  U   .  
55   U  AN  A AS   CS CSF     G          PR  U   .  
56   V  AN  A AS   CS CSF     G          PR  U   .  
57   W  AN  A AS   CS CSF     G          PR  U   .  
58   X  AN  A AS   CS CSF     G          PR  U   .  
59   Y  AN  A AS   CS CSF     G          PR  U   .  
5a   Z  AN  A AS   CS CSF     G          PR  U   .  
5b   [        AS              G    PU    PR      .  
5c   \        AS              G    PU    PR      .  
5d   ]        AS              G    PU    PR      .  
5e   ^        AS              G    PU    PR      .  
5f   _        AS   CS CSF     G    PU    PR      .  
60   `        AS              G    PU    PR      .  
61   a  AN  A AS   CS CSF     G  L       PR     X.  
62   b  AN  A AS   CS CSF     G  L       PR     X.  
63   c  AN  A AS   CS CSF     G  L       PR     X.  
64   d  AN  A AS   CS CSF     G  L       PR     X.  
65   e  AN  A AS   CS CSF     G  L       PR     X.  
66   f  AN  A AS   CS CSF     G  L       PR     X.  
67   g  AN  A AS   CS CSF     G  L       PR      .  
68   h  AN  A AS   CS CSF     G  L       PR      .  
69   i  AN  A AS   CS CSF     G  L       PR      .  
6a   j  AN  A AS   CS CSF     G  L       PR      .  
6b   k  AN  A AS   CS CSF     G  L       PR      .  
6c   l  AN  A AS   CS CSF     G  L       PR      .  
6d   m  AN  A AS   CS CSF     G  L       PR      .  
6e   n  AN  A AS   CS CSF     G  L       PR      .  
6f   o  AN  A AS   CS CSF     G  L       PR      .  
70   p  AN  A AS   CS CSF     G  L       PR      .  
71   q  AN  A AS   CS CSF     G  L       PR      .  
72   r  AN  A AS   CS CSF     G  L       PR      .  
73   s  AN  A AS   CS CSF     G  L       PR      .  
74   t  AN  A AS   CS CSF     G  L       PR      .  
75   u  AN  A AS   CS CSF     G  L       PR      .  
76   v  AN  A AS   CS CSF     G  L       PR      .  
77   w  AN  A AS   CS CSF     G  L       PR      .  
78   x  AN  A AS   CS CSF     G  L       PR      .  
79   y  AN  A AS   CS CSF     G  L       PR      .  
7a   z  AN  A AS   CS CSF     G  L       PR      .  
7b   {        AS              G    PU    PR      .  
7c   |        AS              G    PU    PR      .  
7d   }        AS              G    PU    PR      .  
7e   ~        AS              G    PU    PR      .  
7f            AS  C                              .  
```  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../c-runtime-library/character-classification.md)   
 [Národní prostředí](../c-runtime-library/locale.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Výklad sekvencí vícebajtových znaků](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [to – funkce](../c-runtime-library/to-functions.md)