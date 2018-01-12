---
title: "Weakref::CopyTo – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::CopyTo
dev_langs: C++
helpviewer_keywords: CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b0114a9768fbea12a5b98f51911267cb24b0b43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo – metoda
Přiřadí ukazatele rozhraní, pokud je k dispozici, proměnnou zadaný ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<  
   typename U  
>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Ukazatel rozhraní IInspectable. Je vygenerované chybu, pokud `U` není odvozen od IInspectable.  
  
 `riid`  
 Identifikátor rozhraní. Je vygenerované chybu, pokud `riid` není odvozen od **IWeakReference**.  
  
 `ptr`  
 Dvakrát nepřímý ukazatel na IInspectable nebo IWeakReference.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT popisující selhání. Další informace najdete v části poznámky.  
  
## <a name="remarks"></a>Poznámky  
 Vrácená hodnota S_OK znamená, že tato operace proběhla úspěšně, ale neurčují, zda byla přeložit na odkaz na silné slabé odkaz. Pokud je vrácen S_OK, otestujte tento parametr `p` je silné odkaz; to znamená, parametr `p` není rovno `nullptr`.  
  
 Od verze Windows 10 SDK, tato metoda nenastaví WeakRef instance `nullptr` Pokud nebylo možné získat odkaz na slabé, proto byste neměli Chyba při kontrole kód, který kontroluje WeakRef pro `nullptr`. Místo toho zkontrolujte `ptr` pro `nullptr`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)