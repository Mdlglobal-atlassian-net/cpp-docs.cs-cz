---
title: _com_error::errorMessage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bff5e8f84b316f028daf503c3013667c82aaa4e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940563"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Specifické pro Microsoft**  
  
 Získá řetězcovou zprávu pro HRESULT uložený ve `_com_error` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí řetězcovou zprávu pro v rámci zaznamenaná hodnota HRESULT `_com_error` objektu. Pokud hodnota HRESULT je namapované 16bitové [wCode](../cpp/com-error-wcode.md), obecná zpráva "`IDispatch error #<wCode>`" je vrácena. Není-li nalezena žádná zpráva, je vrácena obecná zpráva „`Unknown error #<hresult>`“. Vrácený řetězec je typu Unicode nebo vícebajtový řetězec, v závislosti na stavu makra _UNICODE.  
  
## <a name="remarks"></a>Poznámky  
 Načte text zprávy příslušného systému pro HRESULT zaznamenaný v `_com_error` objektu. Text zprávy systému je získán voláním rozhraní Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkce. Vrácený řetězec je alokován pomocí rozhraní API `FormatMessage` a je uvolněn po zničení objektu `_com_error`.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)