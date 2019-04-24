---
title: Operátory přetypování
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: e3d892a5aede4cd2d6a980b440875f0ac9837120
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312658"
---
# <a name="cast-operators"></a>Operátory přetypování

Přetypování poskytuje způsob explicitního převodu typu objektu v konkrétní situaci.

## <a name="syntax"></a>Syntaxe

*výraz CAST*: *unární výraz*

**(**  *název typu*  **)**  *výrazem přetypování.*

Kompilátor zpracovává *výrazem přetypování* jako typ *název typu* po přetypování. Přetypování lze použít k převodu objektů libovolného skalárního typu na jiný skalární typ a zpět. Explicitní přetypování jsou omezena stejnými pravidly, která určují účinky implicitních převodů, popsané v [převody přiřazení](../c-language/assignment-conversions.md). Při přetypování mohou být uplatněna další omezení vyplývající ze skutečných velikostí nebo reprezentací konkrétních typů. Zobrazit [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o skutečných velikostech celočíselných typů. Další informace o přetypováních naleznete v tématu [převody přetypování](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Viz také:

[Operátor přetypování: ()](../cpp/cast-operator-parens.md)
