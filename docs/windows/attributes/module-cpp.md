---
title: modul (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 9d4f9e23aaf182e28930ba3a4462b07533ba9015
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754379"
---
# <a name="module-c"></a>module (C++)

Definuje blok knihovny v souboru .idl.

## <a name="syntax"></a>Syntaxe

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
(Nepovinné) Může to být jedna z následujících možností:

- `dll`Přidá funkce a třídy, které umožňují výslednou dll fungovat jako neprocesový server COM. Toto je výchozí hodnota.

- `exe`Přidá funkce a třídy, které umožňují výsledný spustitelný soubor fungovat jako mimo proces COM server.

- `service`Přidá funkce a třídy, které umožňují výsledný spustitelný soubor fungovat jako služba NT.

- `unspecified`Zakáže vkládání kódu KNIHOVNY ATL souvisejícího s atributem modulu: vkládání třídy modulu ATL, globální instance _AtlModule a funkce vstupního bodu. Nezakáže vkládání kódu KNIHOVNY ATL z důvodu jiných atributů v projektu.

*Jméno*<br/>
(Nepovinné) Název bloku knihovny.

*Verze*<br/>
(Nepovinné) Číslo verze, které chcete přiřadit bloku knihovny. Výchozí hodnota je 1,0.

*Uuid*<br/>
Jedinečné ID knihovny. Pokud tento parametr vynecháte, bude pro knihovnu automaticky vygenerováno ID. Možná budete muset načíst *uuid* bloku knihovny, který můžete udělat pomocí identifikátoru **__uuidof(** *název knihovny* **).**

*lcid*<br/>
Lokalizační parametr. Viz [lcid](/windows/win32/Midl/lcid) pro více informací.

*Ovládací prvek*<br/>
(Nepovinné) Určuje, že všechny spolutřídy v knihovně jsou ovládací prvky.

*helpstring*<br/>
Určuje knihovnu typů.

*helpstringdll*<br/>
(Nepovinné) Nastaví název souboru DLL, který se má použít k provedení vyhledávání řetězců dokumentu. Další informace naleznete v [tématu helpstringdll.](/windows/win32/Midl/helpstringdll)

*helpfile*<br/>
(Nepovinné) Název souboru **nápovědy** pro knihovnu typů.

*helpcontext*<br/>
(Nepovinné) **ID nápovědy** pro tuto knihovnu typů.

*helpstringcontext*<br/>
(Nepovinné) Další informace naleznete [v tématu helpstringcontext.](helpstringcontext.md)

*Skryté*<br/>
(Nepovinné) Zabrání zobrazení celé knihovny. Toto použití je určeno pro použití s ovládacími prvky. Hostitelé musí vytvořit novou knihovnu typů, která obtéká ovládací prvek s rozšířenými vlastnostmi. Další informace naleznete v [atributu hidden](/windows/win32/Midl/hidden) MIDL.

*restricted*<br/>
(Nepovinné) Členy knihovny nelze volat libovolně. Další informace naleznete v atributu [MIDL s omezeným](/windows/win32/Midl/restricted) přístupem.

*Vlastní*<br/>
(Nepovinné) Jeden nebo více atributů; To je podobné [vlastní](custom-cpp.md) atribut. První parametr *vlastní* je GUID atributu. Příklad:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
ID prostředku řetězce souboru RGS použitého k registraci ID aplikace DLL, spustitelného souboru nebo služby. Pokud je modul typu služby, tento argument se také používá k získání ID řetězce obsahující název služby.

> [!NOTE]
> Soubor RGS i řetězec obsahující název služby by měly obsahovat stejnou číselnou hodnotu.

## <a name="remarks"></a>Poznámky

Pokud nezadáte *parametr restricted* pro [emitidl](emitidl.md), **modul** je vyžadován v libovolném programu, který používá atributy Jazyka C++.

Blok knihovny bude vytvořen, pokud kromě atributu **modulu** zdrojový kód také používá [dispinterface](dispinterface.md), [dual](dual.md), [object](object-cpp.md)nebo atribut, který implikuje [coclass](coclass.md).

V souboru .idl je povolen jeden blok knihovny. Více položek modulu ve zdrojovém kódu bude sloučeno s nejnovějšími hodnotami parametrů, které jsou implementovány.

Pokud tento atribut se používá v rámci projektu, který používá KNIHOVNU ATL, chování atributu se změní. Kromě výše uvedeného chování atribut také vloží globální `_AtlModule`objekt (nazývaný) správného typu a další kód podpory. Pokud je atribut samostatný, vloží třídu odvozenou od správného typu modulu. Pokud je atribut použit pro třídu, přidá základní třídu správného typu modulu. Správný typ je určen hodnotou parametru *typu:*

- `type` = **Knihovny dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) se používá jako základní třída a standardní vstupní body DLL požadované pro server COM. Tyto vstupní body jsou [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)a [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- `type` = **Exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) se používá jako základní třída a standardní spustitelný vstupní bod [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **Služby**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) se používá jako základní třída a standardní spustitelný vstupní bod [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **Nespecifikované**

   Zakáže vkládání kódu KNIHOVNY ATL souvisejícího s atributem modulu.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit blok knihovny v generovaném souboru .idl.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Následující kód ukazuje, že můžete poskytnout vlastní implementaci funkce, která by se objevila v kódu, který byl vložen v důsledku použití **modulu**. Viz [/Fx](../../build/reference/fx-merge-injected-code.md) další informace o zobrazení vloženého kódu. Chcete-li přepsat jednu z funkcí vložených atributem **modulu,** vytvořte třídu, která bude obsahovat implementaci funkce, a proveďte atribut **modulu** pro tuto třídu.

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Kdekoliv|
|**Opakovatelnou**|Ne|
|**Povinné atributy**|Žádná|
|**Neplatné atributy**|Žádná|

Další informace naleznete v [tématu Kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy IDL](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[Atributy Typedef, Enum, Union a Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Knihovny](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[Verze](version-cpp.md)
