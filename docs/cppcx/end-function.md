---
title: ukončení funkce | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::end
dev_langs:
- C++
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 771d7e83024f9c258df1437ff902d638bffc8478
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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