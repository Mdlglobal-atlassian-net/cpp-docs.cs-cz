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
ms.openlocfilehash: e494285f33cf282d7b7515aac374ec86ef3036b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372493"
---
# <a name="comptr-class"></a>com::ptr – třída

Obálka pro objekt COM, který lze použít jako člen třídy CLR.  Obálka také automatizuje správu životnosti objektu COM a uvolňuje všechny vlastněné odkazy na objekt, když je volána jeho destruktor. Analogické s [třídou CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parametry

*_interface_type*<br/>
rozhraní COM.

## <a name="remarks"></a>Poznámky

A `com::ptr` lze také použít jako proměnnou místní funkce pro zjednodušení různých úloh COM a automatizaci správy životnosti.

A `com::ptr` nelze použít přímo jako parametr funkce; místo toho použijte [operátor sledování odkazu](../extensions/tracking-reference-operator-cpp-component-extensions.md) nebo [popisovač k objektu operátoru (^).](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

A `com::ptr` nelze vrátit přímo z funkce; místo toho použijte popisovač.

## <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena.  Volání veřejné metody třídy má za následek `IXMLDOMDocument` volání obsažený objekt.  Ukázka vytvoří instanci dokumentu XML, vyplní jej jednoduchým XML a provede zjednodušenou chůzi uzlů ve stromu analyzovaného dokumentu, aby se xml vytiskl do konzoly.

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

### <a name="public-constructors"></a>Veřejní konstruktéři

|Name (Název)|Popis|
|---------|-----------|
|[ptr::ptr](#ptr)|Konstrukce `com::ptr` zalomit objekt COM.|
|[ptr::~ptr](#tilde-ptr)|Zničí `com::ptr`.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|---------|-----------|
|[ptr::Attach](#attach)|Připojí objekt COM k `com::ptr`.|
|[ptr::CreateInstance](#createInstance)|Vytvoří instanci objektu `com::ptr`COM v rámci .|
|[ptr::Detach](#detach)|Vydá vlastnictví objektu COM a vrátí mu ukazatel.|
|[ptr::GetInterface](#getInterface)|Vytvoří instanci objektu `com::ptr`COM v rámci .|
|[ptr::QueryInterface](#queryInterface)|Dotazuje vlastněný objekt COM pro rozhraní a `com::ptr`připojí výsledek k jinému .|
|[ptr::Release](#release)|Uvolní všechny vlastněné odkazy na objekt COM.|

### <a name="public-operators"></a>Veřejní provozovatelé

|Name (Název)|Popis|
|---------|-----------|
|[ptr::operátor-&gt;](#operator-arrow)|Operátor přístupu člena, který se používá k volání metod na vlastněný objekt COM.|
|[ptr::operátor=](#operator-assign)|Připojí objekt COM k `com::ptr`.|
|[ptr::operátor&nbsp;bool](#operator-bool)|Operátor pro `com::ptr` použití v podmíněném výrazu.|
|[ptr::operator!](#operator-logical-not)|Operátor k určení, zda je vlastněný objekt COM neplatný.|

## <a name="requirements"></a>Požadavky

**Soubor** \<záhlaví msclr\com\ptr.h>

**Obor názvů** msclr::com

## <a name="ptrptr"></a><a name="ptr"></a>ptr::ptr

Vrátí ukazatel na vlastněný objekt COM.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel rozhraní COM.

### <a name="remarks"></a>Poznámky

Konstruktor bez argumentů `nullptr` přiřadí popisovač základního objektu. Budoucí volání `com::ptr` bude ověřovat vnitřní objekt a tiše nezdaří, dokud je objekt vytvořen nebo připojen.

Konstruktor jednoho argumentu přidá odkaz na objekt COM, ale neuvolní odkaz volajícího, `Release` takže volající musí volat na objekt COM, aby se skutečně vzdal řízení. Při `com::ptr`volání 's destruktor automaticky uvolní své odkazy na objekt COM.

Předání `NULL` tomuto konstruktoru je stejné jako volání verze bez argumentů.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Ukazuje použití obou verzí konstruktoru.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>ptr::~ptr

Zničí `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Poznámky

Při zničení `com::ptr` uvolní všechny odkazy, které vlastní na jeho objekt COM. Za předpokladu, že neexistují žádné další odkazy na objekt COM, objekt COM bude odstraněn a jeho paměť uvolněna.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena.  Ve `main` funkci budou `XmlDocument` volány destruktory dvou objektů, když přejdou z `try` oboru bloku, což `com::ptr` způsobí, že je volán základní destruktor, který uvolní všechny vlastněné odkazy na objekt COM.

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

## <a name="ptrattach"></a><a name="attach"></a>ptr::Připojit

Připojí objekt COM k `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Ukazatel rozhraní COM připojit.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt `Attach` COM, <xref:System.InvalidOperationException>vyvolá .

### <a name="remarks"></a>Poznámky

Volání odkazuje `Attach` na objekt COM, ale neuvolní odkaz volajícího na něj.

Předání `NULL` `Attach` výsledkům v žádné akci.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Členská `ReplaceDocument` funkce `Release` nejprve zavolá na všechny `Attach` dříve vlastněné objekty a potom volá připojit nový objekt dokumentu.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>ptr::Vytvořitinstance

Vytvoří instanci objektu `com::ptr`COM v rámci .

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
Řetězec. `ProgID`

*pouter*<br/>
Ukazatel na rozhraní IUnknown agregovaného objektu (řídící rozhraní IUnknown). Pokud `pouter` není zadán, `NULL` se používá.

*cls_context*<br/>
Kontext, ve kterém bude spuštěn kód, který spravuje nově vytvořený objekt. Hodnoty jsou převzaty `CLSCTX` z výčtu. Pokud `cls_context` není zadán, použije se hodnota, CLSCTX_ALL.

*rclsid (rclsid)*<br/>
`CLSID`spojené s daty a kódem, který bude použit k vytvoření objektu.

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt `CreateInstance` COM, <xref:System.InvalidOperationException>vyvolá .

Tato funkce `CoCreateInstance` volá <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> a používá `HRESULT` k převodu jakékoli chyby na příslušnou výjimku.

### <a name="remarks"></a>Poznámky

`CreateInstance`používá `CoCreateInstance` k vytvoření nové instance zadaného objektu, identifikované buď z Identifikátor UGID nebo CLSID. Odkazuje `com::ptr` na nově vytvořený objekt a automaticky uvolní všechny vlastněné odkazy při zničení.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Konstruktory třídy používají dvě `CreateInstance` různé formy k vytvoření objektu dokumentu buď z ProgID nebo z IDENTIFIKÁTORU CLSID plus CLSCTX.

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

## <a name="ptrdetach"></a><a name="detach"></a>ptr::Detach

Vydá vlastnictví objektu COM a vrátí mu ukazatel.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt COM.

Pokud není vlastněn žádný objekt, je vrácena hodnota NULL.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána na vlastněný objekt `HRESULT` COM a všechny <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>chyby je převeden na výjimku .

### <a name="remarks"></a>Poznámky

`Detach`Nejprve přidá odkaz na objekt COM jménem volajícího a potom `com::ptr`uvolní všechny odkazy vlastněné .  Volající musí nakonec uvolnit vrácený objekt zničit.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena.  Členská `DetachDocument` funkce `Detach` volá vzdát vlastnictví objektu COM a vrátit ukazatel volajícího.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>ptr::Rozhraní Get

Vrátí ukazatel na vlastněný objekt COM.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vlastněný objekt COM.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána na vlastněný objekt `HRESULT` COM a všechny <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>chyby je převeden na výjimku .

### <a name="remarks"></a>Poznámky

Přidá `com::ptr` odkaz na objekt COM jménem volajícího a také udržuje svůj vlastní odkaz na objekt COM. Volající musí nakonec uvolnit odkaz na vrácený objekt nebo nikdy nebude zničen.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Členská `GetDocument` funkce `GetInterface` používá k vrácení ukazatele na objekt COM.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>ptr::QueryInterface

Dotazuje vlastněný objekt COM pro rozhraní a `com::ptr`připojí výsledek k jinému .

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Který `com::ptr` získá rozhraní.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána na vlastněný objekt `HRESULT` COM a všechny <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>chyby je převeden na výjimku .

### <a name="remarks"></a>Poznámky

Tato metoda slouží k vytvoření obálky com pro jiné rozhraní objektu COM vlastněného aktuální obálkou. Tato metoda `QueryInterface` volá prostřednictvím vlastněného objektu COM požádat o ukazatel na určité rozhraní objektu `com::ptr`COM a připojí vrácený ukazatel rozhraní k předané .

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Členská `WriteTopLevelNode` funkce `QueryInterface` používá k `com::ptr` vyplnění `IXMLDOMNode` místní s `com::ptr` a pak předá (sledování masívní ho do soukromé členské funkce, která zapíše název uzlu a vlastnosti textu do konzoly.

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

## <a name="ptrrelease"></a><a name="release"></a>ptr::Uvolnění

Uvolní všechny vlastněné odkazy na objekt COM.

```cpp
void Release();
```

### <a name="remarks"></a>Poznámky

Volání této funkce uvolní všechny vlastněné odkazy na objekt COM a `nullptr`nastaví vnitřní popisovač na objekt COM na .  Pokud neexistují žádné další odkazy na objekt COM, budou zničeny.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena.  Členská `ReplaceDocument` funkce `Release` používá k uvolnění jakéhokoli předchozího objektu dokumentu před připojením nového dokumentu.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>ptr::operátor-&gt;

Operátor přístupu člena, který se používá k volání metod na vlastněný objekt COM.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Návratová hodnota

A `smart_com_ptr` objektu COM.

### <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volána na vlastněný objekt `HRESULT` COM a všechny <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>chyby je převeden na výjimku .

### <a name="remarks"></a>Poznámky

Tento operátor umožňuje volat metody vlastněného objektu COM. Vrátí dočasné, `smart_com_ptr` které automaticky zpracovává `AddRef` `Release`jeho vlastní a .

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Funkce `WriteDocument` používá `operator->` k `get_firstChild` volání člena objektu dokumentu.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>ptr::operátor=

Připojí objekt COM k `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Ukazatel rozhraní COM připojit.

### <a name="return-value"></a>Návratová hodnota

Odkaz na sledování `com::ptr`na .

### <a name="exceptions"></a>Výjimky

Pokud `com::ptr` již vlastní odkaz na objekt `operator=` COM, <xref:System.InvalidOperationException>vyvolá .

### <a name="remarks"></a>Poznámky

Přiřazení objektu COM `com::ptr` k odkazu na objekt COM, ale neuvolní odkaz volajícího na něj.

Tento operátor má stejný `Attach`účinek jako .

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena.  Členská `ReplaceDocument` funkce `Release` nejprve zavolá na všechny `operator=` dříve vlastněné objekty a potom použije k připojení nového objektu dokumentu.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>ptr::operátor bool

Operátor pro `com::ptr` použití v podmíněném výrazu.

```cpp
operator bool();
```

### <a name="return-value"></a>Návratová hodnota

`true`pokud je vlastněný objekt COM platný; `false` v opačném případě.

### <a name="remarks"></a>Poznámky

Vlastněný objekt COM je platný, `nullptr`pokud není .

Tento operátor převede na `_detail_class::_safe_bool` `bool` který je bezpečnější než proto, že nelze převést na integrální typ.

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena. Členská `CreateInstance` funkce `operator bool` používá po vytvoření nového objektu dokumentu k určení, zda je platný, a zapíše do konzoly, pokud je.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>ptr::operátor!

Operátor k určení, zda je vlastněný objekt COM neplatný.

```cpp
bool operator!();
```

### <a name="return-value"></a>Návratová hodnota

`true`pokud je vlastněný objekt COM neplatný. `false` v opačném případě.

### <a name="remarks"></a>Poznámky

Vlastněný objekt COM je platný, `nullptr`pokud není .

### <a name="example"></a>Příklad

Tento příklad implementuje clr `com::ptr` třídy, která `IXMLDOMDocument` používá k obtékání jeho objekt usoukromého člena.  Členská `CreateInstance` funkce `operator!` používá k určení, zda je objekt dokumentu již vlastněn, a vytvoří novou instanci pouze v případě, že je objekt neplatný.

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
