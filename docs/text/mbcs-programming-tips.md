---
title: MBCS – tipy pro programování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a88fffbfc42dd6e7386ec43e55f2013f2548b6f5
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204467"
---
# <a name="mbcs-programming-tips"></a>MBCS – tipy pro programování

Při vývoji nových aplikací měli byste použít kódování znaků Unicode pro všechny řetězce, které mohou případně vidět koncoví uživatelé. Znaková sada MBCS je starou technologií, která byla nahrazena sadou Unicode. Tento oddíl poskytuje tipy pro vývojáře, kteří musí udržovat existující programy, které používají znakové sady MBCS a kde není praktické přejít ke kódování Unicode. Doporučení se týká aplikací knihovny MFC a aplikací, které jsou psány bez knihovny MFC. Mezi témata patří:

- [Obecné rady k programování se znakovou sadou MBCS](../text/general-mbcs-programming-advice.md)

- [Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)

- [Bajtové indexy](../text/byte-indices.md)

- [Poslední znak v řetězci](../text/last-character-in-a-string.md)

- [Přiřazení znaků](../text/character-assignment.md)

- [Porovnávání znaků](../text/character-comparison.md)

- [Přetečení vyrovnávací paměti](../text/buffer-overflow.md)

## <a name="see-also"></a>Viz také

[Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)