---
title: in (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: f25f15148621d7092858577825dbdd6caa1ae0be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166793"
---
# <a name="in-c"></a>in (C++)

Označuje, že parametr má být předán z volající procedury do volané procedury.

## <a name="syntax"></a>Syntaxe

```cpp
[in]
```

## <a name="remarks"></a>Poznámky

Atribut **in** C++ má stejné funkce jako [v](/windows/win32/Midl/in) atributu MIDL.

## <a name="example"></a>Příklad

Příklad použití v nástroji naleznete **v**tématu [BIND](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|**retval**|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)
