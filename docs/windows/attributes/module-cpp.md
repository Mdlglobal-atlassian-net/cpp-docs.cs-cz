---
title: Module (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: daa0ae4aea5ff2a1a3312efcf3c39f43b541abf6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514921"
---
# <a name="module-c"></a>module (C++)

Definuje blok knihovny v souboru. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parametry

*type*<br/>
Volitelné Může to být jedna z následujících:

- `dll`Přidá funkce a třídy, které umožňují výsledné knihovně DLL fungovat jako vnitroprocesové server COM. Jedná se o výchozí hodnotu.

- `exe`Přidá funkce a třídy, které umožní výslednému spustitelnému souboru fungovat jako nezpracovaný server COM.

- `service`Přidá funkce a třídy, které umožní výslednému spustitelnému souboru fungovat jako služba NT.

- `unspecified`Zakáže vkládání kódu ATL, který souvisí s atributem Module: vložení třídy modulu ATL, globálních instancí _AtlModule a funkcí vstupního bodu. Nezakáže vkládání kódu ATL z důvodu jiných atributů v projektu.

*name*<br/>
Volitelné Název bloku knihovny.

*version*<br/>
Volitelné Číslo verze, které chcete přiřadit k bloku knihovny. Výchozí hodnota je 1,0.

*uuid*<br/>
Jedinečné ID knihovny. Pokud tento parametr vynecháte, ID se pro knihovnu vygeneruje automaticky. Možná budete muset načíst *UUID* bloku vaší knihovny, který můžete provést pomocí identifikátoru **__uuidof (** *Library* **)** .

*lcid*<br/>
Parametr Localization Další informace naleznete v tématu [LCID](/windows/win32/Midl/lcid) .

*control*<br/>
Volitelné Určuje, že všechny třídy coclass v knihovně jsou ovládací prvky.

*helpstring*<br/>
Určuje knihovnu typů.

*helpstringdll*<br/>
Volitelné Nastaví název souboru. dll, který se má použít k provedení vyhledávání řetězce dokumentu. Další informace najdete v tématu [helpstringdll](/windows/win32/Midl/helpstringdll) .

*helpfile*<br/>
Volitelné Název souboru s **nápovědu** pro knihovnu typů

*helpcontext*<br/>
Volitelné **ID nápovědu** pro tuto knihovnu typů

*helpstringcontext*<br/>
Volitelné Další informace najdete v tématu [helpstringcontext](helpstringcontext.md) .

*hidden*<br/>
Volitelné Zabraňuje zobrazení celé knihovny. Toto použití je určeno pro použití s ovládacími prvky. Hostitelé musí vytvořit novou knihovnu typů, která ovládací prvek zabalí pomocí rozšířených vlastností. Další informace [](/windows/win32/Midl/hidden) naleznete u skrytého atributu MIDL.

*restricted*<br/>
Volitelné Členy knihovny nelze volat libovolně. Další informace [](/windows/win32/Midl/restricted) naleznete u atributu Restricted MIDL.

*custom*<br/>
Volitelné Jeden nebo více atributů; To se podobá [vlastnímu](custom-cpp.md) atributu. První parametr *vlastní* je identifikátor GUID atributu. Příklad:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
ID prostředku řetězce souboru. rgs používaného k registraci ID aplikace DLL, spustitelného souboru nebo služby. Pokud je modul typu služba, tento argument slouží také k získání ID řetězce obsahujícího název služby.

> [!NOTE]
> Soubor. rgs i řetězec obsahující název služby by měly obsahovat stejnou číselnou hodnotu.

## <a name="remarks"></a>Poznámky

Pokud nezadáte parametr *s omezením* na [emitidl](emitidl.md), **modul** je vyžadován v jakémkoli programu, C++ který používá atributy.

Blok knihovny bude vytvořen, pokud kromě atributu **modulu** používá zdrojový kód také funkci [IDispatch](dispinterface.md), [Dual](dual.md), [Object](object-cpp.md)nebo atribut, který implikuje [třídu typu coclass](coclass.md).

V souboru IDL je povolen jeden blok knihovny. Bude sloučeno více položek modulu ve zdrojovém kódu s nejnovějšími hodnotami parametrů, které jsou implementovány.

Pokud se tento atribut používá v rámci projektu, který používá ATL, chování atributu se změní. Kromě výše uvedeného chování atribut také vloží globální objekt (nazývaný `_AtlModule`) správného typu a další kód podpory. Pokud je atribut samostatný, vloží třídu odvozenou ze správného typu modulu. Pokud je atribut použit pro třídu, přidá základní třídu správného typu modulu. Správný typ je určen hodnotou parametru *typu* :

- `type` = **DLL**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) se používá jako základní třída a standardní vstupní body knihovny DLL vyžadované pro server com. Tyto vstupní body jsou [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DLLUnregisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)a [DllGetClassObject](/previous-versions//dd797891\(v=vs.85\)).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) se používá jako základní třída a standardní spustitelný vstupní bod [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **službám**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) se používá jako základní třída a standardní spustitelný vstupní bod [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **neurčené**

   Zakáže vkládání kódu ATL, který souvisí s atributem Module.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit blok knihovny v generovaném souboru IDL.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Následující kód ukazuje, že můžete poskytnout vlastní implementaci funkce, která by se zobrazila v kódu, který byl vložen jako výsledek použití **modulu**. Další informace o zobrazení vloženého kódu naleznete v tématu [/FX](../../build/reference/fx-merge-injected-code.md) . Chcete-li přepsat jednu z funkcí, které jsou vloženy atributem **Module** , vytvořte třídu, která bude obsahovat vaši implementaci funkce, a nastavte u této třídy atribut **Module** .

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
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[Knihovna](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)