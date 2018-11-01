---
title: LCID (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: e431736fcd38b3c08936e65ecf05594142ced4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655314"
---
# <a name="lcid"></a>lcid

Umožňuje předat funkci identifikátor národního prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
[lcid]
```

## <a name="remarks"></a>Poznámky

**Lcid** C++ atribut implementuje funkce [lcid](/windows/desktop/Midl/lcid) atribut MIDL. Pokud chcete implementovat národní prostředí pro bloku knihovny, použijte **lcid =** `lcid` parametr [modulu](module-cpp.md) atribut.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Parametr rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)