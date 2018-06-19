---
title: EOF, WEOF – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- EOF
dev_langs:
- C++
helpviewer_keywords:
- EOF function
- WEOF function
- end of file
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f4d6138ab18220031c96ab84c2b7ca57e419371
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389160"
---
# <a name="eof-weof"></a>EOF, WEOF
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Vrátí EOF rutiny vstupně-výstupní operace při end konec souboru (nebo v některých případech chybu) je došlo.  
  
 Weof – vypočítá návratovou hodnotu typu **wint_t –** používané signál konec široké datového proudu, nebo k hlášení chybový stav.  
  
## <a name="see-also"></a>Viz také  
 [putc –, putwc –](../c-runtime-library/reference/putc-putwc.md)   
 [ungetc –, ungetwc –](../c-runtime-library/reference/ungetc-ungetwc.md)   
 [scanf, _scanf_l –, wscanf, _wscanf_l –](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [fflush –](../c-runtime-library/reference/fflush.md)   
 [fclose –, _fcloseall –](../c-runtime-library/reference/fclose-fcloseall.md)   
 [_ungetch –, _ungetwch –, _ungetch_nolock –, _ungetwch_nolock –](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)   
 [_putch –, _putwch –](../c-runtime-library/reference/putch-putwch.md)   
 [isascii – __isascii –, iswascii –](../c-runtime-library/reference/isascii-isascii-iswascii.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)