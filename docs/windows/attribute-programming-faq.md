---
title: "Atribut nejčastější dotazy k programování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributed programming
- attributes [C++], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c61ced7e0931f1dba46a7a6b760755f799d29b6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="attribute-programming-faq"></a>Nejčastější dotazy k programování s atributy
Toto téma poskytuje odpovědi na následující nejčastější dotazy:  
  
-   [Co je HRESULT?](#vcconattributeprogrammmingfaqanchor1)  
  
-   [Když je nutné zadat název parametru pro atribut?](#vcconattributeprogrammmingfaqanchor2)  
  
-   [Můžete použít komentáře v bloku atribut?](#vcconattributeprogrammmingfaqanchor3)  
  
-   [Jak atributy komunikovat s dědičnosti?](#vcconattributeprogrammmingfaqanchor4)  
  
-   [Jak můžete použít atributy v neoznačené atributy projektu knihovny ATL?](#vcconattributeprogrammmingfaqanchor5)  
  
-   [Jak můžete použít soubor .idl v projektu s atributy?](#vcconattributeprogrammmingfaqanchor6)  
  
-   [Můžete upravit kód, který je vloženy atribut?](#vcconattributeprogrammmingfaqanchor7)  
  
-   [Jak můžu dál deklarovat s atributy rozhraní?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)  
  
-   [Můžete použít atributy na třídy odvozené od třídy, který také používá atributy?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)  
  
##  <a name="vcconattributeprogrammmingfaqanchor1"></a>Co je HRESULT?  
 `HRESULT` Je jednoduchý datový typ, který se často používá jako typ návratové hodnoty atributů a ATL obecně. Následující tabulka popisuje různé hodnoty. Další hodnoty jsou obsažené v winerror.h soubor hlavičky.  
  
|Název|Popis|Hodnota|  
|----------|-----------------|-----------|  
|S_OK|Operace byla úspěšná.|0x00000000|  
|E_UNEXPECTED|Neočekávané selhání|0x8000FFFF|  
|E_NOTIMPL|Není implementováno|0x80004001|  
|E_OUTOFMEMORY|Přidělení paměti se nezdařilo|0x8007000E|  
|E_INVALIDARG|Některé argumenty nejsou platné|0x80070057|  
|E_NOINTERFACE|Neznámé rozhraní|0x80004002|  
|E_POINTER|Neplatný ukazatel|0x80004003|  
|E_HANDLE|Neplatný popisovač|0x80070006|  
|E_ABORT|Operace byla přerušena|0x80004004|  
|E_FAIL|Nespecifikovaná chyba|0x80004005|  
|E_ACCESSDENIED|Obecná chyba odepření přístupu|0x80070005|  
  
##  <a name="vcconattributeprogrammmingfaqanchor2"></a>Když je nutné zadat název parametru pro atribut?  
 Ve většině případů je atribut má jeden parametr-li název tohoto parametru. Tento název se nevyžaduje při vkládání atribut v kódu. Například následující využití [agregovatelné](../windows/aggregatable.md) atribut:  
  
```  
[coclass, aggregatable(value=allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 je přesně stejný jako:  
  
```  
[coclass, aggregatable(allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 Následující atributy se ale mít jednu, nepojmenované parametry:  
  
||||  
|-|-|-|  
|[call_as –](../windows/call-as.md)|[případ](../windows/case-cpp.md)|[cpp_quote –](../windows/cpp-quote.md)|  
|[Výchozí](../windows/default-cpp.md)|[Výchozí hodnota](../windows/defaultvalue.md)|[defaultvtable –](../windows/defaultvtable.md)|  
|[emitidl –](../windows/emitidl.md)|[Položka](../windows/entry.md)|[first_is –](../windows/first-is.md)|  
|[HelpContext –](../windows/helpcontext.md)|[soubor nápovědy](../windows/helpfile.md)|[helpstring –](../windows/helpstring.md)|  
|[helpstringcontext –](../windows/helpstringcontext.md)|[helpstringdll –](../windows/helpstringdll.md)|[ID](../windows/id.md)|  
|[iid_is –](../windows/iid-is.md)|[Import](../windows/import.md)|[importlib –](../windows/importlib.md)|  
|[Zahrnout](../windows/include-cpp.md)|[includelib –](../windows/includelib-cpp.md)|[last_is –](../windows/last-is.md)|  
|[length_is –](../windows/length-is.md)|[max_is –](../windows/max-is.md)|[no_injected_text –](../windows/no-injected-text.md)|  
|[pointer_default –](../windows/pointer-default.md)|[Direktiva pragma](../windows/pragma.md)|[omezený](../windows/restricted.md)|  
|[size_is –](../windows/size-is.md)|[zdroj](../windows/source-cpp.md)|[switch_is –](../windows/switch-is.md)|  
|[switch_type –](../windows/switch-type.md)|[transmit_as –](../windows/transmit-as.md)|[wire_marshal –](../windows/wire-marshal.md)|  
  
##  <a name="vcconattributeprogrammmingfaqanchor3"></a>Můžete použít komentáře v bloku atribut?  
 Můžete použít jeden řádek a více řádků komentáře v rámci bloku atribut. Nelze však použít buď Styl komentáře v závorkách, která uchovává parametry do atribut.  
  
 Je povoleno následující:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1"), /* Multiple-line  
                                       comment */  
   threading("both") // Single-line comment  
]  
```  
  
 Nepovolené následující:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1" /* Multiple-line comment */ ),  
   threading("both" // Single-line comment)  
]  
```  
  
##  <a name="vcconattributeprogrammmingfaqanchor4"></a>Jak atributy komunikovat s dědičnosti?  
 S atributy i bez atributů třídy lze dědit z jiné třídy, které mohou sami přičítají nebo ne. Výsledek odvozování z s atributy třídy je stejný jako odvozování z třídy po zprostředkovatele atribut má transformaci jeho kód. Atributy nejsou přenášeny do odvozené třídy prostřednictvím dědičnosti jazyka C++. Poskytovatele atribut pouze transformuje kódu v blízkosti jeho atributy.  
  
##  <a name="vcconattributeprogrammmingfaqanchor5"></a>Jak můžete použít atributy v neoznačené atributy projektu knihovny ATL?  
 Můžete mít neoznačené atributy ATL projektu, který má souboru IDL, a chcete začít přidávat objekty s atributy. V takovém případě použijte Průvodce přidáním jak poskytnout kódu.  
  
##  <a name="vcconattributeprogrammmingfaqanchor6"></a>Jak můžete použít soubor .idl v projektu s atributy?  
 Můžete mít .idl souboru, který chcete použít v projektu knihovny ATL s atributy. V takovém případě byste použili [importidl –](../windows/importidl.md) atribut, kompilovat .idl soubor do souboru .h (najdete v článku [MIDL – stránky vlastností](../ide/midl-property-pages.md) v dialogovém okně stránky vlastností projektu) a pak zahrnout soubor hlaviček v projektu .  
  
##  <a name="vcconattributeprogrammmingfaqanchor7"></a>Můžete upravit kód, který je vloženy atribut?  
 Některé atributy vložení kódu do vašeho projektu. Vložený kód můžete zobrazit pomocí [/Fx](../build/reference/fx-merge-injected-code.md) – možnost kompilátoru. Také je možné zkopírovat kód z vloženého souboru a vložte jej do vašeho zdrojového kódu. To umožňuje upravovat chování atribut. Ale budete muset upravit dalších částí kódu také.  
  
 Následující příklad je výsledkem kopírování vložený kód do souboru zdrojového kódu:  
  
```  
// attr_injected.cpp  
// compile with: comsupp.lib  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[ module(name="MyLibrary") ];  
  
// ITestTest  
[   
   object,  
   uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"),  
   dual,  
   helpstring("ITestTest Interface"),  
   pointer_default(unique)  
]  
  
__interface ITestTest : IDispatch {  
   [id(1), helpstring("method DoTest")]   
   HRESULT DoTest([in] BSTR str);  
};  
  
// _ITestTestEvents  
[  
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"),  
   dispinterface,  
   helpstring("_ITestTestEvents Interface")  
]  
  
__interface _ITestTestEvents {  
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);  
};  
  
// CTestTest  
[  
   coclass,  
   threading(apartment),  
   vi_progid("TestATL1.TestTest"),  
   progid("TestATL1.TestTest.1"),  
   version(1.0),  
   uuid("D9632007-14FA-4679-9E1C-28C9A949E784"),  
   // this line would be commented out from original file  
   // event_source("com"),  
   // this line would be added to support injected code  
   source(_ITestTestEvents),  
   helpstring("TestTest Class")  
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
  
##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>Jak můžu dál deklarovat s atributy rozhraní?  
 Pokud chcete předat dál prohlášení rozhraní s atributy, je nutné použít stejné atributy pro dopředného deklarace, které se vztahují k deklaraci skutečné rozhraní. Musíte také použít [exportovat](../windows/export.md) atribut Dopředná deklarace.  
  
##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>Můžete použít atributy na třídy odvozené od třídy, který také používá atributy?  
 Ne, není podporován pomocí atributů na třídy odvozené od třídy, který také používá atributy.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../windows/attributed-programming-concepts.md)