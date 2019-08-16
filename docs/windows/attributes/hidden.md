---
title: Hidden (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501450"
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
|**Požadované atributy**|**Coclass – třída** (při použití u **třídy** nebo **struktury**)|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)