---
title: Položka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9bc6a88ee7dca0bcd4ad2f87fd3aa4c318d8b9d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604762"
---
# <a name="entry"></a>entry

Určuje exportované funkce nebo konstanta v modulu určením vstupní bod v knihovně DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(
   id
) ]
```

### <a name="parameters"></a>Parametry

*id*  
ID vstupní bod.

## <a name="remarks"></a>Poznámky

**Položka** C++ atribut má stejné funkce jako [položka](http://msdn.microsoft.com/library/windows/desktop/aa366815) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [možnost idl_module](../windows/idl-module.md) pro příklad použití **položka**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|`idl_module` Atribut|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  