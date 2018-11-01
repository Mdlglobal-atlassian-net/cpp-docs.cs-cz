---
title: _set_abort_behavior
ms.date: 1/02/2018
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
ms.openlocfilehash: 8b36a771a3694c6d01573d619990743c7ddc0f3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643050"
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Určuje akci, která mají být provedeny, když je program neobvykle ukončen.

> [!NOTE]
> Nepoužívejte [přerušit](abort.md) funkce vypnout aplikaci pomocí Microsoft Store, s výjimkou testování nebo ladění scénářů. Zavření aplikace pro Store způsoby programátorské nebo uživatelské rozhraní nejsou povoleny podle [zásady Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Nová hodnota [přerušit](abort.md) příznaky.

*Maska*<br/>
Maska pro [přerušit](abort.md) nastavit bity příznaky.

## <a name="return-value"></a>Návratová hodnota

Původní hodnota příznaků.

## <a name="remarks"></a>Poznámky

Existují dva [přerušit](abort.md) příznaky: **_WRITE_ABORT_MSG** a **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** Určuje, zda je vytištěna užitečná textová zpráva, když je program neobvykle ukončen. Zpráva hlásí, že aplikace volala [přerušit](abort.md) funkce. Výchozí chování je tisk zprávy. **_CALL_REPORTFAULT**, pokud nastaveno, určuje, že výpis při selhání aplikace Watson je generován a hlášen při [přerušit](abort.md) je volána. Ve výchozím nastavení je hlášení chyb s výpisem paměti povoleno v sestaveních bez ladění.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
