---
title: vi_progid – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 468b5c5dcadc1715384684062f203ae9179ef044
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789533"
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

**Vi_progid –** atribut C++ umožňuje zadat pro objekt modelu COM ProgID nezávislé na verzi. Identifikátor ProgID má tvar *name1.name2.version*. Nezávislé na verze ProgID nemá *verze*. Je možné zadat současně `progid` a **vi_progid –** atributy na `coclass`. Pokud nezadáte **vi_progid –**, nezávislé na verze ProgID se hodnoty určené [progid](progid.md) atribut.

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

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Klíč progID](/windows/desktop/com/-progid--key)  