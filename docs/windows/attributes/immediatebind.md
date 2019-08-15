---
title: immediatebind (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 8c659f23d6828616c4a48522b61330336e994cbb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514649"
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

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)