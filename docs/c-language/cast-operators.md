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

*cast-expression*: *unární výraz*

**(**  *název typu*  **)**  *přetypování – výraz*

Kompilátor zpracovává *přetypování – výraz* jako typ Type *-Name* po přetypování typu. Přetypování lze použít k převodu objektů libovolného skalárního typu na jiný skalární typ a zpět. Explicitní přetypování jsou omezená stejnými pravidly, která určují účinky implicitních převodů popsaných v tématu [převody přiřazení](../c-language/assignment-conversions.md). Při přetypování mohou být uplatněna další omezení vyplývající ze skutečných velikostí nebo reprezentací konkrétních typů. Informace o skutečných velikostech integrálních typů naleznete v tématu [úložiště základních typů](../c-language/storage-of-basic-types.md) . Další informace o přetypování naleznete v tématu [převody typu přetypování](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Viz také

[Operátor přetypování: ()](../cpp/cast-operator-parens.md)
