---
title: propput | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f6adf0f2eaf61c3a280c8ca248cffea2f05bda6f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213166"
---
# <a name="propput"></a>propput

Určuje funkci, která nastavení vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
[propput]
```

## <a name="remarks"></a>Poznámky

**Propput** C++ atribut má stejné funkce jako [propput](/windows/desktop/Midl/propput) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **propput**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`propget`, `propputref`|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  
[propget](../windows/propget.md)  
[propputref](../windows/propputref.md)