---
title: dispinterface (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b02244e0576f99cc0a6940f2ee4a13511cfbe6f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789317"
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
[Vlastní](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)  