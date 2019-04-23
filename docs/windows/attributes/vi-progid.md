---
title: vi_progid – (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: 7050543c9acf3801a99d3e32e119325900bdb050
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033586"
---
# <a name="viprogid"></a>vi_progid

Určuje verzi nezávislé formu ProgID.

## <a name="syntax"></a>Syntaxe

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Nezávislé na verze ProgID reprezentující objekt.

ProgID prezentovat čitelná verze identifikátor třídy (CLSID) slouží k identifikaci objektů modelu COM a ActiveX.

## <a name="remarks"></a>Poznámky

**Vi_progid –** C++ atribut umožňuje zadat pro objekt modelu COM ProgID nezávislé na verzi. Identifikátor ProgID má tvar *name1.name2.version*. Nezávislé na verze ProgID nemá *verze*. Je možné zadat současně `progid` a **vi_progid –** atributy na `coclass`. Pokud nezadáte **vi_progid –**, nezávislé na verze ProgID se hodnoty určené [progid](progid.md) atribut.

**vi_progid –** znamená `coclass` atribut, to znamená, pokud zadáte **vi_progid –**, je totéž jako zadání `coclass` a **vi_progid –** atributy.

**Vi_progid –** atribut způsobí, že třída má být automaticky zaregistrován se zadaným názvem. Generovaného souboru nezobrazí hodnotu ProgID.

V projektech ATL Pokud [coclass](coclass.md) atribut je také k dispozici, používá zadaný identifikátor ProgID `GetVersionIndependentProgID` – funkce (vkládat stisknutím `coclass` atribut).

## <a name="example"></a>Příklad

Zobrazit [coclass](coclass.md) příklad ukázkový používání **vi_progid –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Klíč progID](/windows/desktop/com/-progid--key)
