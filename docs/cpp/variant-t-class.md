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
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187749"
---
# <a name="_variant_t-class"></a>_variant_t – třída

**Specifické pro společnost Microsoft**

Objekt **_variant_t** zapouzdřuje datový typ `VARIANT`. Třída spravuje přidělování a navracení prostředků a poskytuje volání funkcí `VariantInit` a `VariantClear` podle potřeby.

### <a name="construction"></a>Stavbě

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Vytvoří objekt **_variant_t** .|

### <a name="operations"></a>Operace

|||
|-|-|
|[Attach](../cpp/variant-t-attach.md)|Připojí objekt `VARIANT` k objektu **_variant_t** .|
|[Jejich](../cpp/variant-t-clear.md)|Vymaže zapouzdřený `VARIANT` objekt.|
|[ChangeType](../cpp/variant-t-changetype.md)|Změní typ objektu **_variant_t** na uvedený `VARTYPE`.|
|[Detach](../cpp/variant-t-detach.md)|Odpojí zapouzdřený `VARIANT` objekt od tohoto objektu **_variant_t** .|
|[SetString](../cpp/variant-t-setstring.md)|Přiřadí k tomuto objektu **_variant_t** řetězec.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Operátor =](../cpp/variant-t-operator-equal.md)|Přiřadí novou hodnotu existujícímu objektu **_variant_t** .|
|[operator = =,! =](../cpp/variant-t-relational-operators.md)|Porovná dva objekty **_variant_t** k rovnosti nebo nerovnosti.|
|[Extraktory](../cpp/variant-t-extractors.md)|Extrahuje data ze zapouzdřeného objektu `VARIANT`.|

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<comutil. h >

**Lib:** comsuppw. lib nebo comsuppwd. lib (viz [/Zc: Wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , kde najdete další informace.)

## <a name="see-also"></a>Viz také

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)
