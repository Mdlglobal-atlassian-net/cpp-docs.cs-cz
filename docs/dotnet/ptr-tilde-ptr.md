---
title: 'PTR:: ~ ptr | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr.com.ptr.~ptr
- ptr.~ptr
- msclr::com.ptr::~ptr
- ~ptr
- ptr::~ptr
dev_langs:
- C++
helpviewer_keywords:
- ptr::~ptr
ms.assetid: 5f644aa5-fe66-4992-a5f8-13ec1292c949
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e3457bb4bda5e08de676488d6100795b5c04b61a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399571"
---
# <a name="ptrptr"></a>ptr::~ptr

Destructs `com::ptr`.

## <a name="syntax"></a>Syntaxe

```
~ptr();
```

## <a name="remarks"></a>Poznámky

Při zlikvidování `com::ptr` uvolní všechny odkazy na vlastní k jeho objekt modelu COM. Za předpokladu, že neexistují žádné další odkazy, které jsou uložené na objekt modelu COM, odstraní objekt modelu COM a jeho paměť uvolněna.

## <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  V `main` funkce, dva `XmlDocument` destruktory objektů bude volána při mizení z rozsahu `try` blok, což vede k podkladovým `com::ptr` destruktoru je volána, uvolnění všechny vlastněné odkazy modelu COM objekt.

```
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

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Viz také

[ptr – členy](../dotnet/ptr-members.md)<br/>
[ptr::ptr](../dotnet/ptr-ptr.md)<br/>
[ptr::CreateInstance](../dotnet/ptr-createinstance.md)