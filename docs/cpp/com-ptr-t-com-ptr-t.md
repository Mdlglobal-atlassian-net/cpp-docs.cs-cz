---
title: _com_ptr_t::_com_ptr_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::_com_ptr_t
dev_langs: C++
helpviewer_keywords: _com_ptr_t method [C++]
ms.assetid: 0c00620a-28d2-4f60-ae4a-1696be36137e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef1a89617e9e4c0271d491fc63994a504db3dc48
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comptrtcomptrt"></a>_com_ptr_t::_com_ptr_t
**Konkrétní Microsoft**  
  
 Vytvoří `_com_ptr_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
// Default constructor.  
// Constructs a NULL smart pointer.  
_com_ptr_t() throw();  
  
// Constructs a NULL smart pointer. The NULL argument must be zero.  
_com_ptr_t(   
   int null   
);  
  
// Constructs a smart pointer as a copy of another instance of the   
// same smart pointer. AddRef is called to increment the reference   
// count for the encapsulated interface pointer.  
_com_ptr_t(   
   const _com_ptr_t& cp   
) throw();  
  
// Move constructor (Visual Studio 2015 Update 3 and later)  
_com_ptr_t(_com_ptr_t&& cp) throw();  
  
// Constructs a smart pointer from a raw interface pointer of this   
// smart pointer's type. If fAddRef is true, AddRef is called   
// to increment the reference count for the encapsulated   
// interface pointer. If fAddRef is false, this constructor   
// takes ownership of the raw interface pointer without calling AddRef.  
_com_ptr_t(   
   Interface* pInterface,   
   bool fAddRef   
) throw();  
  
// Construct pointer for a _variant_t object.  
// Constructs a smart pointer from a _variant_t object. The   
// encapsulated VARIANT must be of type VT_DISPATCH or VT_UNKNOWN, or   
// it can be converted into one of these two types. If QueryInterface   
// fails with an E_NOINTERFACE error, a NULL smart pointer is   
// constructed.  
_com_ptr_t(   
   const _variant_t& varSrc   
);  
  
// Constructs a smart pointer given the CLSID of a coclass. This   
// function calls CoCreateInstance, by the member function  
//  CreateInstance, to create a new COM object and then queries for   
// this smart pointer's interface type. If QueryInterface fails with   
// an E_NOINTERFACE error, a NULL smart pointer is constructed.  
explicit _com_ptr_t(   
   const CLSID& clsid,    
   IUnknown* pOuter = NULL,    
   DWORD dwClsContext = CLSCTX_ALL   
);  
  
// Calls CoCreateClass with provided CLSID retrieved from string.  
explicit _com_ptr_t(   
   LPCWSTR str,    
   IUnknown* pOuter = NULL,    
   DWORD dwClsContext = CLSCTX_ALL   
);  
  
// Constructs a smart pointer given a multibyte character string that   
// holds either a CLSID (starting with "{") or a ProgID. This function   
// calls CoCreateInstance, by the member function CreateInstance, to   
// create a new COM object and then queries for this smart pointer's   
// interface type. If QueryInterface fails with an E_NOINTERFACE error,   
// a NULL smart pointer is constructed.  
explicit _com_ptr_t(   
   LPCSTR str,   
   IUnknown* pOuter = NULL,   
   DWORD dwClsContext = CLSCTX_ALL   
);  
  
// Saves the interface.  
template<>    
_com_ptr_t(   
   Interface* pInterface   
) throw();  
  
// Make sure correct ctor is called  
template<>    
_com_ptr_t(   
   LPSTR str   
);  
  
// Make sure correct ctor is called  
template<>    
_com_ptr_t(   
   LPWSTR str   
);  
  
// Constructs a smart pointer from a different smart pointer type or   
// from a different raw interface pointer. QueryInterface is called to   
// find an interface pointer of this smart pointer's type. If   
// QueryInterface fails with an E_NOINTERFACE error, a NULL smart   
// pointer is constructed.  
template<typename _OtherIID>    
_com_ptr_t(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
// Constructs a smart-pointer from any IUnknown-based interface pointer.  
template<typename _InterfaceType>   
_com_ptr_t(   
   _InterfaceType* p   
);  
  
// Disable conversion using _com_ptr_t* specialization of  
// template<typename _InterfaceType> _com_ptr_t(_InterfaceType* p)  
template<>    
explicit _com_ptr_t(   
   _com_ptr_t* p   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pInterface`  
 Nezpracovaný ukazatel rozhraní.  
  
 `fAddRef`  
 Pokud **true**, `AddRef` nazývá se zvýší počet odkazů ukazatel zapouzdřené rozhraní.  
  
 *prohlášení CP*  
 A `_com_ptr_t` objektu.  
  
 `p`  
 Nezpracovaný ukazatel rozhraní, jehož typ se liší od typu inteligentního ukazatele tohoto objektu `_com_ptr_t`.  
  
 *varSrc*  
 A `_variant_t` objektu.  
  
 `clsid`  
 **CLSID** z coclass.  
  
 `dwClsContext`  
 Kontext spuštění spustitelného kódu.  
  
 *lpcStr*  
 Více-bajtové řetězec, který obsahuje buď **CLSID** (počínaje "**{**") nebo **ProgID**.  
  
 `pOuter`  
 Vnější Neznámý pro [agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558).  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)