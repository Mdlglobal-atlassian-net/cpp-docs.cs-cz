---
title: _variant_t – třída
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: 69976cab9caed653a8278f80821569b613f690eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165943"
---
# <a name="variantt-class"></a>_variant_t – třída

**Microsoft Specific**

A **_variant_t** zapouzdřuje objektu `VARIANT` datového typu. Třída spravuje a zrušení přidělení prostředků a volá funkci `VariantInit` a `VariantClear` podle potřeby.

### <a name="construction"></a>Konstrukce

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Vytvoří **_variant_t** objektu.|

### <a name="operations"></a>Operace

|||
|-|-|
|[Attach](../cpp/variant-t-attach.md)|Připojí `VARIANT` objektu do **_variant_t** objektu.|
|[Vymazat](../cpp/variant-t-clear.md)|Vymaže zapouzdřeného `VARIANT` objektu.|
|[ChangeType](../cpp/variant-t-changetype.md)|Typ se změní **_variant_t** objekt označený `VARTYPE`.|
|[Detach](../cpp/variant-t-detach.md)|Odpojí zapouzdřeného `VARIANT` objektu z tohoto **_variant_t** objektu.|
|[SetString –](../cpp/variant-t-setstring.md)|Přiřadí řetězec tomuto **_variant_t** objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Operator =](../cpp/variant-t-operator-equal.md)|Přiřadí novou hodnotu do existujícího **_variant_t** objektu.|
|[operátor ==,! =](../cpp/variant-t-relational-operators.md)|Porovnat dva **_variant_t** objekty a zjistí rovnost či nerovnost.|
|[– Extraktory](../cpp/variant-t-extractors.md)|Extrahovat data z zapouzdřeného `VARIANT` objektu.|

**Specifické pro END Microsoft**

## <a name="requirements"></a>Požadavky

**Header:** \<comutil.h>

**Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)