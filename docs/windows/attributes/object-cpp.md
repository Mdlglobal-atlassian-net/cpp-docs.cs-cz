---
title: objekt (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8828ada429875245d583c30d65259300a01f6a5d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067433"
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