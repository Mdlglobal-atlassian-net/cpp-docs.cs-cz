---
title: _except_handler3
ms.date: 11/04/2016
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 144bf25495d803a4db42ab45fcb0b101b09fe7cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613860"
---
# <a name="excepthandler3"></a>_except_handler3

Vnitřní funkce CRT. Používá rozhraní k vyhledání příslušné výjimky obslužná rutina zpracovávala na aktuální výjimku.

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
[in] Informace o určité výjimky.

*Registrace*<br/>
[in] Záznam, který určuje, které rozsah tabulky by měl být použit k vyhledání obslužná rutina výjimky.

*Kontext*<br/>
[in] Vyhrazená.

*Dispečer*<br/>
[in] Vyhrazená.

## <a name="return-value"></a>Návratová hodnota

Pokud by měl zrušit výjimku, vrátí `DISPOSITION_DISMISS`. Pokud výjimky by měly být předány o úroveň výš zapouzdřující obslužné rutiny výjimek, vrátí `DISPOSITION_CONTINUE_SEARCH`.

## <a name="remarks"></a>Poznámky

Pokud tato metoda vyhledá obslužnou rutinu příslušné výjimky, předá výjimku do obslužné rutiny. V takovém případě tato metoda nevrátí do kódu, která ji zavolala a vrácená hodnota je relevantní.

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)