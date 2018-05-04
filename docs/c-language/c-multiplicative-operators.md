---
title: Multiplikativní operátory jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1810cc9dd7a991e302e0e9e2db69f65aebebc613
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-multiplicative-operators"></a>Multiplikativní operátory jazyka C
Multiplikativní operátory provést násobení (**\****), dělení (**/**) a zbytek (`%`) operace.  
  
 **Syntaxe**  
  
 *multiplikativní výraz*:  
 *cast-expression*  
  
 *multiplikativní výraz***\****výraz cast*  
  
 *multiplikativní výraz***/***výraz cast*  
  
 *multiplikativní výraz***%***výraz cast*  
  
 Operandy operátoru zbývající (`%`) musí být celočíselné. Násobení (**\****) a dělení (**/**) operátory může trvat celé číslo nebo číslo s plovoucí čárkou typ – operandy; typy operandy se může lišit.  
  
 Multiplikativní operátory provést obvyklé aritmetické převody operandy. Typ výsledku je typ operandy po převodu.  
  
> [!NOTE]
>  Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.  
  
 Multiplikativní operátory jazyka C jsou následující:  
  
|Operátor|Popis|  
|--------------|-----------------|  
|**\***|Operátor násobení způsobí, že jeho dva operandy vynásobí.|  
|**/**|Operátor dělení způsobí, že první operand rozdělit druhou. Pokud se dál dělí dva operandy celé číslo a výsledek není typu integer, zkrátí se podle následujících pravidel:|  
||-Není definován podle standardu ANSI C výsledek dělení 0. Kompilátor Microsoft C generuje chybu v době kompilace nebo dobu spuštění.|  
||– Pokud jsou oba operandy kladná nebo bez znaménka, výsledek se zkrátí na 0.|  
||– Pokud buď operand je hodnota záporná, jestli je největší celé číslo menší než nebo rovna algebraických podílu výsledek operace, nebo je nejmenší celé číslo větší než nebo rovna hodnotě algebraických podílu je implementace definované. (Viz část Microsoft specifické níže.)|  
|`%`|Výsledek operátor zbytku je zbývající při dělení první operand druhý. Když divizi je nepřesný, výsledek je dáno následující pravidla:|  
||– Pokud pravý operand nulová, výsledkem nedefinovaný.|  
||– Pokud jsou oba operandy kladná nebo bez znaménka, výsledkem je kladná.|  
||– Pokud je záporná. buď operand a výsledkem je nepřesný, výsledkem je implementace definované. (Viz část Microsoft specifické níže.)|  
  
 **Konkrétní Microsoft**  
  
 V oblasti, kde je buď operand záporná je směr zkrácení směrem k 0.  
  
 Pokud je buď operace záporné v divizi s operátor zbytku, výsledek obsahuje stejné znaménko jako dělenec (První operand výrazu).  
  
 **Konkrétní Microsoft END**  
  
## <a name="examples"></a>Příklady  
 Deklarací uvedené níže, se používají pro následující příklady:  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 Tento příkaz používá operátor násobení:  
  
```  
y = x * i;  
```  
  
 V takovém případě `x` se násobí hodnotou `i` poskytnout hodnota 20.0. Výsledek obsahuje **dvojité** typu.  
  
```  
n = i / j;  
```  
  
 V tomto příkladu je rozdělena 10 3. Výsledek se zkrátí na 0, je hodnota celého čísla 3.  
  
```  
n = i % j;  
```  
  
 Tento příkaz přiřadí `n` zbývající celé číslo, 1, při dělení 10 3.  
  
 **Konkrétní Microsoft**  
  
 Znaménko zbývající je stejný jako znaménko dělenec. Příklad:  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 V každém případě `50` a `2` mít stejné znaménko.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Multiplikativní operátory a operátor numerického zbytku](../cpp/multiplicative-operators-and-the-modulus-operator.md)