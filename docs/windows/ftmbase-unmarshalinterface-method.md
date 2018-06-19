---
title: Ftmbase::unmarshalinterface – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 964ce5cc33b51c54446874522317814279cdd960
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877716"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface – metoda
Inicializuje nově vytvořený proxy a vrátí ukazatele rozhraní zda proxy serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStm`  
 Ukazatel na datový proud, ze kterého má být zařazeny ukazatel rozhraní.  
  
 `riid`  
 Odkaz na identifikátor rozhraní být zařazeny.  
  
 `ppv`  
 Po této operaci dokončení adresu proměnné ukazatele, která přijímá ukazatel rozhraní požadované v `riid`. Pokud tato operace úspěšná, *`ppv` obsahuje požadované rozhraní ukazatele rozhraní být zařazeny.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota E_NOINTERFACE nebo E_FAIL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)