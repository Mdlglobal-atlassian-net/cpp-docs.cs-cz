---
title: "Reprezentace plovoucí desetinné čárky IEEE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17fae0cbb16208d5c7e7346f354f3501e4803d96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ieee-floating-point-representation"></a>Reprezentace plovoucí desetinné čárky IEEE
Microsoft Visual C++ je konzistentní s číselné standardů IEEE. Existují tři typy interní reálná čísla. Skutečné\*4 a skutečné\*8 se používají v jazyce Visual C++. Skutečné\*4 je deklarováno s použitím slovo **float**. Skutečné\*8 je deklarováno s použitím slovo **dvojité**. V systému Windows 32-bit programování `long double` datový typ mapuje **dvojité**. Existuje, ale sestavení jazyková podpora pro výpočty pomocí skutečné * 10 datového typu.  
  
 Hodnoty jsou uloženy následujícím způsobem:  
  
|Hodnota|Uložené jako|  
|-----------|---------------|  
|Real * 4|podepsat bit, 8bitové exponent, mantisa 23 bitů|  
|Real * 8|podepsat bit, exponent 11 bitů, mantisa 52 bitů|  
|Real * 10|podepsat bit, exponent 15-bit, mantisa 64-bit|  
  
 V reálné * 4 a skutečné\*8 formátů, v mantisa, které nejsou uloženy v paměti, tak mantisy jsou ve skutečnosti 24 nebo 53 bits, i když se ukládají jenom 23 nebo 52 bits není předpokládané úvodní 1. Skutečné\*10 formátu ve skutečnosti ukládá tento bit.  
  
 O polovinu jejich možné hodnoty jsou tendenční exponenty. To znamená, že odečtena tento odchylka z uložené exponent získat skutečný exponent. Pokud uložené exponent je menší než posun, je ve skutečnosti záporné exponent.  
  
 Exponenty jsou tendenční následujícím způsobem:  
  
|Exponent|Tendenční podle|  
|--------------|---------------|  
|8bitové (real * 4)|127|  
|verze 11 (real * 8)|1023|  
|15-bit (real * 10)|16383|  
  
 Tyto exponenty nejsou pravomocí deset; jsou to zajišťuje dva. To znamená uložené exponenty 8bitové může být až 127 znaků. Hodnota 2 ** 127 je přibližně ekvivalentem 10\*\*38, což je skutečný limit reálné\*4.  
  
 Mantisa se ukládají jako binární zlomek formuláře 1.XXX.... Tato část obsahuje hodnotu větší než nebo rovno 1 a menší než 2. Všimněte si, že reálná čísla byly vždy uloženy ve normalizovaný formuláře; To znamená mantisa doleva přesunuty tak, aby vysokou bitem mantisa je vždy 1. Protože tato verze je vždy 1, předpokládá se (není uložené) v reálné * 4 a skutečné\*8 formáty. Binární (není desetinné číslo) bod se považuje právě napravo od začátku 1.  
  
 Formát, pak pro různé velikosti vypadá takto:  
  
|Formát|BYTE 1|BYTE 2|BYTE 3|BYTE 4|...|N BAJTŮ|  
|------------|------------|------------|------------|------------|---------|------------|  
|Real * 4|`SXXX XXXX`|`XMMM MMMM`|`MMMM MMMM`|`MMMM MMMM`|||  
|Real * 8|`SXXX XXXX`|`XXXX MMMM`|`MMMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
|Real * 10|`SXXX XXXX`|`XXXX XXXX`|`1MMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
  
 `S`představuje přihlašovací bit, `X`na jsou exponentu bits a `M`na jsou mantisa bits. Všimněte si, že krajní levé bit se předpokládá, že v reálném * 4 a skutečné\*8 formáty, ale je k dispozici jako "1" v bajtech 3 skutečných\*10 formátu.  
  
 Se posunou binární bodu správně, nejprve unbias exponent a přejdete binární bodu vpravo nebo ponecháno odpovídající počet bitů.  
  
## <a name="examples"></a>Příklady  
 Tady jsou některé příklady v reálném * 4 formátu:  
  
-   V následujícím příkladu je bit přihlašovací nula a uložené exponent je 128 nebo 100 0000 0 v binární soubor, který je 127 plus 1. Uložené mantisa je (1). 000 0000 ... 0000 0000, který má předpokládané úvodní 1 a binární bod, takže skutečné mantisa představuje jedno.  
  
    ```  
                        SXXX XXXX XMMM MMMM ... MMMM MMMM  
    2   =  1  * 2**1  = 0100 0000 0000 0000 ... 0000 0000 = 4000 0000  
    ```  
  
-   Stejné jako + 2 s tím rozdílem, že je nastaven bit přihlášení. To platí pro všechna čísla s plovoucí desetinnou čárkou IEEE formátu.  
  
    ```  
    -2  = -1  * 2**1  = 1100 0000 0000 0000 ... 0000 0000 = C000 0000  
    ```  
  
-   Stejné mantisa exponent zvýší o 1 (posunutého hodnota je 129 nebo 100 0000 1 v binární.  
  
    ```  
    4  =  1  * 2**2  = 0100 0000 1000 0000 ... 0000 0000 = 4080 0000  
    ```  
  
-   Stejné exponent mantisa je větší o polovinu – jeho (1). 100 0000... 0000 0000, který, protože to je binární zlomek, je 1. 1/2 (hodnoty míst za desetinnou čárkou jsou 1 nebo 2, 1/4, 1/8 a tak dále).  
  
    ```  
    6  = 1.5 * 2**2  = 0100 0000 1100 0000 ... 0000 0000 = 40C0 0000  
    ```  
  
-   Stejné exponent jako ostatní zajišťuje dvou mantisa je méně než dvě po jednom 127 nebo 011 1111 1 v binárním.  
  
    ```  
    1  = 1   * 2**0  = 0011 1111 1000 0000 ... 0000 0000 = 3F80 0000  
    ```  
  
-   Posunutého exponent je 126, 011 1111 0 v binární a mantisa je (1). 100 0000 ... 0000 0000, což je 1. 1/2.  
  
    ```  
    .75 = 1.5 * 2**-1 = 0011 1111 0100 0000 ... 0000 0000 = 3F40 0000  
    ```  
  
-   Stejně jako dva, kromě bit, který představuje 1/4 se nastavuje v mantisa.  
  
    ```  
    2.5 = 1.25 * 2**1 = 0100 0000 0010 0000 ... 0000 0000 = 4020 0000  
    ```  
  
-   1/10 je opakovaný zlomek v binární. Je právě tvy 1.6 mantisa a exponent posunutého říká, že se vydělí 16 1.6 (je 1 1101 011 v binární soubor, který je 123 v desítkové soustavě). Hodnota true, exponent je 123 127 = - 4, což znamená, že je koeficient, kterým se mají vynásobit 2 ** -4 = 1/16. Všimněte si, že je uložená mantisa zaokrouhlený nahoru v poslední bit – pokus o představují číslo unrepresentable jako přesně. (Z důvodu 1/10 a 1/100 nemusí přesně reprezentovat binární je podobná z důvodu, že 1/3 nemusí přesně reprezentovat decimal.)  
  
    ```  
    0.1 = 1.6 * 2**-4 = 0011 1101 1100 1100 ... 1100 1101 = 3DCC CCCD  
    ```  
  
-   `0  = 1.0 * 2**-128 = all zeros--a special case.`  
  
## <a name="see-also"></a>Viz také  
 [Proč čísla s plovoucí desetinnou čárkou můžou ztratit přesnost](../../build/reference/why-floating-point-numbers-may-lose-precision.md)