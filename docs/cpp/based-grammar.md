---
title: __based – gramatika
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 8dec9b0bcc7db25e2ec4c39b9d907922691bfc05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393945"
---
# <a name="based-grammar"></a>__based – gramatika

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Na základě adresování je užitečné, když je nutné mít naprostou kontrolu nad segment, ve kterém jsou objekty přidělovány (statické a dynamické na základě dat).

Jedinou formou adresování podle přijatelný v 32bitových a 64bitových kompilacích je "na základě ukazatel", který definuje typ, který obsahuje 32bitové nebo 64bitové posunutí se základní 32bitová nebo 64bitová verze nebo na základě **void**.

## <a name="grammar"></a>Gramatika

*na základě modifikátoru rozsahu*: **__based (***výraz base***)** 

*výraz Base*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*na základě proměnné*: *identifikátor*

*based-abstract-declarator*: *abstract-declarator*

*Základní typ*: *název typu*

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Základní ukazatele](../cpp/based-pointers-cpp.md)