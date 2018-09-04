---
title: s možností vazby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.bindable
dev_langs:
- C++
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ace2b62197b652baeb7e287a582b521252270f6d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691233"
---
# <a name="bindable"></a>bindable

Označuje, že vlastnost podporuje datové vazby.

## <a name="syntax"></a>Syntaxe

```cpp
[bindable]
```

## <a name="remarks"></a>Poznámky

**Umožňujících vazbu** C++ atribut má stejné funkce jako [umožňujících vazbu](/windows/desktop/Midl/bindable) atribut MIDL. Lze ji použít v vlastnosti definované [propget](../windows/propget.md), [propput](../windows/propput.md), nebo [propputref](../windows/propputref.md) atributy, nebo můžete ručně definovat metodu s možností vazby.

Následující ukázky knihovny MFC ukazují použití **umožňujících vazbu**:

- [Ukázky ovládacích prvků: Ovládací prvky ActiveX založené na knihovně MFC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [KR ukázka: Ovládací prvek ActiveX](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [Ukázka TESTHELP: Ovládací prvek ActiveX s popisy tlačítek a Nápověda](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

## <a name="example"></a>Příklad

Následující kód ukazuje, jak můžete **umožňujících vazbu** u vlastnosti:

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),
   dispinterface,
   helpstring("property demo Interface")  
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  
[defaultbind](../windows/defaultbind.md)  
[displaybind](../windows/displaybind.md)  
[immediatebind](../windows/immediatebind.md)  
[requestedit](../windows/requestedit.md)  