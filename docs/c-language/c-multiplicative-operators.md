---
title: Multiplikativní operátory jazyka C | Dokumentace Microsoftu
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
ms.openlocfilehash: 0be97e271ce8b500274d0e2ab1f271183ef7c238
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199991"
---
# <a name="c-multiplicative-operators"></a>Multiplikativní operátory jazyka C
Operátory násobení provedení násobení (<strong>\*</strong>), dělení (**/**) a zbytek (**%**) operace.  
  
## <a name="syntax"></a>Syntaxe

*multiplikativní výraz*:  
&nbsp;&nbsp;&nbsp;&nbsp;*výraz CAST*  
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz* <strong>\*</strong> *výrazem přetypování.*  
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz* **/** *výrazem přetypování.*  
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz* **%** *výrazem přetypování.*

Operandy operátoru zbytek (**%**) musí být integrálního typu. Násobení (<strong>\**</strong>) a dělení (**/**) operátory může trvat celé číslo nebo číslo s plovoucí čárkou typ – operandy; typy operandy se může lišit.  
  
Operátory násobení provádět běžné aritmetické převody operandů. Typ výsledku je typ operandu po převodu.  
  
> [!NOTE]
>  Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.  
  
 Multiplikativní operátory jazyka C jsou popsané níže:  
  
|Operátor|Popis|  
|--------------|-----------------|  
|<strong>\*</strong>|Operátor násobení způsobí, že se vynásobí dva operandy.|  
|**/**|Operátor dělení způsobí, že první operand k rozdělení po sekundách. Pokud jsou rozděleny dva celočíselné operandy a výsledek není typu integer, zkrátí se podle následujících pravidel:<br/><br/>-Není definováno podle standardu ANSI C výsledek dělení 0. Kompilátor Microsoft C generuje chybu v době kompilace nebo běhu.<br/><br/>-Pokud jsou oba operandy kladné nebo bez znaménka, výsledek je zkrácen na 0.<br/><br/>– Pokud některý operand je záporný, určuje, zda je největší celé číslo menší nebo rovna algebraických podíl výsledek operace, nebo je nejmenší celé číslo větší než nebo rovna hodnotě algebraických podíl je definován implementací. (Viz níže uvedené části specifické pro Microsoft.)|  
|**%**|Výsledek operátoru zbývající je zbytek po prvním operandem, je vyděleno hodnotou druhého. Při dělení je nepřesný, je výsledek určen následujícími pravidly:<br/><br/>– Pokud pravý operand je nula, výsledek není definován.<br/><br/>-Pokud jsou oba operandy kladné nebo bez znaménka, výsledek je kladný.<br/><br/>– Pokud některý operand je záporný a výsledkem je nepřesný, výsledek je definován implementací. (Viz níže uvedené části specifické pro Microsoft.)|  
  
 **Specifické pro Microsoft**  
  
 V oblasti, ve kterém některý operand je záporný je směr zkrácení směrem k 0.  
  
 Pokud je záporné dělení s operátor zbytku buď operace, výsledek má stejné znaménko jako podíl (První operand ve výrazu).  
  
 **Specifické pro END Microsoft**  
  
## <a name="examples"></a>Příklady  
 Následující příklady používají deklarací uvedené níže:  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 Tento příkaz používá operátor násobení:  
  
```  
y = x * i;  
```  
  
 V takovém případě `x` se násobí hodnotou `i` aby byla hodnota 20.0. Výsledek obsahuje **double** typu.  
  
```  
n = i / j;  
```  
  
 V tomto příkladu je 10 dělený 3. Výsledkem je zkrácen na 0, což má za následek celočíselnou hodnotu 3.  
  
```  
n = i % j;  
```  
  
 Tento příkaz přiřadí `n` zbývající celé číslo, 1, 10, je vyděleno hodnotou 3.  
  
 **Specifické pro Microsoft**  
  
 Znaménko zbytek je stejný jako znaménko podíl. Příklad:  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 V obou případech `50` a `2` mají stejné znaménko.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Multiplikativní operátory a operátor numerického zbytku](../cpp/multiplicative-operators-and-the-modulus-operator.md)