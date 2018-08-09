---
title: Weakreference::Resolve – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93df4ebf46b187cab63fbfaed2e273c55e7c0d84
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013246"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Identifikátor rozhraní.  
  
 *ppvObject*  
 Když tato operace dokončí, kopii aktuální silného odkazu, pokud je počet odkazů silné nenulové.  
  
## <a name="return-value"></a>Návratová hodnota  
  
-   S_OK, pokud je tato operace úspěšná, a počet silného odkazu je nula. *PpvObject* parametr je nastaven na **nullptr**.  
  
-   S_OK, pokud je tato operace úspěšná a počet silného odkazu není nenulová. *PpvObject* parametr je nastaven na silný odkaz.  
  
-   V opačném případě HRESULT, který označuje důvod tato operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 Nastaví zadaný ukazatel na aktuální hodnotu silného odkazu, pokud je počet odkazů silné nenulové.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [WeakReference – Třída1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)