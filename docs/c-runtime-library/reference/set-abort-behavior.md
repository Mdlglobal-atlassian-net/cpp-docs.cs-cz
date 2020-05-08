---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: 06f72597a384cc5c90b2e345e62e13dee96c4dca
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913134"
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

*příznaky*<br/>
Nová hodnota příznaků [přerušení](abort.md) .

*Vlastnost maska*<br/>
Maska pro příznaky [přerušování](abort.md) , které se mají nastavit

## <a name="return-value"></a>Návratová hodnota

Stará hodnota příznaků.

## <a name="remarks"></a>Poznámky

Existují dva příznaky [přerušení](abort.md) : **_WRITE_ABORT_MSG** a **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** určuje, zda je při neobvyklém ukončení programu vytištěna užitečná textová zpráva. Zpráva uvádí, že aplikace volala funkci [Abort](abort.md) . Výchozím chováním je vytisknout zprávu. **_CALL_REPORTFAULT**, pokud je nastaveno, určuje, že výpis stavu systému Watson je vygenerován a uveden při volání metody [Abort](abort.md) . Ve výchozím nastavení je hlášení výpisu stavu systému povoleno v sestaveních bez ladění.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_abort_behavior**|\<Stdlib. h>|

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

## <a name="see-also"></a>Viz také

[přerušit](abort.md)<br/>
