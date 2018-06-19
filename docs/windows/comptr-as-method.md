---
title: Comptr::AS – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb9fd0ff09f6775a95ff881d9f8cbaa3edc61065
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857269"
---
# <a name="comptras-method"></a>ComPtr::As – metoda
Vrátí objekt ComPtr, který představuje rozhraní identifikovaný parametr určené šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Rozhraní, které má být reprezentován parametrem `p`.  
  
 `p`  
 ComPtr objekt, který reprezentuje rozhraní určený parametrem `U`. Parametr `p` nesmí odkazovat na aktuální objekt ComPtr.  
  
## <a name="remarks"></a>Poznámky  
 První šablona je formulář, který by měli používat v kódu. Druhá šablona je interní, specializace pomocné rutiny, která podporuje funkcí jazyka C++, jako [automaticky](../cpp/auto-cpp.md) zadejte odvození – klíčové slovo.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)