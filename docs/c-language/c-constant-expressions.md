---
title: Výrazy konstant C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaeb7ab79777d247f0bc0b2e6d749d8df5a7f8e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-constant-expressions"></a>Výrazy konstant v jazyce C
Konstantní výraz vyhodnotí při kompilaci, není běh a je možné v jakémkoli místě lze konstanta. Konstanta, která je v rozsahu hodnot reprezentovat pro tento typ se musí vyhodnotit konstantní výraz. Operandy konstantní výraz může být konstanty typu integer, konstanty znaků, konstanty s plovoucí desetinnou čárkou, konstanty výčtu typu přetypování, `sizeof` výrazy a jiné konstantní výrazy.  
  
## <a name="syntax"></a>Syntaxe  
 *konstantní výraz*:  
 *podmíněného výrazu*  
  
 *podmíněného výrazu*:  
 *logický výraz OR*  
  
 *logický výraz OR* **?**  *výraz* **:***podmíněného výrazu*   
  
 *výraz*:  
 *assignment-expression*  
  
 *výraz* **,***přiřazení – výraz*   
  
 *výraz přiřazení*:  
 *podmíněného výrazu*  
  
 *operátor přiřazení unární výraz přiřazení – výraz*  
  
 *operátor přiřazení*: jeden z  
 **= \*= /= %= += -= <\<= >>= &= ^= &#124;=**  
  
 Obsahovat terminálově nezávislých deklarátor struktura, enumerátor, přímé deklarátor, přímo abstraktní deklarátor a příkaz s popiskem *konstantní výraz* nonterminal.  
  
 Celočíselné konstantní výraz musí použít k určení velikosti členem pole bit do struktury, hodnota konstanty výčtu, velikost pole nebo hodnoty **případ** konstantní.  
  
 Konstantní výrazy použité v preprocesor – direktivy podléhají další omezení. V důsledku toho se označují jako "s omezeným přístupem konstantní výrazy." S omezeným přístupem konstantní výraz nemůže obsahovat `sizeof` výrazy, konstanty výčtu, zadejte do jakéhokoli typu nebo konstanty s plovoucí čárkou typu přetypování. Může, ale obsahovat speciální konstantní výraz `defined (` *identifikátor*`)`.  
  
## <a name="see-also"></a>Viz také  
 [Operandy a výrazy](../c-language/operands-and-expressions.md)