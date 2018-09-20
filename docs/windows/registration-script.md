---
title: registration_script – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.registration_script
dev_langs:
- C++
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4aaef2cca5146291f7d3708a995a116768e0467
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382931"
---
# <a name="registrationscript"></a>registration_script

Provede zadanou registraci vlastní skript.

## <a name="syntax"></a>Syntaxe

```cpp
[ registration_script(
   script
) ]
```

### <a name="parameters"></a>Parametry

*skript*<br/>
Úplná cesta k souboru registrace vlastní skript (.rgs). Hodnota **žádný**, jako například `script = "none"`, označuje, že coclass nemá žádné požadavky na registraci.

## <a name="remarks"></a>Poznámky

**Registration_script –** C++ atribut spustí skript vlastní registrace určené *skript*. Pokud tento atribut není zadán, je použít standardní .rgs soubor (obsahující informace o registraci komponenty). Další informace o .rgs soubory, naleznete v tématu [The komponenta knihovny ATL registru (Registrar)](../atl/atl-registry-component-registrar.md).

Tento atribut vyžaduje, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít u stejného elementu.

## <a name="example"></a>Příklad

Následující kód určuje, že součást má volat cpp_attr_ref_registration_script.rgs skript registru.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Jeden nebo více z následujících akcí: `coclass`, `progid`, nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[COM – atributy](../windows/com-attributes.md)<br/>
[Atributy třídy](../windows/class-attributes.md)<br/>
[rdx](../windows/rdx.md)  