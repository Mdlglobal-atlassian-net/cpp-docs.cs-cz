---
title: modul (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 5692e07e71683b1c24f86a43e989ee3df1fbe904
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570609"
---
# <a name="module-c"></a>module (C++)

Bloku knihovny definuje v souboru IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
(Volitelné) Může být jedna z následujících akcí:

- `dll` Přidá se funkcí a tříd, které umožňují výslednou knihovnu DLL, aby fungoval jako server COM v procesu. Jedná se o výchozí hodnotu.

- `exe` Přidá funkce a třídy, které umožňují Výsledný spustitelný soubor do funkce v podobě mimo procesový server COM.

- `service` Přidá funkce a třídy, které umožňují Výsledný spustitelný soubor do funkce v podobě služby NT.

- `unspecified` Zakáže injektáž kódu ATL související s atributem module: injektáž modulu ATL – třídy, globální instanci _AtlModule a vstupní bod funkce. Injektáž kódu ATL kvůli dalším atributům v projektu není zakázána.

*Jméno*<br/>
(Volitelné) Název bloku knihovny.

*version*<br/>
(Volitelné) Číslo verze, kterou chcete přiřadit k bloku knihovny. Výchozí hodnota je 1.0.

*uuid*<br/>
Jedinečné ID pro knihovnu. Pokud tento parametr vynecháte, ID budou automaticky generovány pro knihovnu. Je nutné načíst *uuid* bloku knihovny, které vám pomůžou s použitím identifikátoru **__uuidof (** *NázevKnihovny* **)**.

*lcid*<br/>
Parametr lokalizace. Zobrazit [lcid](/windows/desktop/Midl/lcid) Další informace.

*control*<br/>
(Volitelné) Určuje, že jsou všechny třídy typu coclass v knihovně ovládací prvky.

*helpstring*<br/>
Určuje knihovnu typů.

*helpstringdll*<br/>
(Volitelné) Nastaví název souboru DLL pro použití k provádění vyhledávací řetězec dokumentu. Zobrazit [helpstringdll –](/windows/desktop/Midl/helpstringdll) pro další informace.

*helpfile*<br/>
(Volitelné) Název **pomáhají** soubor pro knihovnu typů.

*helpcontext*<br/>
(Volitelné) **Pomáhají ID** pro tuto knihovnu typů.

*helpstringcontext*<br/>
(Volitelné) Zobrazit [helpstringcontext –](helpstringcontext.md) pro další informace.

*hidden*<br/>
(Volitelné) Zabrání zobrazení celou knihovnu. Toto použití je určena pro použití s ovládacími prvky. Hostitele je potřeba vytvořit nové knihovny typů, která obaluje ovládací prvek s rozšířených vlastností. Zobrazit [skryté](/windows/desktop/Midl/hidden) atribut MIDL pro další informace.

*restricted*<br/>
(Volitelné) Členové knihovny nejde volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) atribut MIDL pro další informace.

*custom*<br/>
(Volitelné) Jeden nebo více atributů; podobá se to [vlastní](custom-cpp.md) atribut. První parametr *vlastní* je identifikátor GUID atributu. Příklad:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
ID zdroje řetězce souboru .rgs použije k registraci knihovny DLL, spustitelný soubor, nebo že služba ID aplikace. Když v modulu je typ služby, tento argument se používá také k získání ID řetězec obsahující název služby.

> [!NOTE]
> Souboru .rgs a řetězec obsahující název služby by měl obsahovat stejnou číselnou hodnotu.

## <a name="remarks"></a>Poznámky

Pokud nezadáte *s omezeným přístupem* parametr [emitidl](emitidl.md), **modulu** se vyžaduje v libovolné aplikaci, která používá C++ atributy.

Bloku knihovny se vytvoří, pokud, kromě **modulu** atribut, zdrojový kód také používá [dispinterface](dispinterface.md), [duální](dual.md), [objekt](object-cpp.md), nebo atribut, který zahrnuje [coclass](coclass.md).

Jeden blok knihovny je povolen v souboru IDL. Několik záznamů modulu ve zdrojovém kódu se sloučí s nejnovější hodnotami parametrů se implementuje.

Pokud tento atribut se používá v rámci projektu, který používá knihovny ATL, chování změny atributů. Kromě výše uvedených chování atribut také vloží globální objekt (volá `_AtlModule`) správný typ a další podporu kód. Pokud je atribut samostatné, vloží třídy odvozené z typu správný modul. Pokud je atribut aplikován na třídu, přidá základní třídu typu správný modul. Správný typ je určen hodnotou *typ* parametr:

- `type` = **knihovny DLL**

   [Catldllmodulet –](../../atl/reference/catldllmodulet-class.md) slouží jako základní třídu a standardní knihovny DLL vstupní body požadované pro COM server. Tyto vstupní body jsou [DllMain](/windows/desktop/Dlls/dllmain), [DllRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), a [ DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891).

- `type` = **soubor EXE**

   [Catlexemodulet –](../../atl/reference/catlexemodulet-class.md) slouží jako základní třídy a standardní spustitelný soubor vstupního bodu [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **Služba**

   [Catlservicemodulet –](../../atl/reference/catlservicemodulet-class.md) slouží jako základní třídy a standardní spustitelný soubor vstupního bodu [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559).

- `type` = **Tento parametr zadán**

   Zakáže injektáž kódu ATL související s atributem module.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit bloku knihovny v souboru generovaného IDL.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Následující kód ukazuje, že můžete zadat vlastní implementaci funkce, který se objevuje v kódu, který se vloží pomocí parametru **modulu**. Zobrazit [/Fx](../../build/reference/fx-merge-injected-code.md) Další informace o zobrazení vloženého kódu. Za účelem přepsání jedna z funkcí vkládat stisknutím **modulu** atribut, ujistěte se, třídu, která bude obsahovat vaše implementace funkce a ujistěte se, **modulu** platí atribut pro danou třídu.

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

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Knihovna](/windows/desktop/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)