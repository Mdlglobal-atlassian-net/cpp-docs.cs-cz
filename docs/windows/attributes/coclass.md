---
title: coclass – třídaC++ (atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 76540e90fef2e840b91bb07f570a7b8c0987eb10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168328"
---
# <a name="coclass"></a>coclass

Vytvoří objekt modelu COM, který může implementovat rozhraní COM.

## <a name="syntax"></a>Syntaxe

```cpp
[coclass]
```

## <a name="remarks"></a>Poznámky

Atribut **Coclass** C++ umístí konstrukt coclass do generovaného souboru IDL.

Při definování třídy typu coclass můžete také zadat atributy [UUID](uuid-cpp-attributes.md), [verze](version-cpp.md), [vlákna](threading-cpp.md), [vi_progid](vi-progid.md)a [ProgID](progid.md) . Pokud některý z nich není zadán, bude vygenerován.

Pokud dva hlavičkové soubory obsahují třídy s atributem **Coclass** a NEZAURČUJÍ identifikátor GUID, kompilátor použije stejný identifikátor GUID pro obě třídy a to způsobí chybu MIDL.  Proto byste měli použít atribut `uuid` při použití **třídy coclass**.

**Projekty ATL**

Pokud tento atribut předchází definici třídy nebo struktury v projektu ATL, pak:

- Vloží kód nebo data pro podporu automatické registrace objektu.

- Vloží kód nebo data pro podporu objektu pro vytváření tříd modelu COM pro daný objekt.

- Vloží kód nebo data pro implementaci `IUnknown` a vytvoření objektu, který lze vytvořit pomocí modelu COM.

Konkrétně jsou do cílového objektu přidány následující základní třídy:

- [Třída CComCoClass](../../atl/reference/ccomcoclass-class.md) poskytuje výchozí objekt pro vytváření tříd a agregaci pro objekt.

- [Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) má šablonu založenou na třídě modelu vláken určené atributem [vláken](threading-cpp.md) . Pokud není zadán atribut `threading`, je výchozí model vláken typu apartment.

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) je přidán, pokud [atribut není](noncreatable.md) zadán pro cílový objekt.

Nakonec jakékoli duální rozhraní, které není definováno pomocí vloženého IDL, je nahrazeno odpovídající třídou [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) . Pokud je ve vloženém IDL definováno duální rozhraní, konkrétní rozhraní v základním seznamu se neupraví.

Atribut **Coclass** také poskytuje následující funkce, které jsou k dispozici prostřednictvím vloženého kódu, nebo v případě `GetObjectCLSID`jako statické metody v základní třídě `CComCoClass`:

- `UpdateRegistry` registruje továrny tříd cílové třídy.

- `GetObjectCLSID`, která souvisí s registrací, lze také použít k získání identifikátoru CLSID cílové třídy.

- `GetObjectFriendlyName` ve výchozím nastavení vrátí řetězec ve formátu "\<*cílový název třídy*> `Object`". Pokud je tato funkce již přítomna, není přidána. Přidejte tuto funkci do cílové třídy, aby se vrátil název příjemnější, než je ten, který se automaticky vygeneroval.

- `GetProgID`, která souvisí s registrací, vrátí řetězec určený atributem [ProgID](progid.md) .

- `GetVersionIndependentProgID` má stejné funkce jako `GetProgID`, ale vrátí řetězec zadaný pomocí [vi_progid](vi-progid.md).

Následující změny, které se vztahují k mapě modelu COM, jsou provedeny v cílové třídě:

- Je přidána mapa modelu COM s položkami pro všechna rozhraní, které je třída cíle odvozena od a všechny položky určené atributem [vstupní body rozhraní COM](../../mfc/com-interface-entry-points.md) nebo atributy vyžadované atributem [Aggregates](aggregates.md) .

- Do mapy COM je vloženo makro [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) .

Název třídy typu coclass generované v souboru IDL pro třídu bude mít stejný název jako třída.  Například a odkazování na následující příklad, pro přístup k ID třídy pro coclass `CMyClass`v klientovi pomocí souboru hlaviček generovaného pomocí MIDL použijte `CLSID_CMyClass`.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít atribut **Coclass** :

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

Následující příklad ukazuje, jak přepsat výchozí implementaci funkce, která se zobrazí v kódu vloženém atributem **Coclass** . Další informace o zobrazení vloženého kódu naleznete v tématu [/FX](../../build/reference/fx-merge-injected-code.md) . Jakékoli základní třídy nebo rozhraní, které používáte pro třídu, se zobrazí ve vloženém kódu. Pokud je třída ve vloženém kódu standardně zahrnutá ve výchozím nastavení a tuto třídu explicitně zadáte jako základ pro třídu coclass, poskytovatel atributu použije formulář zadaný ve vašem kódu.

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
