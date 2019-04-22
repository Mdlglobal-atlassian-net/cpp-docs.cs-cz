---
title: RDX (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: 2790c3de01d21242daee73fc442ad22d88739355
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023877"
---
# <a name="rdx"></a>rdx

Vytvoří klíč registru nebo upraví stávající klíč registru.

## <a name="syntax"></a>Syntaxe

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parametry

*key*<br/>
Název klíče, který má být vytvořen nebo otevřen.

*Název hodnoty*<br/>
(Volitelné) Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, je přidána.

*regtype*<br/>
Typ přidávaný klíč registru. Může být jedna z následujících akcí: `text`, `dword`, `binary`, nebo `CString`.

## <a name="remarks"></a>Poznámky

**Rdx** C++ atribut vytvoří nebo upraví stávající klíč registru pro komponenty modelu COM. Atribut přidá makro BEGIN_RDX_MAP na objekt, který implementuje cílový člen. `RegistryDataExchange`, funkce vloženy jako výsledek BEGIN_RDX_MAP makra lze použít k přenosu dat mezi registru a datové členy

Tento atribut lze použít ve spojení s [coclass](coclass.md), [progid](progid.md), nebo [vi_progid –](vi-progid.md) atributy nebo jiné atributy, které zahrnuje jeden z nich.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída** nebo **struktura** člena|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

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

## <a name="see-also"></a>Viz také:

[COM – atributy](com-attributes.md)<br/>
[registration_script](registration-script.md)