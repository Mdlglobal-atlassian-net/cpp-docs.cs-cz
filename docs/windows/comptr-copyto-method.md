---
title: "Comptr::CopyTo – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::CopyTo
dev_langs: C++
helpviewer_keywords: CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 184abddec5099eff20f75531fe240886841e9814
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo – metoda
Kopie rozhraní zadané nebo aktuální přidružený tento ComPtr na zadaný ukazatel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  
template<  
   typename U  
>  
  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Název typu.  
  
 `ptr`  
 Když tato operace dokončí, ukazatel na požadované rozhraní.  
  
 `riid`  
 Identifikátor rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT, která označuje, proč implicitní QueryInterface operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 První funkce vrátí kopii ukazatele rozhraní přidružené k této ComPtr. Tato funkce vždy vrátí hodnotu S_OK.  
  
 Funkce second provede operaci QueryInterface na rozhraní přidružené k této ComPtr pro rozhraní zadané `riid` parametr.  
  
 Třetí funkce provede operaci QueryInterface na rozhraní přidružené k této ComPtr pro základní rozhraní `U` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)