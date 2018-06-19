---
title: _com_error::Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02afac78de5eb5908d477f8503ceeebffe46f672
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412579"
---
# <a name="comerrorerror"></a>_com_error::Error
**Konkrétní Microsoft**  
  
 Načte `HRESULT` předaný konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Nezpracovaná položka `HRESULT` předaná do konstruktoru.  
  
## <a name="remarks"></a>Poznámky  
 Načítá zapouzdřenou položku `HRESULT` v objektu `_com_error`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)