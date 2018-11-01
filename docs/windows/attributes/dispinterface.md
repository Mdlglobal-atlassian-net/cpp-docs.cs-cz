---
title: dispinterface (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: d0ace76fdbbc1ff930bccb4e6fc203895b4f1637
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677276"
---
# <a name="dispinterface"></a>dispinterface

Umístí rozhraní v souboru IDL jako rozhraní odbavení.

## <a name="syntax"></a>Syntaxe

```cpp
[dispinterface]
```

## <a name="remarks"></a>Poznámky

Když **dispinterface** C++ atribut předchází rozhraní, způsobí, že rozhraní být umístěny uvnitř bloku knihovny v souboru generovaného IDL.

Pokud zadáte základní třídy, rozhraní odbavení odvodí z `IDispatch`. Je nutné zadat [id](id.md) pro členy rozhraní odbavení.

Příklad použití pro [dispinterface](/windows/desktop/Midl/dispinterface) v dokumentaci k MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

není platný pro **dispinterface** atribut.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](bindable.md) příklad, jak používat **dispinterface**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**interface**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy podle použití](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)