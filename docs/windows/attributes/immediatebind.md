---
title: immediatebind (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 1844e72ecd1fe7c0f4255426eb48f5c70471e5f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409470"
---
# <a name="immediatebind"></a>immediatebind

Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.

## <a name="syntax"></a>Syntaxe

```cpp
[immediatebind]
```

## <a name="remarks"></a>Poznámky

**Immediatebind** C++ atribut má stejné funkce jako [immediatebind](/windows/desktop/Midl/immediatebind) atribut MIDL.

## <a name="example"></a>Příklad

Zobrazit [umožňujících vazbu](bindable.md) příklad, jak používat **immediatebind**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)