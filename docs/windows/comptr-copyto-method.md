---
title: Comptr::CopyTo – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 680c1278ca2b17c7ea35e72946fb5d5030c5e7c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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

template<typename U>  
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