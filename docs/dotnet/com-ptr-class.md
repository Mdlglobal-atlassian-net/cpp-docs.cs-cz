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
ms.openlocfilehash: 342c222b837e179e2e13dbbd27c88efc18b12332
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774167"
---
# <a name="comptr-class"></a>com::ptr – třída

Obálka pro objekt modelu COM, který může sloužit jako člen třídy CLR.  Obálka kanál také automatizuje správu životního cyklu objektu COM, uvolňuje všechny vlastněné odkazů na objekt, když jeho destruktoru je volána. Obdobná [CComPtr – třída](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parametry

*_interface_type*<br/>
Rozhraní COM.

## <a name="remarks"></a>Poznámky

A `com::ptr` lze také jako funkce místní proměnnou ke zjednodušení různé úlohy COM a automatizují správu životního cyklu.

A `com::ptr` nelze použít přímo jako parametr funkce; použijte [operátor odkazu sledování](../extensions/tracking-reference-operator-cpp-component-extensions.md) nebo [operátor popisovače objektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) místo.

A `com::ptr` nemůže být vráceny přímo z funkce; místo toho použijte popisovač.

## <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  Volání veřejné metody tříd výsledky ve volání do uzavřeného `IXMLDOMDocument` objektu.  Ukázka vytvoří instanci dokumentu XML, vyplní některé jednoduché XML a nemá zjednodušené procházení uzlů ve stromu analyzovaný dokumentu a vytisknout XML do konzoly.

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

|Name|Popis| 
|---------|-----------| 
|[ptr::ptr](#ptr)|Vytvoří `com::ptr` zabalit objekt modelu COM.| 
|[ptr::~ptr](#tilde-ptr)|Destructs `com::ptr`.| 

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|---------|-----------| 
|[ptr::Attach](#attach)|Připojí objektu modelu COM `com::ptr`.| 
|[ptr::CreateInstance](#createInstance)|Vytvoří instanci objektu modelu COM v rámci `com::ptr`.| 
|[ptr::Detach](#detach)|Vrací vlastnictví objektu COM, vrací ukazatel na objekt.| 
|[ptr::GetInterface](#getInterface)|Vytvoří instanci objektu modelu COM v rámci `com::ptr`.| 
|[ptr::QueryInterface](#queryInterface)|Dotazuje se vlastnictví objektu modelu COM pro rozhraní a připojí výsledek do jiného `com::ptr`.| 
|[ptr::Release](#release)|Uvolní všechny vlastněné odkazy na objekt modelu COM.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|---------|-----------| 
|[PTR::Operator-&gt;](#operator-arrow)|Operátor přístupu členů použít k volání metody na vlastní objekt modelu COM.| 
|[ptr::operator=](#operator-assign)|Připojí objektu modelu COM `com::ptr`.| 
|[PTR::Operator&nbsp;bool](#operator-bool)|Operátor pro používání `com::ptr` v podmíněných výrazech.| 
|[ptr::operator!](#operator-logical-not)|Operátor zjistit, zda vlastní objekt modelu COM je neplatná.| 

## <a name="requirements"></a>Požadavky

**Header file** \<msclr\com\ptr.h>

**Namespace** msclr::com

 

## <a name="ptr"></a>ptr::ptr

Vrací ukazatel na vlastní objekt modelu COM.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatele rozhraní modelu COM.

### <a name="remarks"></a>Poznámky

Konstruktor bez argumentů přiřadí `nullptr` na podkladové popisovač objektu. Budoucí volání `com::ptr` ověření na vnitřní objekt, který se tiše skončit neúspěchem, dokud nebude objekt je vytvořen nebo připojen.

Konstruktor jednoargumentové přidá odkaz na objekt modelu COM, ale nebude release odkaz volajícího, aby volající musí zavolat `Release` u objektu COM skutečně ztratit kontrolu. Při `com::ptr`zavolán destruktor automaticky vydá jejich odkazů na objekt modelu COM.

Předání `NULL` pro tento konstruktor je stejná jako verze bez argumentů volání.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. Ukazuje použití obě verze konstruktoru.

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

## <a name="tilde-ptr"></a>PTR:: ~ ptr

Destructs `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Poznámky

Při zlikvidování `com::ptr` uvolní všechny odkazy na vlastní k jeho objekt modelu COM. Za předpokladu, že neexistují žádné další odkazy, které jsou uložené na objekt modelu COM, odstraní objekt modelu COM a jeho paměť uvolněna.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  V `main` funkce, dva `XmlDocument` destruktory objektů bude volána při mizení z rozsahu `try` blok, což vede k podkladovým `com::ptr` destruktoru je volána, uvolnění všechny vlastněné odkazy modelu COM objekt.

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

## <a name="attach"></a>ptr::Attach

Připojí objektu modelu COM `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*vp_ravo*<br/>
Ukazatele rozhraní modelu COM pro připojení.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt modelu COM `Attach` vyvolá <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Poznámky

Volání `Attach` odkazuje na objekt modelu COM, ale nemá verzi na ni odkaz volajícího.

Předání `NULL` k `Attach` výsledkem je provedena žádná akce.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. `ReplaceDocument` První volání členských funkcí `Release` na žádném dříve vlastněn objekt a poté zavolá `Attach` připojit nový objekt dokumentu.

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

## <a name="createInstance"></a>PTR::CreateInstance

Vytvoří instanci objektu modelu COM v rámci `com::ptr`.

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
A `ProgID` řetězec.

*pouter*<br/>
Ukazatel na rozhraní IUnknown agregovaný objekt (řídící rozhraní IUnknown). Pokud `pouter` není zadán, `NULL` se používá.

*cls_context*<br/>
Kontext, ve kterém se spustí kód, který spravuje nově vytvořený objekt. Hodnoty pocházejí ze `CLSCTX` výčtu. Pokud `cls_context` není zadána, hodnota se používá CLSCTX_ALL.

*rclsid*<br/>
`CLSID` související s daty a kód, který se použije k vytvoření objektu.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt modelu COM `CreateInstance` vyvolá <xref:System.InvalidOperationException>.

Tato funkce volá `CoCreateInstance` a používá <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> převést všechny chyby `HRESULT` k příslušné výjimky.

### <a name="remarks"></a>Poznámky

`CreateInstance` používá `CoCreateInstance` k vytvoření nové instance zadaného objektu určen buď z ProgID a CLSID. `com::ptr` Odkazuje na nově vytvořený objekt a automaticky uvolní všechny vlastní reference při zničení.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. Konstruktor třídy použít dva různé způsoby `CreateInstance` vytvořit objekt dokumentu z ProgID nebo z CLSID plus CLSCTX.

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

## <a name="detach"></a>ptr::Detach

Vrací vlastnictví objektu COM, vrací ukazatel na objekt.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt modelu COM.

Pokud je vlastní žádný objekt, je vrácena hodnota NULL.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volán na vlastní objekt modelu COM a všechny chyby `HRESULT` jsou převedeny na výjimky podle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

`Detach` nejprve přidá odkaz na objekt modelu COM jménem volající a uvolní všechny odkazy na vlastní `com::ptr`.  Volající musí nakonec uvolnit vráceného objektu na jeho zničení.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  `DetachDocument` Volání členských funkcí `Detach` vzdát vlastnictví objektu modelu COM a vrací ukazatel na volajícího.

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

## <a name="getInterface"></a>ptr::GetInterface

Vrací ukazatel na vlastní objekt modelu COM.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vlastní objekt modelu COM.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volán na vlastní objekt modelu COM a všechny chyby `HRESULT` jsou převedeny na výjimky podle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

`com::ptr` Přidá odkaz na objekt modelu COM jménem volajícího a také udržuje svůj vlastní odkaz na objekt modelu COM. Volající musí nakonec uvolnění odkazu na vráceného objektu nebo se nikdy zničení.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. `GetDocument` Členská funkce používá `GetInterface` se vraťte ukazatel na objekt modelu COM.

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

## <a name="queryInterface"></a>ptr::QueryInterface

Dotazuje se vlastnictví objektu modelu COM pro rozhraní a připojí výsledek do jiného `com::ptr`.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
`com::ptr` , Která získá rozhraní.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volán na vlastní objekt modelu COM a všechny chyby `HRESULT` jsou převedeny na výjimky podle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete vytvořit obálky COM pro jiné rozhraní objektu COM, který vlastní aktuální obálky. Tato metoda volá `QueryInterface` prostřednictvím vlastní objekt modelu COM požádat o ukazatel na určité rozhraní modelu COM objektu a připojí Vrácený ukazatel rozhraní k předaným `com::ptr`.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. `WriteTopLevelNode` Členská funkce používá `QueryInterface` tak, aby vyplnil místní `com::ptr` s `IXMLDOMNode` a pak předá `com::ptr` (sledováním odkaz) privátní členské funkci, která zapisuje do konzole vlastnosti name a text uzlu.

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

## <a name="release"></a>PTR::Release

Uvolní všechny vlastněné odkazy na objekt modelu COM.

```cpp
void Release();
```

### <a name="remarks"></a>Poznámky

Volání této funkce uvolní vlastnictví všech odkazů na objekt modelu COM a nastaví vnitřní popisovač objektu modelu COM `nullptr`.  Pokud neexistují žádné odkazy na objekt modelu COM, se zničil.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  `ReplaceDocument` Členská funkce používá `Release` uvolnit jakýkoli objekt předchozí dokument před připojením nový dokument.

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

## <a name="operator-arrow"></a>PTR::Operator-&gt;

Operátor přístupu členů použít k volání metody na vlastní objekt modelu COM.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Návratová hodnota

A `smart_com_ptr` objekt modelu COM.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volán na vlastní objekt modelu COM a všechny chyby `HRESULT` jsou převedeny na výjimky podle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Poznámky

Tento operátor můžete volat metody vlastní objekt modelu COM. Vrátí dočasnou `smart_com_ptr` , která automaticky zpracovává vlastní `AddRef` a `Release`.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. `WriteDocument` Funkce používá `operator->` volat `get_firstChild` člen objektu dokumentu.

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

## <a name="operator-assign"></a>PTR::Operator =

Připojí objektu modelu COM `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*vp_ravo*<br/>
Ukazatele rozhraní modelu COM pro připojení.

### <a name="return-value"></a>Návratová hodnota

Odkaz sledování na `com::ptr`.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt modelu COM `operator=` vyvolá <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Poznámky

Přiřazení objektu modelu COM `com::ptr` odkazuje na objekt modelu COM, ale nemá verzi na ni odkaz volajícího.

Tento operátor má stejný účinek jako `Attach`.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  `ReplaceDocument` První volání členských funkcí `Release` na žádném dříve vlastněn objekt a potom použije `operator=` připojit nový objekt dokumentu.

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

## <a name="operator-bool"></a> PTR::Operator bool

Operátor pro používání `com::ptr` v podmíněných výrazech.

```cpp
operator bool();
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je platná; vlastní objekt modelu COM `false` jinak.

### <a name="remarks"></a>Poznámky

Vlastní objekt modelu COM je platný, pokud není `nullptr`.

Tento operátor převede na `_detail_class::_safe_bool` což je bezpečnější než `bool` vzhledem k tomu, že jej nelze převést na celočíselný typ.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. `CreateInstance` Členská funkce používá `operator bool` po vytvoření nového objektu dokumentu k určení, zda je platný a zapisuje do konzoly, pokud se jedná.

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

## <a name="operator-logical-not"></a>PTR::Operator!

Operátor zjistit, zda vlastní objekt modelu COM je neplatná.

```cpp
bool operator!();
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud je neplatný; vlastní objekt modelu COM `false` jinak.

### <a name="remarks"></a>Poznámky

Vlastní objekt modelu COM je platný, pokud není `nullptr`.

### <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  `CreateInstance` Členská funkce používá `operator!` k určení, zda již vlastní objekt dokumentu a pouze vytvoří novou instanci, pokud objekt je neplatný.

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
