---
title: oleautomation (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 4a50121e1a2e170ba69ee21526f4600512097c74
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471666"
---
# <a name="oleautomation"></a>oleautomation

Označuje, že je kompatibilní s automatizací rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[oleautomation]
```

## <a name="remarks"></a>Poznámky

**Oleautomation** C++ atribut má stejné funkce jako [oleautomation](/windows/desktop/Midl/oleautomation) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklady pro [defaultvalue](defaultvalue.md) a [nerozšiřitelnou kategorii](nonextensible.md) ukázkový používání **oleautomation**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**interface**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|**dispinterface**|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)