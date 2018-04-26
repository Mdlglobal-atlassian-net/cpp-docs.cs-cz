---
title: _set_abort_behavior – | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7ee65b603997a0be4fe9e937299eab9520c6f5b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Určuje akci, která mají být provedeny, když program je ukončen neobvyklým způsobem.

> [!NOTE]
> Nepoužívejte [abort](abort.md) funkce vypnout aplikaci pomocí Microsoft Store, s výjimkou testování nebo ladění scénáře. Zavřete aplikaci ve Store způsoby programový nebo uživatelského rozhraní nejsou povolené podle požadavků [Microsoft Store zásady](http://go.microsoft.com/fwlink/?LinkId=865936). Další informace najdete v tématu [životní cyklus aplikace UWP](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*Příznaky*<br/>
Nová hodnota [abort](abort.md) příznaky.

*Maska*<br/>
Maskování pro [abort](abort.md) flags bits k nastavení.

## <a name="return-value"></a>Návratová hodnota

Původní hodnota příznaků.

## <a name="remarks"></a>Poznámky

Existují dva [abort](abort.md) příznaky: **_WRITE_ABORT_MSG** a **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** Určuje, zda je vytištěna užitečné textovou zprávu, když program je ukončen neobvyklým způsobem. Zpráva, že aplikace volal [abort](abort.md) funkce. Výchozí chování je tisknout zprávy. **_CALL_REPORTFAULT**, pokud nastavení, určuje, že stav systému Watson se generuje a kdy hlášené [abort](abort.md) je volána. Ve výchozím nastavení je hlášení chyb výpisu povolené v sestavení bez ladění.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[abort](abort.md)<br/>
