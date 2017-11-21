---
title: "Třída typu coclass | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.coclass
dev_langs: C++
helpviewer_keywords: coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1699d47e9c3ca8778922af16587915fb3e6df45
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="coclass"></a>coclass
Vytvoří objekt COM, které můžete implementovat rozhraní modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[coclass]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Třída typu coclass** C++ atribut umístí do souboru generovaného .idl třída typu coclass konstrukce.  
  
 Při definování coclass, můžete také zadat [uuid](../windows/uuid-cpp-attributes.md), [verze](../windows/version-cpp.md), [dělení na vlákna](../windows/threading-cpp.md), [vi_progid –](../windows/vi-progid.md), a [progid ](../windows/progid.md) atributy. Pokud není zadána kterákoli z nich, bude vygenerována.  
  
 Pokud dva soubory hlaviček obsahovat tříd pomocí **třída typu coclass** atribut a nemáte zadejte identifikátor GUID, kompilátor použije stejný identifikátor GUID pro obě třídy a, bude výsledkem chyba MIDL.  Proto byste měli používat `uuid` atributu při použití **třída typu coclass**.  
  
 **Projekty knihovny ATL**  
  
 Když tento atribut předchází třídu nebo strukturu definice v projektu knihovny ATL ho:  
  
-   Vloží kód nebo data pro podporu automatické registrace pro objekt.  
  
-   Vloží kód nebo data pro podporu objekt třídy COM pro objekt.  
  
-   Vloží kód nebo data k implementaci **IUnknown** a nastaví objekt na objekt COM vytvořitelné.  
  
 Konkrétně jsou přidány následující základní třídy na objekt cíle:  
  
-   [Třída CComCoClass](../atl/reference/ccomcoclass-class.md) poskytuje model výchozí třídu objektu pro vytváření a agregaci pro objekt.  
  
-   [Třída CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) má šablony založené na třídě vláken modelu určeného [dělení na vlákna](../windows/threading-cpp.md) atribut. Pokud **dělení na vlákna** atribut není zadán, výchozí model vláken typu apartment.  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) se přidá, pokud [noncreatable –](../windows/noncreatable.md) pro cílový objekt není zadán atribut.  
  
 Nakonec se nahradí jakékoli duální rozhraní, které není definován pomocí vložených IDL odpovídající [IDispatchImpl](../atl/reference/idispatchimpl-class.md) třídy. Pokud duální rozhraní je definována v embedded IDL, konkrétní rozhraní v seznamu základní se nemění.  
  
 **Třída typu coclass** atribut také zpřístupní následující funkce pomocí vloženého kódu nebo v případě `GetObjectCLSID`, jako statickou metodu v základní třídě `CComCoClass`:  
  
-   `UpdateRegistry`zaregistruje tříd cílové třídy.  
  
-   `GetObjectCLSID`, která má relaci k registraci, lze také získat CLSID cílové třídy.  
  
-   **GetObjectFriendlyName** ve výchozím nastavení vrací řetězec ve formátu "\<*název cílové třídy*> `Object`". Pokud tato funkce je již přítomen, tam není přidaný. Přidejte tuto funkci k třídě cíle vrátit příjemnější název než ten, který automaticky generovány.  
  
-   **GetProgID**, která má relaci k registraci, vrátí řetězec zadaný [progid](../windows/progid.md) atribut.  
  
-   **GetVersionIndependentProgID** má stejné funkce jako **GetProgID**, ale vrátí řetězec zadaný s [vi_progid –](../windows/vi-progid.md).  
  
 Jsou provedeny následující změny, které se vztahují k mapu modelu COM, k třídě cíle:  
  
-   Mapa modelu COM se přidá s položky pro všechny rozhraní, která je odvozena od třídy cíle a všechny položky, které jsou určené [COM – vstupní body rozhraní](../mfc/com-interface-entry-points.md) atribut nebo těch, které vyžadují [agregace](../windows/aggregates.md) atribut.  
  
-   [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto) makro se vloží do modelu COM mapy.
  
 Název třída typu coclass vygenerovaných souborů .idl pro třídu, bude mít stejný název jako třída.  Například a odkazy na následující příklad a použijte pro přístup k ID třídy pro coclass CMyClass, v klientovi prostřednictvím soubor hlavičky generované MIDL CLSID_CMyClass.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití **třída typu coclass** atribut:  
  
```  
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
  
 Následující příklad ukazuje, jak přepsat výchozí implementaci funkci, která se zobrazí v kódu vloženy **třída typu coclass** atribut. V tématu [/Fx](../build/reference/fx-merge-injected-code.md) Další informace o zobrazení vloženého kódu. Všechny základní třídy nebo rozhraní, které používáte pro třídu se zobrazí ve vloženém kódu.   Dál platí Pokud třída je zahrnutá ve výchozím nastavení ve vloženém kódu a explicitně zadáte tuto třídu jako základ pro vaše třída typu coclass, zprostředkovatele atribut bude formulář zadaný v kódu.  
  
```  
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
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [COM – atributy](../windows/com-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject –](../windows/appobject.md)