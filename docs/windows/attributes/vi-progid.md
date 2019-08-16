---
title: vi_progid (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514870"
---
# <a name="vi_progid"></a>vi_progid

Určuje formu ProgID nezávislou na verzi.

## <a name="syntax"></a>Syntaxe

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parametry

*name*<br/>
Identifikátor ProgID nezávislý na verzi představující objekt.

Identifikátory ProgID prezentují uživatelsky čitelné verze identifikátoru třídy (CLSID) používané k identifikaci objektů COM/ActiveX.

## <a name="remarks"></a>Poznámky

Atribut **vi_progid** C++ umožňuje určit identifikátor ProgID nezávislý na verzi pro objekt modelu COM. Identifikátor ProgID má formu *název1. název2. Version*. Identifikátor ProgID nezávislý na verzi nemá *verzi*. Je možné zadat jak `progid` atributy, tak i **vi_progid** pro. `coclass` Pokud nezadáte **vi_progid**, je ProgID nezávislá na verzi hodnotou určenou atributem [ProgID](progid.md) .

**vi_progid** implikuje `coclass` atribut, to znamená, že pokud zadáte **vi_progid**, je totéž jako zadání `coclass` atributů **vi_progid** a.

Atribut **vi_progid** způsobí, že se třída automaticky zaregistruje pod zadaným názvem. Ve vygenerovaném souboru. idl se nezobrazí hodnota ProgID.

V projektech ATL, pokud je současně atribut [Coclass](coclass.md) , je zadaný identifikátor ProgID použit `GetVersionIndependentProgID` funkcí `coclass` (vloženou atributem).

## <a name="example"></a>Příklad

Ukázku použití **vi_progid**naleznete v příkladu [Coclass](coclass.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Klíč ProgID](/windows/win32/com/-progid--key)
