---
title: com::ptr – třída
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 8a3223543dfa6c1b5b45fef2780cd11b558eab84
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078967"
---
# <a name="comptr-class"></a>com::ptr – třída

Obálka pro objekt modelu COM, který lze použít jako člen třídy CLR.  Obálka také automatizuje správu životního cyklu objektu COM a uvolní všechny vlastněné odkazy na objekt při volání jeho destruktoru. Analogová ke [třídě CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parametry

*_interface_type*<br/>
Rozhraní COM.

## <a name="remarks"></a>Poznámky

`com::ptr` lze použít také jako místní proměnnou funkce pro zjednodušení různých úloh COM a automatizaci správy životního cyklu.

`com::ptr` nelze použít přímo jako parametr funkce; místo toho použijte [Operátor sledovacího odkazu](../extensions/tracking-reference-operator-cpp-component-extensions.md) nebo [popisovač na objekt (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) .

`com::ptr` nelze přímo vrátit z funkce; místo toho použijte popisovač.

## <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu.  Volání veřejných metod třídy má za následek volání objektu obsaženého `IXMLDOMDocument`.  Ukázka vytvoří instanci dokumentu XML, vyplní ji pomocí nějakého jednoduchého kódu XML a zjednodušuje procházení uzlů ve stromu analyzovaných dokumentů pro tisk XML do konzoly.

```cpp
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|---------|-----------|
|[ptr::ptr](#ptr)|Vytvoří `com::ptr` pro zabalení objektu COM.|
|[ptr::~ptr](#tilde-ptr)|Destrukturuje `com::ptr`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|---------|-----------|
|[ptr::Attach](#attach)|Připojí objekt COM k `com::ptr`.|
|[ptr::CreateInstance](#createInstance)|Vytvoří instanci objektu COM v rámci `com::ptr`.|
|[ptr::Detach](#detach)|Přidělí vlastnictví objektu COM a vrátí ukazatel na objekt.|
|[ptr::GetInterface](#getInterface)|Vytvoří instanci objektu COM v rámci `com::ptr`.|
|[ptr::QueryInterface](#queryInterface)|Zadá dotaz na vlastní objekt modelu COM pro rozhraní a připojí výsledek k jinému `com::ptr`.|
|[ptr::Release](#release)|Uvolní všechny vlastněné odkazy na objekt COM.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|---------|-----------|
|[PTR:: operator-&gt;](#operator-arrow)|Operátor přístupu ke členu, který se používá k volání metod ve vlastněných objektech COM.|
|[ptr::operator=](#operator-assign)|Připojí objekt COM k `com::ptr`.|
|[PTR:: operator&nbsp;bool](#operator-bool)|Operátor pro použití `com::ptr` v podmíněném výrazu.|
|[ptr::operator!](#operator-logical-not)|K určení, zda je vlastněný objekt COM neplatný|

## <a name="requirements"></a>Požadavky

**Hlavičkový soubor** \<msclr\com\ptr.h >

**Obor názvů** msclr –:: com

## <a name="ptrptr"></a><a name="ptr"></a>PTR::p TR

Vrátí ukazatel na vlastněný objekt COM.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parametry

*Trub*<br/>
Ukazatel rozhraní modelu COM.

### <a name="remarks"></a>Poznámky

Konstruktor bez argumentů přiřadí `nullptr` k popisovači objektu. Budoucí volání `com::ptr` ověří interní objekt a tiše selže, dokud se objekt nevytvoří nebo nepřipojí.

Konstruktor s jedním argumentem přidá odkaz na objekt modelu COM, ale neuvolní odkaz volajícího, takže volající musí volat `Release` v objektu COM, aby bylo možné skutečně poskytnout řízení. Pokud je volán destruktor `com::ptr`, automaticky uvolní odkazy na objekt modelu COM.

Předávání `NULL` k tomuto konstruktoru je stejné jako volání verze bez argumentů.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Ukazuje použití obou verzí konstruktoru.

```cpp
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrptr"></a><a name="tilde-ptr"></a>PTR:: ~ PTR

Destrukturuje `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Poznámky

Při zničení `com::ptr` uvolní všechny odkazy, které vlastní, ke svému objektu COM. Za předpokladu, že neexistují žádné další odkazy na objekt modelu COM, objekt COM bude odstraněn a jeho uvolněná paměť.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu.  Ve funkci `main` budou volány dva destruktory objektů `XmlDocument`, pokud přestanou z oboru bloku `try`, což vede k vyvolání základního destruktoru `com::ptr`, který uvolňuje všechny vlastněné odkazy na objekt modelu COM.

```cpp
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrattach"></a><a name="attach"></a>PTR:: Attach

Připojí objekt COM k `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Ukazatel rozhraní modelu COM, který se má připojit.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt modelu COM, `Attach` vyvolá <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Poznámky

Volání `Attach` odkazuje na objekt modelu COM, ale neuvolní na něj odkaz volajícího.

Předání `NULL` k `Attach` výsledky neprovádí žádnou akci.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Členská funkce `ReplaceDocument` nejprve volá `Release` na všechny dřív vlastněné objekty a potom volá `Attach` pro připojení nového objektu dokumentu.

```cpp
// comptr_attach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>PTR:: CreateInstance

Vytvoří instanci objektu COM v rámci `com::ptr`.

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>Parametry

*progid*<br/>
`ProgID` řetězec.

*pouter*<br/>
Ukazatel na rozhraní IUnknown agregovaného objektu (řízení IUnknown). Pokud `pouter` není zadán, použije se `NULL`.

*cls_context*<br/>
Kontext, ve kterém se spustí kód, který spravuje nově vytvořený objekt. Hodnoty jsou pořízeny z výčtu `CLSCTX`. Pokud `cls_context` není zadán, použije se hodnota CLSCTX_ALL.

*rclsid*<br/>
`CLSID` spojená s daty a kódem, který se použije k vytvoření objektu.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt modelu COM, `CreateInstance` vyvolá <xref:System.InvalidOperationException>.

Tato funkce volá `CoCreateInstance` a používá <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> k převodu všech `HRESULT` chyb na odpovídající výjimku.

### <a name="remarks"></a>Poznámky

`CreateInstance` používá `CoCreateInstance` k vytvoření nové instance zadaného objektu identifikovaného buď z identifikátoru ProgID nebo CLSID. `com::ptr` odkazuje na nově vytvořený objekt a bude automaticky vydávat všechny vlastněné odkazy po zničení.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Konstruktory třídy používají dvě různé formy `CreateInstance` k vytvoření objektu dokumentu buď z identifikátoru ProgID, nebo z identifikátoru CLSID a CLSCTX.

```cpp
// comptr_createinstance.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="ptrdetach"></a><a name="detach"></a>PTR::D etach

Přidělí vlastnictví objektu COM a vrátí ukazatel na objekt.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt modelu COM.

Pokud žádný objekt není vlastněn, je vrácena hodnota NULL.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána ve vlastněných objektech COM a všechny chyby `HRESULT` jsou převedeny na výjimku <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

`Detach` nejprve přidá odkaz na objekt COM jménem volajícího a poté uvolní všechny odkazy, které jsou vlastněny `com::ptr`.  Volající musí nakonec uvolnit vrácený objekt k jeho zničení.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu.  Členská funkce `DetachDocument` volá `Detach`, aby poskytovala vlastnictví objektu COM a vrátila ukazatel na volajícího.

```cpp
// comptr_detach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

## <a name="ptrgetinterface"></a><a name="getInterface"></a>PTR:: GetInterface

Vrátí ukazatel na vlastněný objekt COM.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vlastněný objekt COM.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána ve vlastněných objektech COM a všechny chyby `HRESULT` jsou převedeny na výjimku <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

`com::ptr` přidá odkaz na objekt modelu COM jménem volajícího a také uchovává svůj vlastní odkaz na objekt modelu COM. Volající musí nakonec uvolnit odkaz na vrácený objekt nebo nebude nikdy zničen.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Členská funkce `GetDocument` používá `GetInterface` k vrácení ukazatele na objekt modelu COM.

```cpp
// comptr_getinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>PTR:: QueryInterface

Zadá dotaz na vlastní objekt modelu COM pro rozhraní a připojí výsledek k jinému `com::ptr`.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
`com::ptr`, který získá rozhraní.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána ve vlastněných objektech COM a všechny chyby `HRESULT` jsou převedeny na výjimku <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li vytvořit obálku modelu COM pro jiné rozhraní objektu COM vlastněné aktuální obálkou. Tato metoda volá `QueryInterface` prostřednictvím vlastněné objektu COM k vyžádání ukazatele na konkrétní rozhraní objektu COM a připojí ukazatel vráceného rozhraní k předanému `com::ptr`.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Členská funkce `WriteTopLevelNode` používá `QueryInterface` k vyplnění místního `com::ptr` `IXMLDOMNode` a poté předá `com::ptr` (sledováním odkazu) do soukromé členské funkce, která zapisuje vlastnosti názvu a textu uzlu do konzoly.

```cpp
// comptr_queryinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into our document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="ptrrelease"></a><a name="release"></a>PTR:: Release

Uvolní všechny vlastněné odkazy na objekt COM.

```cpp
void Release();
```

### <a name="remarks"></a>Poznámky

Volání této funkce uvolní všechny vlastněné odkazy na objekt modelu COM a nastaví vnitřní popisovač objektu COM na `nullptr`.  Pokud neexistují žádné další odkazy na objekt COM, budou zničeny.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu.  Členská funkce `ReplaceDocument` používá `Release` k uvolnění dříve objektu dokumentu před připojením nového dokumentu.

```cpp
// comptr_release.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>PTR:: operator-&gt;

Operátor přístupu ke členu, který se používá k volání metod ve vlastněných objektech COM.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Návratová hodnota

`smart_com_ptr` objektu COM.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána ve vlastněných objektech COM a všechny chyby `HRESULT` jsou převedeny na výjimku <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

Tento operátor umožňuje volat metody vlastněné objektu COM. Vrátí dočasnou `smart_com_ptr`, která automaticky zpracuje vlastní `AddRef` a `Release`.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Funkce `WriteDocument` používá `operator->` k volání `get_firstChild` člena objektu dokumentu.

```cpp
// comptr_op_member.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="ptroperator"></a><a name="operator-assign"></a>PTR:: operator =

Připojí objekt COM k `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Ukazatel rozhraní modelu COM, který se má připojit.

### <a name="return-value"></a>Návratová hodnota

Sledovací odkaz na `com::ptr`.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt modelu COM, `operator=` vyvolá <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Poznámky

Přiřazení objektu COM k `com::ptr` odkazuje na objekt modelu COM, ale neuvolní na něj odkaz volajícího.

Tento operátor má stejný účinek jako `Attach`.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu.  Členská funkce `ReplaceDocument` nejdříve volá `Release` na všech dřív vlastněných objektech a poté používá `operator=` k připojení nového objektu dokumentu.

```cpp
// comptr_op_assign.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>PTR:: operator bool

Operátor pro použití `com::ptr` v podmíněném výrazu.

```cpp
operator bool();
```

### <a name="return-value"></a>Návratová hodnota

`true`, je-li vlastněný objekt modelu COM platný; `false` jinak.

### <a name="remarks"></a>Poznámky

Vlastněný objekt COM je platný, pokud není `nullptr`.

Tento operátor převede na `_detail_class::_safe_bool`, která je bezpečnější než `bool`, protože nemůže být převedena na celočíselný typ.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu. Členská funkce `CreateInstance` používá `operator bool` po vytvoření nového objektu dokumentu k určení, zda je platný a zapisuje do konzoly, pokud je.

```cpp
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="ptroperator"></a><a name="operator-logical-not"></a>PTR:: operator!

K určení, zda je vlastněný objekt COM neplatný

```cpp
bool operator!();
```

### <a name="return-value"></a>Návratová hodnota

`true`, je-li vlastněný objekt COM neplatný; `false` jinak.

### <a name="remarks"></a>Poznámky

Vlastněný objekt COM je platný, pokud není `nullptr`.

### <a name="example"></a>Příklad

Tento příklad implementuje třídu CLR, která používá `com::ptr` k zabalení jeho soukromého člena `IXMLDOMDocument` objektu.  Členská funkce `CreateInstance` používá `operator!` k určení, zda je objekt dokumentu již vlastněn, a vytvoří pouze novou instanci, pokud je objekt neplatný.

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```
