---
title: PTR::CreateInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd4ba56b92150046b986f2b101f6a004c114bf28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance
Vytvoří instanci objektu COM v rámci `com::ptr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `progid`  
 A `ProgID` řetězec.  
  
 `pouter`  
 Ukazatel na agregovaný objekt IUnknown – rozhraní (řízení IUnknown). Pokud `pouter` není zadán, `NULL` se používá.  
  
 `cls_context`  
 Kontext, ve kterém se spustí kód, který spravuje nově vytvořený objekt. Hodnoty jsou převzaty z `CLSCTX` výčtu. Pokud `cls_context` není zadán, hodnota CLSCTX_ALL se používá.  
  
 `rclsid`  
 `CLSID` související s daty a kód, který se použije k vytvoření objektu.  
  
## <a name="exceptions"></a>Výjimky  
 Pokud `com::ptr` již vlastní odkaz na objekt COM `CreateInstance` vyvolá <xref:System.InvalidOperationException>.  
  
 Tato funkce volá `CoCreateInstance` a používá <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> převést chyby `HRESULT` k příslušné výjimky.  
  
## <a name="remarks"></a>Poznámky  
 `CreateInstance` používá `CoCreateInstance` vytvořit novou instanci objektu zadaného identifikovat buď z ProgID nebo identifikátor CLSID. `com::ptr` Odkazuje na nově vytvořený objekt a bude automaticky uvolnit všechny vlastní odkazy při odstraňování.  
  
## <a name="example"></a>Příklad  
 Tento příklad implementuje CLR třídu, která využívá `com::ptr` zabalit jeho privátního člena `IXMLDOMDocument` objektu. Třída konstruktory použít dvě různé formy `CreateInstance` vytvořit objekt dokumentu z ProgID nebo z identifikátor CLSID plus CLSCTX.  
  
```  
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
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Viz také  
 [ptr – členy](../dotnet/ptr-members.md)