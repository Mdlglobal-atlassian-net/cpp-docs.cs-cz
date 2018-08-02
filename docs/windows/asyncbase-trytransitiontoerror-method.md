---
title: Asyncbase::trytransitiontoerror – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc677304ae7ab61e6726366869e85f731cd92484
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463204"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError – metoda
Určuje, zda kód zadanou chybovou můžete upravit stavu došlo k vnitřní chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Chyba*  
 Chyba HRESULT.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud státu došlo k vnitřní chybě byla změněné; v opačném případě **false**.  
  
## <a name="remarks"></a>Poznámky  
 Tato operace změní chybový stav, pouze v případě, že chybový stav je již nastavena na hodnotu S_OK. Tato operace nemá žádný vliv, pokud chybový stav je již chyba, zrušena, Dokončeno nebo Uzavřeno.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)