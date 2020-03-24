---
title: Object (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 4545d899c13a1eabf8ea5fb6fe3918fb5f05b626
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214657"
---
# <a name="object-c"></a>object (C++)

Identifikuje vlastní rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[object]
```

## <a name="remarks"></a>Poznámky

Při předchozí definici rozhraní atribut **Object** C++ způsobí, že rozhraní bude umístěno v souboru. idl jako vlastní rozhraní.

Jakékoli rozhraní označené objektem musí dědit od `IUnknown`. Tento stav je splněn, pokud některý ze základních rozhraní dědí od `IUnknown`. Pokud žádná ze základních rozhraní nedědí od `IUnknown`, kompilátor způsobí, že rozhraní označené **objektem** bude odvozeno od `IUnknown`.

## <a name="example"></a>Příklad

Příklad použití **objektu**naleznete v tématu [neprocházetelné](nonbrowsable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
