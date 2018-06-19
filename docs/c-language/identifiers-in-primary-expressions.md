---
title: Identifikátory v primárních výrazech | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9f39f7ce609ea06a2d991ac79c2b1151625bc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384756"
---
# <a name="identifiers-in-primary-expressions"></a>Identifikátory v primárních výrazech
Identifikátory může mít integrální, **float**, `enum`, `struct`, **– typ union**, pole, ukazatele, nebo typ funkce. Identifikátor je primární výraz za předpokladu, že byl deklarován jako označující objekt (v tomto případě je to l hodnota) nebo jako funkce (v tomto případě je to označení funkce). V tématu [L-Value a R-Value výrazy](../c-language/l-value-and-r-value-expressions.md) pro definici l-value.  
  
 Hodnota ukazatele, která je představována identifikátorem pole, není proměnná a pole identifikátoru tedy nemůže vytvořit levý operand operátoru přiřazení a nejedná se tedy o upravitelnou l-hodnotu.  
  
 Identifikátor deklarovaný jako funkce představuje ukazatel, jehož hodnotou je adresa funkce. Ukazatel adresuje funkci vracející hodnotu zadaného typu. V operacích přiřazení tedy nemohou být l-hodnotami ani identifikátory funkce. Další informace najdete v tématu [identifikátory](../c-language/c-identifiers.md).  
  
## <a name="see-also"></a>Viz také  
 [Primární výrazy jazyka C](../c-language/c-primary-expressions.md)