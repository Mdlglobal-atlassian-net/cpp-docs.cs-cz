---
title: "Výrazy konstant C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 596f558ea5c22f1850800d95b0d4ad0b5edd6a8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 *přiřazení – výraz*  
  
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