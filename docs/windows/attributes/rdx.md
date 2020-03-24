---
title: RDX (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f0140b759b1d78eb1284213a0dc47d9600b2a83b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214627"
---
# <a name="rdx"></a>rdx

Vytvoří klíč registru nebo upraví existující klíč registru.

## <a name="syntax"></a>Syntaxe

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parametry

*key*<br/>
Název klíče, který má být vytvořen nebo otevřen.

*hodnoty*<br/>
Volitelné Určuje pole hodnoty, které se má nastavit. Pokud pole hodnota s tímto názvem ještě v klíči neexistuje, přidá se.

*regtype*<br/>
Typ přidávaného klíče registru. Může to být jedna z následujících: `text`, `dword`, `binary`nebo `CString`.

## <a name="remarks"></a>Poznámky

Atribut **RDX** C++ vytvoří nebo upraví existující klíč registru pro komponentu com. Atribut přidá makro BEGIN_RDX_MAP do objektu, který implementuje cílový člen. `RegistryDataExchange`, funkce vložená jako výsledek makra BEGIN_RDX_MAP, se dá použít k přenosu dat mezi registrem a datovými členy.

Tento atribut lze použít ve spojení s atributy [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) nebo s jinými atributy, které implikují jednu z nich.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|člen **třídy** nebo **struktury**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Příklad

Následující kód přidá do systému klíč registru s názvem hodnota, který popisuje komponentu CMyClass COM.

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

[COM – atributy](com-attributes.md)<br/>
[registration_script](registration-script.md)
