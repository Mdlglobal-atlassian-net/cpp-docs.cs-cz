---
title: "Weakref::AS – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::As
dev_langs: C++
helpviewer_keywords: As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5160cb93d6660eaf990856a58d5b9379e911125e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="weakrefas-method"></a>WeakRef::As – metoda
Nastaví zadaný parametr ukazatel ComPtr představují specifikované rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Identifikátor rozhraní.  
  
 `ptr`  
 Když tato operace dokončí, objekt, který představuje parametr `U`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
-   S_OK, pokud je tato operace úspěšná; jinak hodnota HRESULT určující z důvodu operace se nezdařila, a `ptr` je nastaven na `nullptr`.  
  
-   S_OK, pokud se tato operace úspěšná, ale aktuální objekt WeakRef už byla uvolněna. Parametr `ptr` je nastaven na `nullptr`.  
  
-   Pokud se tato operace úspěšná, ale aktuální objekt WeakRef není odvozen z parametru S_OK `U`. Parametr `ptr` je nastaven na `nullptr`.  
  
## <a name="remarks"></a>Poznámky  
 Je vygenerované chybu, pokud parametr `U` je IWeakReference nebo není odvozen od IInspectable.  
  
 První šablona je formulář, který by měli používat v kódu. Druhá šablona je interní, specializace pomocné rutiny, která podporuje funkcí jazyka C++, jako [automaticky](../cpp/auto-cpp.md) zadejte odvození – klíčové slovo.  
  
 Od verze Windows 10 SDK, tato metoda nenastaví WeakRef instance `nullptr` Pokud nebylo možné získat odkaz na slabé, proto byste neměli kontrolní součet, která kontroluje WeakRef pro `nullptr`. Místo toho zkontrolujte `ptr` pro `nullptr`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)