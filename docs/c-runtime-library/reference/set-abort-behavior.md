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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: fd3a3c2f99d1702cdccf68328c2122b965b2d078
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337874"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Určuje akci, která má být provedena při abnormálně ukončení programu.

> [!NOTE]
> Nepoužívejte funkci [přerušení](abort.md) k vypnutí aplikace Microsoft Store, s výjimkou scénářů testování nebo ladění. Programové nebo způsoby, jak zavřít aplikaci store, nejsou povoleny v souladu se [zásadami Microsoft Storu](/legal/windows/agreements/store-policies). Další informace naleznete v [tématu Životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Nová hodnota [abort](abort.md) příznaky.

*Vlastnost maska*<br/>
Maska pro [přerušení](abort.md) příznaky bitů nastavit.

## <a name="return-value"></a>Návratová hodnota

Stará hodnota příznaky.

## <a name="remarks"></a>Poznámky

Existují dva příznaky [přerušení:](abort.md) **_WRITE_ABORT_MSG** a **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** určuje, zda je užitečná textová zpráva vytištěna při abnormálně ukončeném programu. Zpráva uvádí, že aplikace volala funkci [abort.](abort.md) Výchozí chování je vytisknout zprávu. **_CALL_REPORTFAULT**, pokud je nastavena, určuje, že je generován a hlášen výpis stavu systému Watson při volání [abort.](abort.md) Ve výchozím nastavení je v sestaveních bez ladění povoleno vykazování výpisu stavu systému.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Přerušení](abort.md)<br/>
