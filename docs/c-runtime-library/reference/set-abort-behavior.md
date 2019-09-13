---
title: _set_abort_behavior
ms.date: 01/02/2018
apiname:
- _set_abort_behavior
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: b72a485287684fc85f1e232e89774e07a5e3f42b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927481"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Určuje akci, která má být provedena při neobvyklém ukončení programu.

> [!NOTE]
> Nepoužívejte funkci [Abort](abort.md) k ukončení aplikace Microsoft Store, s výjimkou scénářů testování nebo ladění. Programové a uživatelské možnosti pro zavření aplikace ze Storu nejsou povolené podle [zásad Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*Flag*<br/>
Nová hodnota příznaků [přerušení](abort.md) .

*zrušit*<br/>
Maska pro příznaky [přerušování](abort.md) , které se mají nastavit

## <a name="return-value"></a>Návratová hodnota

Stará hodnota příznaků.

## <a name="remarks"></a>Poznámky

Existují dva příznaky [přerušení](abort.md) : **_WRITE_ABORT_MSG** a **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** určuje, zda je při neobvyklém ukončení programu vytištěna užitečná textová zpráva. Zpráva uvádí, že aplikace volala funkci [Abort](abort.md) . Výchozím chováním je vytisknout zprávu. **_CALL_REPORTFAULT**, pokud je nastaveno, určuje, že výpis stavu při selhání Watson je vygenerován a uveden při volání metody [Abort](abort.md) . Ve výchozím nastavení je hlášení výpisu stavu systému povoleno v sestaveních bez ladění.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>Viz také:

[abort](abort.md)<br/>
