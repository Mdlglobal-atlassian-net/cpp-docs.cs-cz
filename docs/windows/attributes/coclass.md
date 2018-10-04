---
title: Coclass (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a76fa402cd270bfc7d0fa87902362de50c55a73
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789313"
---
# <a name="coclass"></a>coclass

Vytvoří objekt modelu COM, které můžete implementovat rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[coclass]
```

## <a name="remarks"></a>Poznámky

**Coclass** C++ atribut umístí konstrukt coclass v souboru generovaného IDL.

Při definování coclass, můžete také určit [uuid](uuid-cpp-attributes.md), [verze](version-cpp.md), [dělení na vlákna](threading-cpp.md), [vi_progid –](vi-progid.md), a [progid ](progid.md) atributy. Pokud některý z nich není zadán, bude vygenerována.

Pokud dva soubory hlaviček obsahují třídy, které se **coclass** atribut a identifikátor GUID nezadávejte kompilátor použije stejný identifikátor GUID pro obě třídy a které způsobí chybu MIDL.  Proto byste měli použít `uuid` atribut při použití **coclass**.

**Projekty knihovny ATL**

Pokud tento atribut předchází definici třídy nebo struktury v projektu knihovny ATL ho:

- Vkládá kód nebo dat pro podporu automatické registrace pro objekt.

- Vkládá kód nebo dat pro podporu objekt pro vytváření tříd modelu COM pro objekt.

- Vkládá kód nebo data k implementaci `IUnknown` a nastavte objekt vytvořitelný modelem COM objektu.

Konkrétně následující základní třídy jsou přidány do cílového objektu:

- [Třídy CComCoClass](../../atl/reference/ccomcoclass-class.md) poskytuje výchozí třídu objektu pro vytváření a agregace model pro objekt.

- [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md) má šablony založené na třídě model dělení na vlákna určené [dělení na vlákna](threading-cpp.md) atribut. Pokud `threading` atribut není zadán, je výchozí model vláken typu apartment.

- [Iprovideclassinfo2impl –](../../atl/reference/iprovideclassinfo2impl-class.md) se přidá [noncreatable](noncreatable.md) pro cílový objekt není zadán atribut.

Nakonec duální rozhraní, který není definován pomocí vložené IDL nahradí odpovídající [třídou IDispatchImpl](../../atl/reference/idispatchimpl-class.md) třídy. Pokud duální rozhraní je definováno v vložené IDL, zejména rozhraní v seznamu základních se nezmění.

**Coclass** atribut rovněž provede následující funkce dostupné prostřednictvím vloženého kódu nebo v případě `GetObjectCLSID`, jako statickou metodu v základní třídě `CComCoClass`:

- `UpdateRegistry` zaregistruje třídu továren cílové třídy.

- `GetObjectCLSID`, která má vztah k registraci, také umožňuje získat identifikátor CLSID cílové třídy.

- `GetObjectFriendlyName` ve výchozím nastavení vrací řetězec ve formátu "\<*název cílové třídy*> `Object`". Pokud tato funkce je již k dispozici, tam není přidaný. Přidejte tuto funkci do cílové třídy se vraťte lépe vyhovující název než ten, který automaticky generovány.

- `GetProgID`, která má vztah k registraci, vrátí řetězec zadaný [progid](progid.md) atribut.

- `GetVersionIndependentProgID` má stejné funkce jako `GetProgID`, ale vrací řetězec zadaný s [vi_progid –](vi-progid.md).

Cílové třídy jsou provedeny následující změny, které se vztahují k mapy modelu COM:

- Mapy modelu COM se přidá s záznamy pro všechny cílové třídy je odvozen z rozhraní a všechny položky, které jsou určené [COM – vstupní body rozhraní](../../mfc/com-interface-entry-points.md) atributu nebo jsou vyžadované [agregace](aggregates.md) atribut.

- [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) – makro je vložen do objektu map COM.

Název třídy typu coclass v souboru IDL pro třídu vygenerované bude mít stejný název jako třída.  Například a odkazuje na následující příklad a pro přístup k ID třídy pro konstruktor coclass `CMyClass`, použijte v klientovi v souboru hlavičky generované MIDL `CLSID_CMyClass`.

## <a name="example"></a>Příklad

Následující kód ukazuje způsob použití **coclass** atribut:

```cpp
// cpp_attr_ref_coclass1.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]
class CMyClass : public I {};
```

Následující příklad ukazuje, jak lze přepsat výchozí implementace funkce, která se zobrazí v kódu vloženy **coclass** atribut. Zobrazit [/Fx](../../build/reference/fx-merge-injected-code.md) Další informace o zobrazení vloženého kódu. Všechny základní třídy nebo rozhraní, které můžete použít pro třídu se zobrazí ve vloženém kódu. Dále pokud explicitně neurčíte tuto třídu jako základ pro váš coclass, třída je zahrnuta ve výchozím nastavení ve vloženém kódu atribut poskytovatel použije formulář určili ve svém kódu.

```cpp
// cpp_attr_ref_coclass2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface bb {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class CMyClass : public bb {
public:
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

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
[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)