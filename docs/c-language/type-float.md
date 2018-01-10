---
title: Typ float | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0b1362d5cb0451f5190ca63ab0344f557256190
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-float"></a>Float – typ
Čísla s plovoucí desetinnou čárkou použijte formát IEEE (Institute of Electrical and Electronics Engineers). Hodnoty jednoduchou přesností s typ float mají 4 bajtů, skládající se z přihlašovací bit, exponentem binární nad 127 8bitové a mantisa 23 bitů. Mantisa představuje číslo mezi 1.0 a 2.0. Vzhledem k tomu, že vysoce bitem mantisa je vždy 1, se neukládají v číslo. Tento zápis poskytuje řadu přibližně 3.4E-38 3.4E + 38 pro typ float.  
  
 Proměnné můžou deklarovat jako float nebo double, v závislosti na potřebách vaší aplikace. Hlavní rozdíly mezi těmito dvěma typy jsou význam, které mohou představovat, úložiště, které vyžadují a jejich rozsah. Následující tabulka ukazuje vztah mezi násobek a požadavky na úložiště.  
  
### <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou  
  
|Typ|Platných číslic|Počet bajtů|  
|----------|------------------------|---------------------|  
|float|6 - 7|4|  
|double|15 - 16|8|  
  
 Proměnné s plovoucí desetinnou čárkou jsou reprezentované pomocí mantisa, která obsahuje hodnotu číslo a exponentem, který obsahuje pořadí podle velikosti čísla.  
  
 Následující tabulka ukazuje počet bitů přidělených mantisa a exponent pro jednotlivé typy s plovoucí desetinnou čárkou. Nejvyšší bit žádné float nebo double je vždy bit přihlášení. Pokud je 1, číslo je považován za záporné; jinak je považována za kladné číslo.  
  
### <a name="lengths-of-exponents-and-mantissas"></a>Délek exponenty a mantisy  
  
|Typ|Délka exponentu|Mantisa délka|  
|----------|---------------------|---------------------|  
|float|8 bitů|23 bits|  
|double|11 bits|52 bitů|  
  
 Exponenty jsou uloženy ve formuláři bez znaménka, je exponent předpětím podle poloviční možná hodnota. Pro typ float je posun 127; double – typ je 1023. Skutečná hodnota exponentu můžete vypočítat odečtením hodnotu posunu z exponentu hodnoty.  
  
 Mantisa se ukládají jako binární zlomek větší než nebo rovno 1 a menší než 2. Pro typy float a double je předpokládané úvodní 1 mantisa v pozici většinu významný bit, tak mantisy jsou ve skutečnosti bity 24 a 53 dlouho, v uvedeném pořadí, i když většina významné bit se nikdy uložené v paměti.  
  
 Místo metody úložiště právě popsané můžete s plovoucí desetinnou čárkou balíček uložit binární čísla s plovoucí desetinnou čárkou nenormalizované čísla. "Nenormalizované čísla" jsou nenulové hodnoty s plovoucí desetinnou čárkou s vyhrazené exponentu hodnoty, ve kterých je důležité pro většinu bit mantisa je 0. Pomocí nenormalizované formátu lze rozšířit rozsah číslo s plovoucí desetinnou čárkou za cenu přesnost. Nemůžete ovládat, zda je v podobě normalizovaný nebo nenormalizované; reprezentována číslem s plovoucí desetinnou čárkou balíček s plovoucí desetinnou čárkou určuje reprezentace. Balíček s plovoucí desetinnou čárkou nikdy používá nenormalizované formuláře, pokud se změní na exponent menší než minimální, který může být určený ve formuláři normalizovaný.  
  
 V následující tabulce jsou uvedeny minimální a maximální hodnoty, že můžete ukládat do proměnné jednotlivých typů s plovoucí desetinnou čárkou. Hodnoty uvedené v této tabulce se vztahují pouze na normalizovaný čísla s plovoucí desetinnou čárkou Nenormalizované čísla s plovoucí desetinnou čárkou mít menší minimální hodnotu. Všimněte si, že čísla uchovávají v 80*x*87 registry jsou vždy reprezentované v podobě normalizovaný 80-bit; čísla můžete zastoupení jenom v nenormalizované formuláře při uložené v proměnné s plovoucí desetinnou čárkou 32bitovou nebo 64bitovou (proměnné float – typ a typ long).  
  
### <a name="range-of-floating-point-types"></a>Rozsah typů s plovoucí desetinnou čárkou  
  
|Typ|Minimální hodnota|Maximální hodnota|  
|----------|-------------------|-------------------|  
|float|1.175494351 E - 38|3.402823466 E + 38|  
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|  
  
 Pokud přesnost je méně důležité než úložiště, zvažte použití typ float pro proměnné s plovoucí desetinnou čárkou. Naopak pokud přesnost je nejdůležitější kritérium, použijte typ double.  
  
 Proměnné s plovoucí desetinnou čárkou mohou zvýšit na typ větší násobek (z typu float na typ double). Povýšení často dochází, když provádíte aritmetické na proměnné s plovoucí desetinnou čárkou. Tato aritmetické se vždycky provádí v jako vysoce stupeň přesnost jako proměnnou na nejvyšší úrovni přesnosti. Zvažte například následující typ deklarace:  
  
```  
float f_short;  
double f_long;  
long double f_longer;  
  
f_short = f_short * f_long;  
```  
  
 V předchozím příkladu, proměnná `f_short` je zvýšit na typ double a násobí hodnotou `f_long`; výsledek se zaokrouhlí na typ float před přiřazeny `f_short`.  
  
 V následujícím příkladu (která používá deklarace z předchozího příkladu), že aritmetické operace se provádí v přesnost float (32 bitů) na proměnné; výsledek se poté vyzval k double – typ:  
  
```  
f_longer = f_short * f_short;  
```  
  
## <a name="see-also"></a>Viz také  
 [Úložiště základních typů](../c-language/storage-of-basic-types.md)