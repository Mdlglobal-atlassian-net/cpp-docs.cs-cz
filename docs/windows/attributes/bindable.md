---
title: Atribut s možností vazby (C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 07f446b946d6703c4a8b9ae59ae0edd8172c6879
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148390"
---
# <a name="bindable"></a>bindable

Označuje, že vlastnost podporuje datové vazby.

## <a name="syntax"></a>Syntaxe

```cpp
[bindable]
```

## <a name="remarks"></a>Poznámky

**Umožňujících vazbu** C++ atribut má stejné funkce jako [umožňujících vazbu](/windows/desktop/Midl/bindable) atribut MIDL. Lze ji použít v vlastnosti definované [propget](propget.md), [propput](propput.md), nebo [propputref](propputref.md) atributy, nebo můžete ručně definovat metodu s možností vazby.

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
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"), dispinterface, helpstring("property demo Interface")
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
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)