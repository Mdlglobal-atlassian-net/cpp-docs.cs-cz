---
title: _set_SSE2_enable
ms.date: 04/05/2018
apiname:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: c340423e93b6487a4a951e4b96055cba6e474269
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356534"
---
# <a name="setsse2enable"></a>_set_SSE2_enable

Povolí nebo zakáže použití instrukcí Streaming SIMD Extensions 2 (SSE2) v CRT matematických rutin. (Tato funkce není k dispozici na x64 architektury vzhledem k tomu, že je ve výchozím nastavení povolené SSE2.)

## <a name="syntax"></a>Syntaxe

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Parametry

*Příznak*<br/>
1 pro zapnutí provádění SSE2; 0 pro vypnutí implementace SSE2. Ve výchozím nastavení je implementace SSE2 povolené u procesorů, které ho podporují.

## <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povolené provádění SSE2; nula v případě implementace SSE2 je zakázaná.

## <a name="remarks"></a>Poznámky

Následující funkce mají implementace SSE2, které se dá nastavit pomocí **_set_sse2_enable –**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [Dolní mez](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [Pow](pow-powf-powl.md)

Implementace SSE2 z těchto funkcí může přidělit odpovědi trochu jinak než výchozí implementace, protože SSE2 mezilehlých hodnot s plovoucí desetinnou čárkou množství 64-bit ale hodnoty, ležící výchozí implementace jsou 80 bitů počty s plovoucí desetinnou čárkou.

> [!NOTE]
> Pokud používáte [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md) – možnost kompilátoru ke kompilaci projektu, může se zobrazit, který **_set_sse2_enable –** nemá žádný vliv. **/Oi** – možnost kompilátoru dává kompilátoru oprávnění k použití vnitřních objektů pro nahrazení volání CRT; toto chování potlačuje účinek **_set_sse2_enable –**. Pokud chcete zaručit, že **/Oi** nepřepisuje **_set_sse2_enable –**, použijte **/Oi-** ke kompilaci projektu. To může být také vhodné při použití jiné přepínače kompilátoru, které znamenají **/Oi**.

Implementace SSE2 se používá jenom v případě, že se maskují všechny výjimky. Použití [_control87 – _controlfp](control87-controlfp-control87-2.md) pro masku výjimky.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
