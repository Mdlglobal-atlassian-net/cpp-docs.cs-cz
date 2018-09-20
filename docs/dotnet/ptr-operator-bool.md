---
title: PTR::Operator bool | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::operator bool
- ptr.operator bool
- operator bool
- msclr::com::ptr::operator bool
- msclr.com.ptr.operator bool
dev_langs:
- C++
helpviewer_keywords:
- ptr::operator bool
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d9536b6260df68d07390707efcef90117e8538c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386929"
---
# <a name="ptroperator-bool"></a>ptr::operator bool

Operátor pro používání `com::ptr` v podmíněných výrazech.

## <a name="syntax"></a>Syntaxe

```
operator bool();
```

## <a name="return-value"></a>Návratová hodnota

`true` Pokud je platná; vlastní objekt modelu COM `false` jinak.

## <a name="remarks"></a>Poznámky

Vlastní objekt modelu COM je platný, pokud není `nullptr`.

Tento operátor převede ve skutečnosti na `_detail_class::_safe_bool` což je bezpečnější než `bool` vzhledem k tomu, že jej nelze převést na celočíselný typ.

## <a name="example"></a>Příklad

V tomto příkladu implementuje třídu CLR, která se používá `com::ptr` zabalit její privátní člen `IXMLDOMDocument` objektu. `CreateInstance` Členská funkce používá `operator bool` po vytvoření nového objektu dokumentu k určení, zda je platný a zapisuje do konzoly, pokud se jedná.

```
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

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Viz také

[ptr – členy](../dotnet/ptr-members.md)<br/>
[ptr::operator!](../dotnet/ptr-operator-logical-not.md)