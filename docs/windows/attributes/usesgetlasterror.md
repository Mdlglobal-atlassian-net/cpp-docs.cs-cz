---
title: usesgetlasterror (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: f58929db01a1710e811a973c0559ad29b242b4eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166130"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Říká volajícímu, že pokud při volání této funkce dojde k chybě, volající pak může zavolat `GetLastError`, aby získal kód chyby.

## <a name="syntax"></a>Syntaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Poznámky

Atribut **usesgetlasterror** C++ má stejné funkce jako atribut [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) MIDL.

## <a name="example"></a>Příklad

Ukázku použití **usesgetlasterror**najdete v příkladu [idl_module](idl-module.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|atribut **Module**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)
