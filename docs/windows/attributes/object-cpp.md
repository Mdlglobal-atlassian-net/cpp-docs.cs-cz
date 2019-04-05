---
title: objekt (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0f544e84e5110761dfd01e25abef4352f055ff5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022356"
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
|**Platí pro**|**rozhraní**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[vlastní](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)