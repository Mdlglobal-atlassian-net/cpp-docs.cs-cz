---
title: modul (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a119ebcccea3881d7b595e0581e23f53c656b91c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200215"
---
# <a name="module-c"></a>module (C++)

Bloku knihovny definuje v souboru IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ module (
   type=dll,
   name=string,
   version=1.0,
   uuid=uuid,
   lcid=integer,
   control=boolean,
   helpstring=string,
   helpstringdll=string,
   helpfile=string,
   helpcontext=integer,
   helpstringcontext=integer,
   hidden=boolean,
   restricted=boolean,
   custom=string,
   resource_name=string,
) ];
```

### <a name="parameters"></a>Parametry

*typ* (volitelné)  
Může být jedna z následujících akcí:

- `dll` Přidá se funkcí a tříd, které umožňují výslednou knihovnu DLL, aby fungoval jako server COM v procesu. Jedná se o výchozí hodnotu.

- `exe` Přidá funkce a třídy, které umožňují Výsledný spustitelný soubor do funkce v podobě mimo procesový server COM.

- `service` Přidá funkce a třídy, které umožňují Výsledný spustitelný soubor do funkce v podobě služby NT.

- `unspecified` Zakáže injektáž kódu ATL související s atributem module: injektáž modulu ATL – třídy, globální instanci _AtlModule a vstupní bod funkce. Injektáž kódu ATL kvůli dalším atributům v projektu není zakázána.

*Název* (volitelné)  
Název bloku knihovny.

*verze* (volitelné)  
Číslo verze, kterou chcete přiřadit k bloku knihovny. Výchozí hodnota je 1.0.

*uuid*  
Jedinečné ID pro knihovnu. Pokud tento parametr vynecháte, ID budou automaticky generovány pro knihovnu. Je nutné načíst *uuid* bloku knihovny, které vám pomůžou s použitím identifikátoru **__uuidof (** *NázevKnihovny* **)**.

*lcid*  
Parametr lokalizace. Zobrazit [lcid](/windows/desktop/Midl/lcid) Další informace.

*ovládací prvek* (volitelné)  
Určuje, že jsou všechny třídy typu coclass v knihovně ovládací prvky.

*helpstring*  
Určuje knihovnu typů.

*helpstringdll –* (volitelné)  
Nastaví název souboru DLL pro použití k provádění vyhledávací řetězec dokumentu. Zobrazit [helpstringdll –](/windows/desktop/Midl/helpstringdll) pro další informace.

*HelpFile –* (volitelné)  
Název **pomáhají** soubor pro knihovnu typů.

*HelpContext* (volitelné)  
**Pomáhají ID** pro tuto knihovnu typů.

*helpstringcontext –* (volitelné)  
Zobrazit [helpstringcontext –](../windows/helpstringcontext.md) pro další informace.

*skryté* (volitelné)  
Zabrání zobrazení celou knihovnu. Toto použití je určena pro použití s ovládacími prvky. Hostitele je potřeba vytvořit nové knihovny typů, která obaluje ovládací prvek s rozšířených vlastností. Zobrazit [skryté](/windows/desktop/Midl/hidden) atribut MIDL pro další informace.

*s omezeným přístupem* (volitelné)  
Členové knihovny nejde volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) atribut MIDL pro další informace.

*vlastní* (volitelné)  
Jeden nebo více atributů; podobá se to [vlastní](../windows/custom-cpp.md) atribut. První parametr *vlastní* je identifikátor GUID atributu. Příklad:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*  
ID zdroje řetězce souboru .rgs použije k registraci knihovny DLL, spustitelný soubor, nebo že služba ID aplikace. Když v modulu je typ služby, tento argument se používá také k získání ID řetězec obsahující název služby.

> [!NOTE]
> Souboru .rgs a řetězec obsahující název služby by měl obsahovat stejnou číselnou hodnotu.

## <a name="remarks"></a>Poznámky

Pokud nezadáte *s omezeným přístupem* parametr [emitidl](../windows/emitidl.md), **modulu** se vyžaduje v libovolné aplikaci, která používá C++ atributy.

Bloku knihovny se vytvoří, pokud, kromě **modulu** atribut, zdrojový kód také používá [dispinterface](../windows/dispinterface.md), [duální](../windows/dual.md), [objekt](../windows/object-cpp.md), nebo atribut, který zahrnuje [coclass](../windows/coclass.md).

Jeden blok knihovny je povolen v souboru IDL. Několik záznamů modulu ve zdrojovém kódu se sloučí s nejnovější hodnotami parametrů se implementuje.

Pokud tento atribut se používá v rámci projektu, který používá knihovny ATL, chování změny atributů. Kromě výše uvedených chování atribut také vloží globální objekt (volá `_AtlModule`) správný typ a další podporu kód. Pokud je atribut samostatné, vloží třídy odvozené z typu správný modul. Pokud je atribut aplikován na třídu, přidá základní třídu typu správný modul. Správný typ je určen hodnotou *typ* parametr:

- `type` = **knihovny DLL**

   [Catldllmodulet –](../atl/reference/catldllmodulet-class.md) slouží jako základní třídu a standardní knihovny DLL vstupní body požadované pro COM server. Tyto vstupní body jsou [DllMain](/windows/desktop/Dlls/dllmain), [DllRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), a [ DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891).

- `type` = **soubor EXE**

   [Catlexemodulet –](../atl/reference/catlexemodulet-class.md) slouží jako základní třídy a standardní spustitelný soubor vstupního bodu [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **Služba**

   [Catlservicemodulet –](../atl/reference/catlservicemodulet-class.md) slouží jako základní třídy a standardní spustitelný soubor vstupního bodu [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **Tento parametr zadán**

   Zakáže injektáž kódu ATL související s atributem module.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit bloku knihovny v souboru generovaného IDL.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Následující kód ukazuje, že můžete zadat vlastní implementaci funkce, který se objevuje v kódu, který se vloží pomocí parametru **modulu**. Zobrazit [/Fx](../build/reference/fx-merge-injected-code.md) Další informace o zobrazení vloženého kódu. Za účelem přepsání jedna z funkcí vkládat stisknutím **modulu** atribut, ujistěte se, třídu, která bude obsahovat vaše implementace funkce a ujistěte se, **modulu** platí atribut pro danou třídu.

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[usesgetlasterror](../windows/usesgetlasterror.md)  
[Knihovna](/windows/desktop/Midl/library)  
[helpcontext](../windows/helpcontext.md)  
[helpstring](../windows/helpstring.md)  
[helpfile](../windows/helpfile.md)  
[Verze](../windows/version-cpp.md)  