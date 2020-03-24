---
title: Hidden (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 6b420e8f50bd217de460a81f5faaf9583c701376
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168093"
---
# <a name="hidden"></a>hidden

Označuje, že položka existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele.

## <a name="syntax"></a>Syntaxe

```cpp
[hidden]
```

## <a name="remarks"></a>Poznámky

**Skrytý** C++ atribut má stejné funkce jako [skrytý](/windows/win32/Midl/hidden) atribut MIDL.

## <a name="example"></a>Příklad

Příklad, jak používat **skryté**, najdete v příkladu s možností [vytvoření vazby](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**rozhraní**, **Třída**, **Struktura**, metoda, vlastnost|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**Coclass – třída** (při použití pro **třídu** nebo **strukturu**)|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)
