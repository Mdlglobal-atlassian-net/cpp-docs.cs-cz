---
title: Operátory přetypování
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: dd84ae2e9868e53fedf9e7977fe4c253ad2db72f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443950"
---
# <a name="cast-operators"></a>Operátory přetypování

Přetypování poskytuje způsob explicitního převodu typu objektu v konkrétní situaci.

## <a name="syntax"></a>Syntaxe

*výraz CAST*: *unární výraz*

**(**  *název typu*  **)**  *výrazem přetypování.*

Kompilátor zpracovává *výrazem přetypování* jako typ *název typu* po přetypování. Přetypování lze použít k převodu objektů libovolného skalárního typu na jiný skalární typ a zpět. Explicitní přetypování jsou omezena stejnými pravidly, která určují účinky implicitních převodů, popsané v [převody přiřazení](../c-language/assignment-conversions.md). Při přetypování mohou být uplatněna další omezení vyplývající ze skutečných velikostí nebo reprezentací konkrétních typů. Zobrazit [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o skutečných velikostech celočíselných typů. Další informace o přetypováních naleznete v tématu [převody přetypování](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Viz také

[Operátor přetypování: ()](../cpp/cast-operator-parens.md)