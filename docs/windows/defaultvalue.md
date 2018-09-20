---
title: Výchozí hodnota | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a27120869c464a9009f8d19cf0f84bfde7a02e96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446052"
---
# <a name="defaultvalue"></a>defaultvalue

Umožňuje specifikace výchozí hodnotu pro zadaný nepovinný parametr.

## <a name="syntax"></a>Syntaxe

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výchozí hodnota pro parametr.

## <a name="remarks"></a>Poznámky

**Defaultvalue** C++ atribut má stejné funkce jako [defaultvalue](/windows/desktop/Midl/defaultvalue) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje metodu rozhraní pomocí **defaultvalue** atribut:

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),
   dual, oleautomation,
   helpstring("IFireTabCtrl Interface"),
   helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Parametr rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy parametru](../windows/parameter-attributes.md)<br/>
[out](../windows/out-cpp.md)<br/>
[retval](../windows/retval.md)<br/>
[in](../windows/in-cpp.md)<br/>
[pointer_default](../windows/pointer-default.md)<br/>
[Jedinečný](../windows/unique-cpp.md)  