---
title: "Weakreference::Resolve – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs: C++
helpviewer_keywords: Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9dc2eef072e64d38b96afd045bae6a9b23d59d94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identifikátor rozhraní.  
  
 `ppvObject`  
 Po této operaci dokončení vytvoří kopii aktuální silné odkaz, pokud je tento počet silné odkaz nenulové hodnoty.  
  
## <a name="return-value"></a>Návratová hodnota  
  
-   S_OK, pokud tato operace úspěšná a počet silné odkaz je nulová. `ppvObject` Parametr je nastaven na `nullptr`.  
  
-   S_OK, pokud tato operace je úspěšné a počet silné odkaz je nenulové hodnoty. `ppvObject` Parametr je nastaven na silné odkaz.  
  
-   Jinak hodnota HRESULT určující z důvodu této operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 Nastaví zadaný ukazatele na aktuální hodnotu silné odkaz, pokud počet silné odkazů nenulové hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [WeakReference Class1](../windows/weakreference-class1.md)   
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)