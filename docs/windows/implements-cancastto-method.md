---
title: "Implements::cancastto – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 83d217cb749c350da45bcae2159e6b46d03f68cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo – metoda
Získá ukazatele k zadanému rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odkaz na rozhraní ID.  
  
 `ppv`  
 Pokud úspěšné, ukazatel na rozhraní zadán `riid`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak, který značí chybu, jako je například E_NOINTERFACE HRESULT.  
  
## <a name="remarks"></a>Poznámky  
 Toto je k interní pomocné funkce, který provede operaci QueryInterface.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Implements – struktura](../windows/implements-structure.md)