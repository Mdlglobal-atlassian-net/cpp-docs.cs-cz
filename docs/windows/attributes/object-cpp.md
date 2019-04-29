---
title: objekt (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0f544e84e5110761dfd01e25abef4352f055ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407533"
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
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)