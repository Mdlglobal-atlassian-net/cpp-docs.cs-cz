---
title: "Začněte funkce | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::begin
dev_langs: C++
helpviewer_keywords: begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d47244e6428979f5319c9ee02f252ef3e559f7ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="begin-function"></a>begin – funkce
Vrátí iterátor, který odkazuje na začátek kolekce, které je přístupné parametrem specifikované rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru šablony.  
  
 `v`  
 Kolekce vektoru\<T > nebo VectorView\<T > objekty, které přistupují IVector\<T > nebo IVectorView\<T > rozhraní.  
  
 `i`  
 Kolekce objektů libovolný prostředí Windows Runtime, které přistupují IIterable\<T > rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator, která odkazuje na začátek kolekce.  
  
### <a name="remarks"></a>Poznámky  
 První dvě šablony funkce vrátí iterátory a vrátí vstupní iterator třetí funkce šablony.  
  
 VectorIterator začít objekt, který je vrácen je iterator proxy, která ukládá elementy typu VectorProxy\<T >. Objekt proxy serveru je však téměř žádné viditelné pro uživatelského kódu. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Viz také  
 [Namespace Windows::Foundation::Collections](../cppcx/windows-foundation-collections-namespace-c-cx.md)