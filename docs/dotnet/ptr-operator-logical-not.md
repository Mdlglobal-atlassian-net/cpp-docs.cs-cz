---
title: ptr::operator! | Dokumenty Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::operator!
- msclr::com::ptr::operator!
- ptr.operator!
- msclr.com.ptr.operator!
dev_langs:
- C++
helpviewer_keywords:
- ptr::operator!
ms.assetid: 7f4101dc-2045-42e7-abb1-6a30e17147f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 186fe4bbeb86780cde586500380a7e2c500da38e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443503"
---
# <a name="ptroperator"></a>ptr::operator!

Operátor zjistit, zda vlastní objekt modelu COM je neplatná.

## <a name="syntax"></a>Syntaxe

```
bool operator!();
```

## <a name="return-value"></a>Návratová hodnota

`true` Pokud je neplatný; vlastní objekt modelu COM `false` jinak.

## <a name="remarks"></a>Poznámky

Vlastní objekt modelu COM je platný, pokud není `nullptr`.

## <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu.  `CreateInstance` Členská funkce používá `operator!` k určení, zda již vlastní objekt dokumentu a pouze vytvoří novou instanci, pokud objekt je neplatný.

```
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

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Viz také

[ptr – členy](../dotnet/ptr-members.md)<br/>
[ptr::operator bool](../dotnet/ptr-operator-bool.md)