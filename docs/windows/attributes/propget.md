---
title: propget (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 495c6e974bbe226a77d5685c7d1d8adb29e30830
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645997"
---
# <a name="propget"></a>propget

Určuje funkci, která přistupujícího objektu vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
[propget]
```

## <a name="remarks"></a>Poznámky

**Propget** C++ atribut má stejné funkce jako [propget](/windows/desktop/Midl/propget) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](bindable.md) ukázkový používání **propget**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`propput`, `propputref`|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)