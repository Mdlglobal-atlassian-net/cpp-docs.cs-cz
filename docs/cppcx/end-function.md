---
title: ukončení funkce | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::end
dev_langs:
- C++
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
caps.latest.revision: 4
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 264ffdad3d55ae9d2df44646240d42ac02d5fcb1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="end-function"></a>end – funkce
Vrátí iterátor, který ukazuje přesahuje za konec kolekce, která přistupuje parametr specifikované rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template <typename T>  
    ::Platform::Collections::VectorIterator<T>   
    end(  
        IVector<T>^ v       );  
  
template <typename T>  
    ::Platform::Collections::VectorViewIterator<T>   
    end(  
        IVectorView<T>^ v  
       );  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    end(  
        IIterable<T>^ i  
       );  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru šablony.  
  
 `v`  
 Kolekce vektoru\<T > nebo VectorView\<T > objekty, které přistupují IVector\<T >, nebo IVectorView\<T > rozhraní.  
  
 `i`  
 Kolekce arbitraty prostředí Windows Runtime objekty, které přistupují IIterable\<T > rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator, který odkazuje přesahuje za konec kolekce.  
  
### <a name="remarks"></a>Poznámky  
 První dvě šablony funkce vrátí iterátory a vrátí vstupní iterator třetí funkce šablony.  
  
 [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) objekt, který je vrácen `end` je iterator proxy, která ukládá elementy typu `VectorProxy<T>`. Objekt proxy serveru je však téměř žádné viditelné pro uživatelského kódu. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Viz také  
 [Namespace Windows::Foundation::Collections](../cppcx/windows-foundation-collections-namespace-c-cx.md)