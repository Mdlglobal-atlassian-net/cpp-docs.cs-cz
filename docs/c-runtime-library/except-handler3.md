---
title: _except_handler3
ms.date: 11/04/2016
api_name:
- _except_handler3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 5e1dbab97e0f193d4ff59c19229d2c00e2cd7d6a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944485"
---
# <a name="_except_handler3"></a>_except_handler3

Vnitřní funkce CRT. Používá se rozhraním k nalezení vhodné obslužné rutiny výjimky pro zpracování aktuální výjimky.

## <a name="syntax"></a>Syntaxe

```
int _except_handler3(
   PEXCEPTION_RECORD exception_record,
   PEXCEPTION_REGISTRATION registration,
   PCONTEXT context,
   PEXCEPTION_REGISTRATION dispatcher
);
```

#### <a name="parameters"></a>Parametry

*exception_record*<br/>
pro Informace o konkrétní výjimce.

*evidenc*<br/>
pro Záznam, který označuje tabulku oboru, by měl být použit k vyhledání obslužné rutiny výjimky.

*context*<br/>
pro Rezervovaný.

*dispatcher*<br/>
pro Rezervovaný.

## <a name="return-value"></a>Návratová hodnota

Pokud by měla být výjimka zrušena, vrátí `DISPOSITION_DISMISS`. Pokud by výjimka měla být předána úrovní pro zapouzdření obslužných rutin výjimek, vrátí `DISPOSITION_CONTINUE_SEARCH`.

## <a name="remarks"></a>Poznámky

Pokud tato metoda najde vhodnou obslužnou rutinu výjimky, předá výjimku obslužné rutině. V této situaci se tato metoda nevrátí do kódu, který ji volal, a návratová hodnota je nerelevantní.

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
