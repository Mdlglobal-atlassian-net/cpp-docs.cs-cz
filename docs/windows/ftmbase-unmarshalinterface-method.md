---
title: Ftmbase::unmarshalinterface – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: d7b34f1af7734fa22db3a9f296bc021917356f8a
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570025"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface – metoda
Inicializuje nově vytvořeného serveru proxy a vrátí ukazatel rozhraní na tento server proxy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 *pStm*  
 Ukazatel na datový proud, ze kterého má být zrušeno ukazatel rozhraní.  
  
 *riid*  
 Odkaz na identifikátor rozhraní bude zrušeno.  
  
 *ppv*  
 Když tato operace dokončí, adresu proměnné ukazatele, která přijímá ukazatel rozhraní požadovaný v *riid*. Pokud je tato operace úspěšná, **ppv* obsahuje požadované rozhraní ukazatel rozhraní, bude zrušeno.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; jinak E_NOINTERFACE nebo E_FAIL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)