---
title: registration_script (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 780f3d41676d01458f47542d6f0862a278edff6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214575"
---
# <a name="registration_script"></a>registration_script

Provede zadaný vlastní registrační skript.

## <a name="syntax"></a>Syntaxe

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Parametry

*pravidel*<br/>
Úplná cesta k souboru vlastního registračního skriptu (. rgs) Hodnota **none**, například `script = "none"`, označuje, že kotřída nemá žádné požadavky na registraci.

## <a name="remarks"></a>Poznámky

Atribut **registration_script** C++ spustí vlastní registrační skript určený *skriptem*. Pokud tento atribut není zadán, je použit standardní soubor. rgs (obsahující informace pro registraci komponenty). Další informace o souborech. rgs naleznete v tématu [Komponenta registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

Tento atribut vyžaduje, aby atribut [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) (nebo jiný atribut, který implikuje jednu z nich) byl také použit pro stejný prvek.

## <a name="example"></a>Příklad

Následující kód určuje, že komponenta má skript registru s názvem cpp_attr_ref_registration_script. rgs.

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Jednu nebo více následujících možností: `coclass`, `progid`nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[rdx](rdx.md)
