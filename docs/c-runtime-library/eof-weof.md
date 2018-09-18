---
title: KONEC SOUBORU, WEOF | Dokumentace Microsoftu
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
ms.openlocfilehash: 113ae268b4f97fdd14a3ac1a7fd0397b61ef8eb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065748"
---
# <a name="eof-weof"></a>EOF, WEOF

## <a name="syntax"></a>Syntaxe

```

#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Konec souboru je vrácený rutiny vstupně-výstupní operace při ukončení ze souboru (nebo v některých případech může chybu) dochází.

WEOF vrací návratovou hodnotu typu **wint_t**, která se používá, který signalizuje, že konec široké datového proudu nebo hlášení chybovou podmínku.

## <a name="see-also"></a>Viz také

[putc, putwc](../c-runtime-library/reference/putc-putwc.md)<br/>
[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[fflush](../c-runtime-library/reference/fflush.md)<br/>
[fclose, _fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)<br/>
[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)