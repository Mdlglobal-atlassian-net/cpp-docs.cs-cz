---
title: RDX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00ef28954a686dac72c8b7f55b86c88313e74643
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719717"
---
# <a name="rdx"></a>rdx

Vytvoří klíč registru nebo upraví stávající klíč registru.

## <a name="syntax"></a>Syntaxe

```cpp
[ rdx(
   key,
   valuename=NULL,
   regtype
) ]
```

### <a name="parameters"></a>Parametry

*Klíč*  
Název klíče, který má být vytvořen nebo otevřen.

*Název hodnoty*  
(Volitelné) Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, je přidána.

*regtype*  
Typ přidávaný klíč registru. Může být jedna z následujících akcí: `text`, `dword`, `binary`, nebo `CString`.

## <a name="remarks"></a>Poznámky

**Rdx** C++ atribut vytvoří nebo upraví stávající klíč registru pro komponenty modelu COM. Atribut přidá makro BEGIN_RDX_MAP na objekt, který implementuje cílový člen. `RegistryDataExchange`, funkce vloženy jako výsledek BEGIN_RDX_MAP makra lze použít k přenosu dat mezi registru a datové členy

Tento atribut lze použít ve spojení s [coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atributy nebo jiné atributy, které zahrnuje jeden z nich.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída** nebo **struktura** člena|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="example"></a>Příklad

Následující kód přidá klíč registru s názvem MyValue popisující komponenty modelu COM CMyClass systému.

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>Viz také

[COM – atributy](../windows/com-attributes.md)  
[registration_script](../windows/registration-script.md)  