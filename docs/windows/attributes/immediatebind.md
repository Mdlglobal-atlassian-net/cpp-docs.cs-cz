---
title: immediatebind (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: d0fb85a3f5642bc5fffcad29892ca15bb13a1ce0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166911"
---
# <a name="immediatebind"></a>immediatebind

Označuje, že se bude databáze okamžitě informovat o všech změnách vlastnosti objektu vázaného na data.

## <a name="syntax"></a>Syntaxe

```cpp
[immediatebind]
```

## <a name="remarks"></a>Poznámky

Atribut **immediatebind** C++ má stejné funkce jako atribut [immediatebind](/windows/win32/Midl/immediatebind) MIDL.

## <a name="example"></a>Příklad

Příklad použití **immediatebind**najdete v tématu s možností [vazby](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)
