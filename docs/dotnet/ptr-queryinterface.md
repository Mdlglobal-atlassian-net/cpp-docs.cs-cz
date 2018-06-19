---
title: PTR::QueryInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.QueryInterface
- ptr::QueryInterface
- msclr::com::ptr::QueryInterface
- msclr.com.ptr.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: c2619517-3fde-493b-b12d-da8f62d5d803
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd25661fc14cb9539d4b8e68f42c29895ce0d70e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160963"
---
# <a name="ptrqueryinterface"></a>ptr::QueryInterface
Dotazuje vlastní objekt COM pro rozhraní a připojí výsledek do jiného `com::ptr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class _other_type>  
void QueryInterface(  
   ptr<_other_type> % other  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 `com::ptr` , Získají rozhraní.  
  
## <a name="exceptions"></a>Výjimky  
 Interně `QueryInterface` se volá na vlastní objekt COM a všechny chyby `HRESULT` jsou převedeny na výjimky podle <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k vytvoření obálky COM pro jiné rozhraní objektu COM vlastníkem aktuální obálku. Tato metoda volá `QueryInterface` prostřednictvím vlastní objekt COM požádat o ukazatel na určité rozhraní COM objektu a připojí ukazatel vrácený rozhraní k předané `com::ptr`.  
  
## <a name="example"></a>Příklad  
 Tento příklad implementuje CLR třídu, která využívá `com::ptr` zabalit jeho privátního člena `IXMLDOMDocument` objektu. `WriteTopLevelNode` – Členská funkce používá `QueryInterface` k vyplnění místní `com::ptr` s `IXMLDOMNode` a pak předá `com::ptr` (podle sledovací odkaz) privátního člena funkce, která zapisuje vlastnosti uzlu název a text do konzoly.  
  
```  
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
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Viz také  
 [PTR – členové](../dotnet/ptr-members.md)   
 [ptr::GetInterface](../dotnet/ptr-getinterface.md)