---
title: Koprocesor plovoucí desetinné čárky a konvence volání
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188614"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor plovoucí desetinné čárky a konvence volání

Pokud píšete rutiny sestavení pro koprocesor plovoucí desetinné čárky, je nutné zachovat řídicí slovo s plovoucí desetinnou čárkou a vyčistit zásobník koprocesorů, Pokud nevrátíte hodnotu **typu float** nebo **Double** (kterou by měla funkce vracet v St (0)).

## <a name="see-also"></a>Viz také

[Konvence volání](../cpp/calling-conventions.md)
