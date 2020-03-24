---
title: LCID (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: bb9e44d34c675e4f5d955c5f422a6dd35259ec8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214796"
---
# <a name="lcid"></a>lcid

Umožňuje předat identifikátor národního prostředí do funkce.

## <a name="syntax"></a>Syntaxe

```cpp
[lcid]
```

## <a name="remarks"></a>Poznámky

Atribut **LCID** C++ implementuje funkci atributu [LCID](/windows/win32/Midl/lcid) MIDL. Pokud chcete implementovat národní prostředí pro blok knihovny, použijte parametr **LCID =** `lcid` pro atribut [Module](module-cpp.md) .

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Parametr rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)
