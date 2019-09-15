---
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: 8838282db851c6811a3f24c75a03b31c5870e6d3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948364"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

Povolí nebo zakáže použití Streaming SIMD Extensions 2 (SSE2) instrukcí v matematických rutinách CRT. (Tato funkce není k dispozici v architekturách x64, protože ve výchozím nastavení je povolená služba SSE2.)

## <a name="syntax"></a>Syntaxe

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Parametry

*příznaků*<br/>
1 pro povolení implementace SSE2; 0 pro zakázání implementace SSE2 Ve výchozím nastavení je implementace SSE2 povolená u procesorů, které ho podporují.

## <a name="return-value"></a>Návratová hodnota

Nenulová, je-li povolena implementace SSE2; nula, pokud je SSE2 implementace zakázána.

## <a name="remarks"></a>Poznámky

Následující funkce mají SSE2 implementace, které lze povolit pomocí **_set_SSE2_enable**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil –](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [řízení](floor-floorf-floorl.md)

- [protokolu](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf –](modf-modff-modfl.md)

- [log](pow-powf-powl.md)

SSE2 implementace těchto funkcí může vést ke mírně odlišným odpovědím, než je výchozí implementace, protože SSE2 mezilehlé hodnoty jsou 64, ale výchozí implementace mezihodnot jsou 80-bit. množství s plovoucí desetinnou čárkou.

> [!NOTE]
> Použijete-li možnost kompilátoru [/Oi (generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md) pro zkompilování projektu, může se zdát, že **_set_SSE2_enable** nemá žádný vliv. Možnost kompilátoru **/Oi** dává kompilátoru oprávnění k použití vnitřníchy k nahrazení volání CRT; Toto chování Přepisuje účinek **_set_SSE2_enable**. Chcete-li zaručit, že **/Oi** nepřepisuje **_set_SSE2_enable**, použijte k zkompilování projektu **/Oi-** . To může být také dobrý postup při použití dalších přepínačů kompilátoru, které implikují **/Oi**.

Implementace SSE2 se používá pouze v případě, že jsou všechny výjimky maskovány. Použijte [_control87, _controlfp](control87-controlfp-control87-2.md) k maskování výjimek.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_SSE2_enable**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>Viz také:

[Funkce knihovny CRT](../../c-runtime-library/crt-library-features.md)<br/>
