---
title: __based – gramatika
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: a8c923b5a111144c539b5bea1b2f47eb58dd1fbd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857642"
---
# <a name="__based-grammar"></a>__based – gramatika

**Specifické pro společnost Microsoft**

Založené na adresách je užitečné, pokud potřebujete přesnou kontrolu nad segmentem, ve kterém jsou objekty přiděleny (statická a dynamická data).

Jediná forma adresování, která je přijatelná v 32 a 64 bitových kompilacích, je založena na ukazateli, který definuje typ, který obsahuje 32-bitové 64 nebo 16bitové přemístění na 32 nebo na základě hodnoty **void**.

## <a name="grammar"></a>Gramatika

*založený na rozsahu – modifikátor*: **__based (**  *základní výraz*  **)**

*základní-výraz*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*based – proměnná*: *identifikátor*

*založené na abstract-deklarátor*: *abstract-deklarátor*

*základní typ*: *typ – název*

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Základní ukazatele](../cpp/based-pointers-cpp.md)