---
title: retval | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ff83b156054774a06a371e7832dc73dc95a579c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221255"
---
# <a name="retval"></a>retval

Označí parametr, který přijímá návratovou hodnotu člena.

## <a name="syntax"></a>Syntaxe

```cpp
[retval]
```

## <a name="remarks"></a>Poznámky

**Retval** C++ atribut má stejné funkce jako [retval](/windows/desktop/Midl/retval) atribut MIDL.

**retval** musí být uvedena v posledním argumentu v deklaraci funkce.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **retval**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Rozhraní parametrů, metody rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**out**|
|**Neplatné atributy**|**in**|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy parametru](../windows/parameter-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  