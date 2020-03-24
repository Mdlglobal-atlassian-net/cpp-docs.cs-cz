---
title: out (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 6ab8fdf691e2220087f5c5d64bb70c5deb27675c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214656"
---
# <a name="out-c"></a>out (C++)

Identifikuje parametry ukazatele, které se vracejí z volané procedury do volající procedury (ze serveru do klienta).

## <a name="syntax"></a>Syntaxe

```cpp
[out]
```

## <a name="remarks"></a>Poznámky

Atribut **out** C++ má stejné funkce jako atribut [out](/windows/win32/Midl/out-idl) MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [vázání](bindable.md) pro použití ukázkového použití **.**

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Parametr rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)
