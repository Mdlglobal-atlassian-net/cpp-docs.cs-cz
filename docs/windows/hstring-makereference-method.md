---
title: Hstring::makereference – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 673d5b10706580303f179ee453495b581d96eda3
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608332"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference – metoda
Vytvoří `HStringReference` objekt ze zadaného parametru řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
### <a name="parameters"></a>Parametry  
 *sizeDest*  
 Parametr šablony, které určuje velikost cílové `HStringReference` vyrovnávací paměti.  
  
 *str*  
 Odkaz na řetězec širokých znaků.  
  
 *Délka*  
 Maximální délka *str* parametr vyrovnávací paměti pro použití v této operaci. Pokud *len* parametr není zadán, celý *str* parametr se používá.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HStringReference` Objekt, jehož hodnota je stejný jako zadaný *str* parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)