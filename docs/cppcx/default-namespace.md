---
title: default – obor názvů
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: b67aedc791ed41e93268d9e9f44492781940d55e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740519"
---
# <a name="default-namespace"></a>default – obor názvů

Obor názvů je integrovaných typů, které jsou podporovány nástrojem C++ `default`

## <a name="syntax"></a>Syntaxe

```
namespace default;
```

### <a name="members"></a>Členové

Všechny předdefinované typy dědí následující členy.

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Vrátí kód hash této instance.|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Vrátí řetězec, který představuje aktuální typ.|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Vrátí řetězec, který představuje aktuální typ.|

### <a name="built-in-types"></a>Předdefinované typy

|Name|Popis|
|----------|-----------------|
|`char16`|16bitová nečíselná hodnota, která představuje bod kódu Unicode (UTF-16).|
|`float32`|32 číslo s plovoucí desetinnou čárkou standardu IEEE 754.|
|`float64`|64 číslo s plovoucí desetinnou čárkou standardu IEEE 754.|
|`int16`|16bitové celé číslo se znaménkem.|
|`int32`|32 celé číslo se znaménkem.|
|`int64`|64 celé číslo se znaménkem.|
|`int8`|16bitová číselná hodnota se znaménkem.|
|`uint16`|16bitová unsigned integer.|
|`uint32`|32 bitová unsigned integer.|
|`uint64`|64 bitová unsigned integer.|
|`uint8`|16bitová číselná hodnota bez znaménka.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** vccorlib. h

## <a name="see-also"></a>Viz také:

[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
