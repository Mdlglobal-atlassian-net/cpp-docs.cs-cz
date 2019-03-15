---
title: Nejčastější dotazy k programování s atributy
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 89c37b2fe81a414bdd02d73e3c3dfd5205a03831
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815876"
---
# <a name="attribute-programming-faq"></a>Nejčastější dotazy k programování s atributy

Toto téma poskytuje odpovědi na následující nejčastější dotazy:

- [Co je HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Když je nutné zadat název parametru atributu](#vcconattributeprogrammmingfaqanchor2)

- [Můžete použít komentáře v bloku atributu?](#vcconattributeprogrammmingfaqanchor3)

- [Jak atributy komunikovat s dědičnosti?](#vcconattributeprogrammmingfaqanchor4)

- [Jak můžete použít atributy v bez atributové projekt knihovny ATL?](#vcconattributeprogrammmingfaqanchor5)

- [Použití souboru v projektu s atributy IDL](#vcconattributeprogrammmingfaqanchor6)

- [Můžete upravit kód, který se vloží atributem?](#vcconattributeprogrammmingfaqanchor7)

- [Jak můžu vpřed deklarovat s atributy rozhraní?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Můžete použít atributy na třídu odvozenou z třídy, která rovněž používá atributy?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="vcconattributeprogrammmingfaqanchor1"></a> Co je HRESULT?

HRESULT je jednoduchý datový typ, který se často používá jako návratovou hodnotu tak, že atributy a knihovny ATL obecně. Následující tabulka popisuje různé hodnoty. Další hodnoty jsou obsaženy v souboru winerror.h záhlaví.

|Název|Popis|Hodnota|
|----------|-----------------|-----------|
|S_OK|Operace byla úspěšná.|0x00000000|
|E_UNEXPECTED, JE-|Došlo k neočekávané chybě|0x8000FFFF|
|E_NOTIMPL|Není implementováno|0x80004001|
|E_OUTOFMEMORY|Nepovedlo se přidělit dost paměti|0x8007000E|
|E_INVALIDARG|Jeden nebo více argumentů jsou neplatné|0x80070057|
|E_NOINTERFACE|Rozhraní není podporováno|0x80004002|
|E_POINTER|Neplatný ukazatel|0x80004003|
|E_HANDLE|Neplatný popisovač|0x80070006|
|E_ABORT|Operace byla přerušena.|0x80004004|
|E_FAIL|Neurčená chyba|0x80004005|
|E_ACCESSDENIED|Obecná chyba odepření přístupu|0x80070005|

##  <a name="vcconattributeprogrammmingfaqanchor2"></a> Když je nutné zadat název parametru atributu

Ve většině případů, pokud atribut má jeden parametr, tento parametr je pojmenován. Tento název se nevyžaduje při vkládání atribut ve vašem kódu. Například následující použití příkazu [agregovatelné](aggregatable.md) atribut:

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

je přesně stejný jako:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Následující atributy však máte jeden, nepojmenované parametry:

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="vcconattributeprogrammmingfaqanchor3"></a> Můžete použít komentáře v bloku atributu?

Můžete použít jeden řádek a více řádků komentáře v bloku atributu. Však nelze použít buď styl komentář mezi kulaté závorky obsahující parametry atributu.

Je povoleno následující:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Je zakázáno následující:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="vcconattributeprogrammmingfaqanchor4"></a> Jak atributy komunikovat s dědičnosti?

S atributy a zjednodušeně třídy můžete dědit z jiné třídy, které pravděpodobně samy přiřadit nebo ne. Odvozování z třídy s atributy výsledek je stejný jako odvození z této třídy po zprostředkovatele atribut má transformaci jeho kód. Atributy nejsou přenášeny do odvozené třídy prostřednictvím dědičnosti jazyka C++. Poskytovatele atributu transformuje pouze kód pixelům jeho atributy.

##  <a name="vcconattributeprogrammmingfaqanchor5"></a> Jak můžete použít atributy v bez atributové projekt knihovny ATL?

Možná bude bez atributové projekt knihovny ATL, který má soubor .idl, a můžete začít přidávat s atributy objektů. V takovém případě použijte **Průvodce přidáním třídy** poskytnout kód.

##  <a name="vcconattributeprogrammmingfaqanchor6"></a> Použití souboru v projektu s atributy IDL

Může mít soubor .idl, který chcete použít v projektu ATL s atributy. V takovém případě byste použili [importidl –](importidl.md) atribut, zkompilujte soubor .idl do souboru .h (najdete v článku [MIDL – stránky vlastností](../../build/reference/midl-property-pages.md) v projektu **stránky vlastností** dialogové okno), a soubor .h pak zahrňte do projektu.

##  <a name="vcconattributeprogrammmingfaqanchor7"></a> Můžete upravit kód, který se vloží atributem?

Některé atributy vloží kód do vašeho projektu. Vložený kód můžete zobrazit pomocí [/Fx](../../build/reference/fx-merge-injected-code.md) – možnost kompilátoru. Je také možné zkopírovat kód z vloženého souboru a vložit do zdrojového kódu. To umožňuje upravovat chování atribut. Ale budete muset upravit jiných částí kódu také.

Následující příklad je výsledkem kopírování kódu injektovaného do souboru zdrojového kódu:

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Jak můžu vpřed deklarovat s atributy rozhraní?

Pokud se chystáte provést Dopředná deklarace s atributy rozhraní, musíte použít stejné atributy pro dopřednou deklarací, které platí pro deklaraci skutečné rozhraní. Musíte taky použít [exportovat](export.md) atribut Dopředná deklarace.

##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> Můžete použít atributy na třídu odvozenou z třídy, která rovněž používá atributy?

Ne, použití atributů na třídy odvozené z třídy, která rovněž používá atributy není podporováno.

## <a name="see-also"></a>Viz také

[Atributy C++ pro COM a .NET](cpp-attributes-com-net.md)