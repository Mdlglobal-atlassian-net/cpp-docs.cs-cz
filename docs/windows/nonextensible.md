---
title: nonextensible – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f24aa8b1aa6b4e2e996ec22062263f785d730d0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222577"
---
# <a name="nonextensible"></a>nonextensible

Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Poznámky

**Nerozšiřitelnou kategorii** C++ atribut má stejné funkce jako [nerozšiřitelnou kategorii](/windows/desktop/Midl/nonextensible) atribut MIDL.

Použití **nerozšiřitelnou kategorii** také vyžaduje [oleautomation](../windows/oleautomation.md) atribut.

## <a name="example"></a>Příklad

Následující kód ukazuje jedno použití **nerozšiřitelnou kategorii** atribut:

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**interface**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|`dual` a `oleautomation`, nebo `dispinterface`|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy rozhraní](../windows/interface-attributes.md)  