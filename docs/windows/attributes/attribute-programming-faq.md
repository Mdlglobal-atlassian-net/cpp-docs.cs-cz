---
title: Nejčastější dotazy k programování s atributy
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376067"
---
# <a name="attribute-programming-faq"></a>Nejčastější dotazy k programování s atributy

Toto téma odpovídá na následující často kladené otázky:

- [Co je HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Kdy musím zadat název parametru atributu?](#vcconattributeprogrammmingfaqanchor2)

- [Mohu použít komentáře v bloku atributů?](#vcconattributeprogrammmingfaqanchor3)

- [Jak atributy interagují s dědičností?](#vcconattributeprogrammmingfaqanchor4)

- [Jak lze použít atributy v projektu ATL bez atributů?](#vcconattributeprogrammmingfaqanchor5)

- [Jak lze použít soubor .idl v přiděleném projektu?](#vcconattributeprogrammmingfaqanchor6)

- [Lze upravit kód, který je vložen atributem?](#vcconattributeprogrammmingfaqanchor7)

- [Jak mohu předat deklarovat přidělené rozhraní?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Lze použít atributy na třídu odvozené z třídy, která také používá atributy?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>Co je HRESULT?

HRESULT je jednoduchý datový typ, který se často používá jako vrácená hodnota atributy a KNIHOVNA ATL obecně. Následující tabulka popisuje různé hodnoty. Další hodnoty jsou obsaženy v souboru záhlaví winerror.h.

|Name (Název)|Popis|Hodnota|
|----------|-----------------|-----------|
|S_OK|Operace byla úspěšná.|0x00000000|
|E_UNEXPECTED|Neočekávaná chyba|0x8000FFFF|
|E_NOTIMPL|Není implementováno|0x80004001|
|E_OUTOFMEMORY|Přidělení potřebné paměti se nezdařilo.|0x8007000E|
|E_invalidarg|Jeden nebo více argumentů je neplatných.|0x80070057|
|E_NOINTERFACE|Žádné takové rozhraní není podporováno|0x80004002|
|E_POINTER|Neplatný ukazatel|0x80004003|
|E_HANDLE|Neplatný popisovač|0x80070006|
|E_ABORT|Operace byla přerušena.|0x80004004|
|E_fail|Nespecifikovaná porucha|0x80004005|
|E_ACCESSDENIED|Obecná chyba odepření přístupu|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>Kdy musím zadat název parametru atributu?

Ve většině případů, pokud atribut má jeden parametr, tento parametr je pojmenován. Tento název není vyžadován při vkládání atributu do kódu. Například následující použití atributu [agregatable:](aggregatable.md)

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

Následující atributy však mají jeden, nepojmenované parametry:

||||
|-|-|-|
|[call_as](call-as.md)|[Případě](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[Položka](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[Id](id.md)|
|[iid_is](iid-is.md)|[Import](import.md)|[importlib](importlib.md)|
|[Zahrnout](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[Zdroj](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>Mohu použít komentáře v bloku atributů?

V rámci bloku atributů můžete použít komentáře s jedním i více řádků. Nelze však použít ani jeden styl komentáře v závorce, které drží parametry atributu.

Je povoleno následující:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Následující je zakázáno:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>Jak atributy interagují s dědičností?

Můžete dědit jak přidělené, tak nepřiřazené třídy z jiných tříd, které mohou být samy přiřazeny nebo ne. Výsledek odvození z přiřazené třídy je stejný jako odvození z této třídy poté, co zprostředkovatel atributu transformoval svůj kód. Atributy nejsou přenášeny do odvozených tříd prostřednictvím dědičnosti jazyka C++. Zprostředkovatel atributů transformuje kód pouze v blízkosti jeho atributů.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>Jak lze použít atributy v projektu ATL bez atributů?

Můžete mít nepřiřazený projekt knihovny ATL, který má soubor .idl a můžete začít přidávat přiřazené objekty. V takovém případě použijte **Průvodce přidáním třídy** k zadání kódu.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>Jak lze použít soubor .idl v přiděleném projektu?

Můžete mít soubor .idl, který chcete použít v projektu přiřazené k atl. V takovém případě byste [použili atribut importidl,](importidl.md) zkompilovali soubor .idl do souboru H (viz [stránky vlastností MIDL](../../build/reference/midl-property-pages.md) v dialogovém okně **Stránky vlastností** projektu) a potom do projektu zahrnuli soubor H.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>Lze upravit kód, který je vložen atributem?

Některé atributy vloží kód do projektu. Můžete zobrazit vložený kód pomocí možnosti kompilátoru [/Fx.](../../build/reference/fx-merge-injected-code.md) Je také možné zkopírovat kód z vloženého souboru a vložit jej do zdrojového kódu. To umožňuje změnit chování atributu. Však bude pravděpodobně nutné upravit další části kódu také.

Následující ukázka je výsledkem kopírování vloženého kódu do souboru zdrojového kódu:

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>Jak mohu předat deklarovat přidělené rozhraní?

Pokud se chystáte provést dopřednou deklaraci přidělené rozhraní, musíte použít stejné atributy forward prohlášení, které platí pro deklaraci skutečné rozhraní. Je také nutné použít atribut [exportu](export.md) dopředné deklarace.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>Lze použít atributy na třídu odvozené z třídy, která také používá atributy?

Ne, použití atributů ve třídě odvozené z třídy, která také používá atributy, není podporováno.

## <a name="see-also"></a>Viz také

[Atributy C++ pro COM a .NET](cpp-attributes-com-net.md)
