---
title: operátor&lt; – operátor (Microsoft::WRL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
dev_langs:
- C++
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2de0d40a4b506da2cec36719b8fa2fe9c22108d8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604210"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operátor&lt; – operátor (Microsoft::WRL)
Určuje, zda je adresa jeden objekt menší než jiný.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<class T, class U>  
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();  
template<class T, class U>  
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *a*  
 Levý objekt.  
  
 *b*  
 Pravý objekt.  
  
## <a name="return-value"></a>Návratová hodnota  
 **true** Pokud adresa *a* je menší než adresu *b*; v opačném případě **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)