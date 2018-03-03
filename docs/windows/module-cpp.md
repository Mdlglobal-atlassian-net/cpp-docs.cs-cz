---
title: modul (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75b41ea146096a60210918b5f21e7b6278e35001
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="module-c"></a>module (C++)
Knihovna bloku definuje v souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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
  
#### <a name="parameters"></a>Parametry  
 ***typ*** (volitelné)  
 Může být jedna z následujících akcí:  
  
-   **knihovny DLL** přidá funkce a třídy, které umožňují výsledné DLL fungovat jako server COM v procesu. Jedná se o výchozí hodnotu.  
  
-   **exe** přidá funkce a třídy, které umožňují výsledná fungovat jako mimo server COM procesu spustitelného souboru.  
  
-   **Služba** přidá funkce a třídy, které umožňují výsledná spustitelné funkce jako služba NT.  
  
-   **neurčené** zakáže injekce kódu ATL související s atribut modulu: vkládání ATL Module – třídy, globální instance _AtlModule a vstupní bod funkce.  Vkládání kódu ATL z důvodu další atributy v projektu není zakázána.  
  
 ***název*** (volitelné)  
 Název knihovny bloku.  
  
 ***verze*** (volitelné)  
 Číslo verze, které chcete přiřadit bloku knihovny. Výchozí hodnota je 1.0.  
  
 `uuid`  
 Jedinečné ID pro knihovnu. Pokud tento parametr vynecháte, ID budou automaticky generovány pro knihovnu. Budete muset načíst *uuid* bloku knihovny, což lze provést pomocí identifikátor **__uuidof – (***NázevKnihovny***)**.  
  
 **lcid**  
 Lokalizace parametr. V tématu [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) Další informace.  
  
 **ovládací prvek** (volitelné)  
 Určuje, že jsou všechny třídy typu coclass v knihovně ovládací prvky.  
  
 **helpstring**  
 Určuje knihovny typů.  
  
 ***helpstringdll –*** (volitelné)  
 Nastaví název souboru DLL používat k provádění vyhledávací řetězec dokumentu. V tématu [helpstringdll –](http://msdn.microsoft.com/library/windows/desktop/aa366860) Další informace.  
  
 **soubor nápovědy** (volitelné)  
 Název souboru nápovědy knihovny typů.  
  
 **HelpContext –** (volitelné)  
 Pomůže ID pro tuto knihovnu typů.  
  
 **helpstringcontext –** (volitelné)  
 V tématu [helpstringcontext –](../windows/helpstringcontext.md) Další informace.  
  
 **Skrytá** (volitelné)  
 Zabraňuje celou knihovnu zobrazení. Toto použití je určena pro použití s ovládacími prvky. Hostitelů je nutné vytvořit nové knihovny typů, které zabaluje s rozšířených vlastností ovládacího prvku. Najdete v článku [Skrytá](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL atribut pro další informace.  
  
 **s omezeným přístupem** (volitelné)  
 Členové knihovny nelze volat libovolně. Najdete v článku [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL atribut pro další informace.  
  
 ***vlastní*** (volitelné)  
 Jeden nebo více atributů; Toto je podobná [vlastní](../windows/custom-cpp.md) atribut. První parametr `custom` je identifikátor GUID atributu. Příklad:  
  
```  
[module(custom={guid,1}, custom={guid1,2})]  
```  
  
 **resource_name**  
 ID prostředku řetězec souboru použitá pro zaregistrování ID aplikace knihovny DLL, spustitelný soubor nebo služby. Pokud je modul služby typu, tento argument se taky používají k získání ID řetězec obsahující název služby.  
  
> [!NOTE]
>  Souboru a řetězce, který obsahuje název služby by měl obsahovat stejnou číselnou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud nezadáte **s omezeným přístupem** parametru [emitidl –](../windows/emitidl.md), **modulu** je nutné v žádné program, který používá atributy C++.  
  
 Blok knihovny bude vytvořen, pokud, kromě **modulu** atribut, zdrojový kód také používá [dispinterface](../windows/dispinterface.md), [duální](../windows/dual.md), [objekt](../windows/object-cpp.md), nebo atribut, který znamená [třída typu coclass](../windows/coclass.md).  
  
 V souboru IDL je povoleno jeden blok knihovny. Několik záznamů modulu ve zdrojovém kódu bude sloučen s nejnovější hodnoty parametru se implementuje.  
  
 Pokud tento atribut se používá v rámci projekt, který používá ATL chování změny atributů. Kromě výše uvedených chování atribut také vloží globální objekt (nazývá **_AtlModule**) správný typ a další podporu kód. Pokud je atribut samostatné, vloží třídy odvozené od typu správný modul. Pokud atribut se použije na třídu, přidá základní třídu typu správný modul. Správný typ je určen hodnotou `type` parametr:  
  
-   `type` = **knihovny DLL**  
  
     [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) slouží jako základní třídy a standardní knihovny DLL položku body požadované pro COM server. Tyto vstupní body jsou [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583), [DllRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368), a [ DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/dd797891).  
  
-   `type` = **soubor EXE**  
  
     [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) slouží jako základní třídy a standardní spustitelný soubor vstupního bodu [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **služby**  
  
     [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) slouží jako základní třídy a standardní spustitelný soubor vstupního bodu [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **Tento parametr**  
  
     Zakáže injekce kódu ATL související s atribut modulu.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit blok knihovny v souboru generovaného .idl.  
  
```  
// cpp_attr_ref_module1.cpp  
// compile with: /LD  
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];  
```  
  
 Následující kód ukazuje, že můžete zadat vlastní implementace funkce, které by se zobrazí v kódu, který byl v důsledku použití Vložit **modulu**. V tématu [/Fx](../build/reference/fx-merge-injected-code.md) Další informace o zobrazení vloženého kódu. Chcete-li přepsat jedna z funkcí vložená **modulu** atribut, ujistěte se, třídu, která obsahuje implementaci funkce a ujistěte se, **modulu** atribut platí pro tuto třídu.  
  
```  
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
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [usesgetlasterror –](../windows/usesgetlasterror.md)   
 [Knihovna](http://msdn.microsoft.com/library/windows/desktop/aa367069)   
 [HelpContext –](../windows/helpcontext.md)   
 [helpstring –](../windows/helpstring.md)   
 [soubor nápovědy](../windows/helpfile.md)   
 [verze](../windows/version-cpp.md)   
