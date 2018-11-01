---
title: objekt (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 1cae9e6b014f33dfbbcccdeb4172d6f35349e307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526157"
---
# <a name="object-c"></a>object (C++)

Určuje vlastní rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[object]
```

## <a name="remarks"></a>Poznámky

Pokud předchozí definice rozhraní, **objekt** C++ atribut způsobí, že rozhraní budou umístěny v souboru IDL jako vlastní rozhraní.

Libovolné rozhraní označené objektu musí dědit z `IUnknown`. Tato podmínka splněna Pokud některý z základních rozhraní dědí od `IUnknown`. Pokud žádná základní rozhraní dědí od `IUnknown`, kompilátor způsobí, že rozhraní označené **objekt** odvodit z `IUnknown`.

## <a name="example"></a>Příklad

Zobrazit [nonbrowsable](nonbrowsable.md) příklad, jak používat **objekt**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**interface**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)