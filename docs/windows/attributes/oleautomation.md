---
title: oleautomation (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.oleautomation
dev_langs:
- C++
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ccc83dd6f51c3b7072b17d141f29e93c63688fa1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059529"
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