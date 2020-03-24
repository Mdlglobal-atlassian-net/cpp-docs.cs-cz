---
title: odesílající (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 66567b0a1b043136e0a754e3a52bbdd7c463e178
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168236"
---
# <a name="dispinterface"></a>dispinterface

Umístí rozhraní do souboru. idl jako odesílající rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[dispinterface]
```

## <a name="remarks"></a>Poznámky

Když atribut **odesílající** C++ rozhraní předchází rozhraní, způsobí, že rozhraní bude umístěno uvnitř bloku knihovny v generovaném souboru. idl.

Pokud nezadáte základní třídu, rozhraní Dispatch bude odvozeno z `IDispatch`. Je nutné zadat [ID](id.md) pro členy rozhraní dispatch.

Příklad použití pro rozhraní [IDispatch](/windows/win32/Midl/dispinterface) v dokumentaci MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

není platný pro atribut **odesílajícího** rozhraní.

## <a name="example"></a>Příklad

Příklad, jak používat **odesílající**rozhraní, najdete v příkladu pro [vázání](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|`dual`, `object`, `oleautomation`, `local``ms_union`|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy podle použití](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
