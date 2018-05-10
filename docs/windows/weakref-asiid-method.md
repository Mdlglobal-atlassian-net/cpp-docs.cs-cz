---
title: Weakref::asiid – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69108681b181d0b2fce20f9e30a009b6b93c2180
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID – metoda
Nastaví zadaný parametr ukazatel ComPtr představují ID specifikované rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identifikátor rozhraní.  
  
 `ptr`  
 Když tato operace dokončí, objekt, který představuje parametr `riid`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
-   S_OK, pokud je tato operace úspěšná; jinak hodnota HRESULT určující z důvodu operace se nezdařila, a `ptr` je nastaven na `nullptr`.  
  
-   S_OK, pokud se tato operace úspěšná, ale aktuální objekt WeakRef už byla uvolněna. Parametr `ptr` je nastaven na `nullptr`.  
  
-   Pokud se tato operace úspěšná, ale aktuální objekt WeakRef není odvozen z parametru S_OK `riid`. Parametr `ptr` je nastaven na `nullptr`. (Další informace najdete v části poznámky.)  
  
## <a name="remarks"></a>Poznámky  
 Je vygenerované chybu, pokud parametr `riid` není odvozen od IInspectable. Tato chyba nahrazuje návratovou hodnotu.  
  
 První šablona je formulář, který by měli používat v kódu. Druhá šablona (není vidět tady, ale v záhlaví souboru deklarována) je interní, specializace pomocné rutiny, která podporuje funkcí jazyka C++, jako [automaticky](../cpp/auto-cpp.md) zadejte odvození – klíčové slovo.  
  
 Od verze Windows 10 SDK, tato metoda nenastaví WeakRef instance `nullptr` Pokud nebylo možné získat odkaz na slabé, proto byste neměli kontrolní součet, která kontroluje WeakRef pro `nullptr`. Místo toho zkontrolujte `ptr` pro `nullptr`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)