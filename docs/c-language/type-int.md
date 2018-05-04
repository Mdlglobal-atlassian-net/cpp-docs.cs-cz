---
title: Typ int | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ed3fcd9b11a76f8ff211bf8be5cf50ee6664cda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="type-int"></a>Typ int
Velikost položky typu `int` se znaménkem nebo bez něj je standardní velikostí celého čísla na daném počítači. Například v 16bitových operačních systémech má typ `int` obvykle 16 bitů, tedy 2 bajty. Ve 32bitových operačních systémech má typ `int` obvykle 32 bitů, tedy 4 bajty. Proto `int` typ je ekvivalentní buď `short int` nebo **dlouho int** typ a `unsigned int` typ je ekvivalentní buď **nepodepsané prostě** nebo `unsigned long` typ, v závislosti na cílovém prostředí. Všechny typy `int` představují hodnoty se znaménkem, není-li zadáno jinak.  
  
 Specifikátory typu `int` a `unsigned int` (nebo jednoduše `unsigned`) definují určité funkce jazyka C (například typ `enum`). V těchto případech určují skutečnou velikost úložiště definice typu `int` a unsigned int pro danou implementaci.  
  
 **Konkrétní Microsoft**  
  
 Celá čísla se znaménkem jsou reprezentována ve tvaru dvojkového doplňku. Nejvýznamnější bit uchovává znaménko: 1 pro záporné, 0 pro kladné a nulu. Rozsah hodnot je uveden v [omezení typu Integer C++](../c-language/cpp-integer-limits.md), které jsou převzaty z omezení. Soubor hlaviček H.  
  
 **Konkrétní Microsoft END**  
  
> [!NOTE]
>  Specifikátory typu int a unsigned int se v programech jazyka C hojně používají, protože umožňují konkrétnímu počítači zpracovat celočíselné hodnoty způsobem pro daný počítač nejefektivnějším. Jelikož se však velikosti typů int a unsigned int liší, programy, které závisí na konkrétní velikosti celého čísla, mohou být nepřenositelné na jiné počítače. Chcete-li programy víc přenosného, můžete použít výrazy s sizeof – operátor (jak je popsáno v [sizeof – operátor](../c-language/sizeof-operator-c.md)) místo pevně data velikosti.  
  
## <a name="see-also"></a>Viz také  
 [Úložiště základních typů](../c-language/storage-of-basic-types.md)