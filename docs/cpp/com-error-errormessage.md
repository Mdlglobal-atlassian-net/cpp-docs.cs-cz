---
title: _com_error::errorMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::ErrorMessage
dev_langs: C++
helpviewer_keywords: ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b60c0f74cd350382b6cf8669361087dee601fe4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Konkrétní Microsoft**  
  
 Získá řetězcovou zprávu pro `HRESULT` uložený v `_com_error`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí řetězcovou zprávu pro `HRESULT`, který je zaznamenaný v rámci objektu `_com_error`. Pokud `HRESULT` je namapované 16bitové [wcode –](../cpp/com-error-wcode.md), pak obecná zpráva "`IDispatch error #<wCode>`" je vrácen. Není-li nalezena žádná zpráva, je vrácena obecná zpráva „`Unknown error #<hresult>`“. Vrácený řetězec je Unicode nebo vícebajtové řetězec, v závislosti na stavu **_UNICODE** makro.  
  
## <a name="remarks"></a>Poznámky  
 Načte text zprávy příslušného systému pro `HRESULT`, který je zaznamenán v rámci objektu `_com_error`. Text zprávy systému se získá voláním Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkce. Vrácený řetězec je alokován pomocí rozhraní API `FormatMessage` a je uvolněn po zničení objektu `_com_error`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)