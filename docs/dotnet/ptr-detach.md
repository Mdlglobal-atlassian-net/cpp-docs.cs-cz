---
title: ptr::Detach
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr.Detach
- msclr.com.ptr.Detach
- ptr::Detach
- msclr::com::ptr::Detach
helpviewer_keywords:
- ptr::Detach
ms.assetid: 23370c8a-8f79-4880-9fa1-46e110c1a92c
ms.openlocfilehash: 1b8ebd44cad7853415856594b523f8d70039d371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445120"
---
# <a name="ptrdetach"></a>ptr::Detach

Vrací vlastnictví objektu COM, vrací ukazatel na objekt.

## <a name="syntax"></a>Syntaxe

```
_interface_type * Detach();
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt modelu COM.

Pokud je vlastní žádný objekt, je vrácena hodnota NULL.

## <a name="exceptions"></a>Výjimky

Interně `QueryInterface` je volán na vlastní objekt modelu COM a všechny chyby `HRESULT` jsou převedeny na výjimky podle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

## <a name="remarks"></a>Poznámky

`Detach` nejprve přidá odkaz na objekt modelu COM jménem volající a uvolní všechny odkazy na vlastní `com::ptr`.  Volající musí nakonec uvolnit vráceného objektu na jeho zničení.

## <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  `DetachDocument` Volání členských funkcí `Detach` vzdát vlastnictví objektu modelu COM a vrací ukazatel na volajícího.

```
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

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Viz také

[ptr – členy](../dotnet/ptr-members.md)<br/>
[ptr::Release](../dotnet/ptr-release.md)<br/>
[ptr::Attach](../dotnet/ptr-attach.md)