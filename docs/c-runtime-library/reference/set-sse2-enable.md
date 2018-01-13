---
title: "_set_sse2_enable – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_SSE2_enable
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
dev_langs: C++
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28cbebdd46f9e6b95ff88bf159550e7ccc5f3ec0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setsse2enable"></a>_set_SSE2_enable
Povolí nebo zakáže použití [Streaming SIMD Extensions 2](http://msdn.microsoft.com/en-us/f98440eb-73a9-4f96-b203-ac41bb6701ea) pokynů (SSE2) v CRT matematické rutiny. (Tato funkce není k dispozici na x64 architektury vzhledem k tomu, že je ve výchozím nastavení povolené SSE2.)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _set_SSE2_enable(  
   int flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `flag`  
 1 pro zapnutí SSE2 implementace; 0 pro vypnutí SSE2 implementace. Ve výchozím nastavení je implementace SSE2 povolené u procesorů, které ji podporují.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je povoleno SSE2 implementace; nula, pokud je zakázána SSE2 implementace.  
  
## <a name="remarks"></a>Poznámky  
 Následující funkce nemají SSE2 implementace, které je možné povolit pomocí `_set_SSE2_enable`:  
  
-   [Atan](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)  
  
-   [ceil](../../c-runtime-library/reference/ceil-ceilf-ceill.md)  
  
-   [Exp](../../c-runtime-library/reference/exp-expf.md)  
  
-   [Floor](../../c-runtime-library/reference/floor-floorf-floorl.md)  
  
-   [protokolu](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [LOG10](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [modf –](../../c-runtime-library/reference/modf-modff-modfl.md)  
  
-   [Pow](../../c-runtime-library/reference/pow-powf-powl.md)  
  
 Implementace SSE2 těchto funkcí může poskytnout odpovědi trochu jiná než výchozí implementace, protože SSE2 pomocných hodnot s plovoucí desetinnou čárkou počty 64-bit ale pomocných hodnot výchozí implementace jsou 80bitová počty s plovoucí desetinnou čárkou.  
  
> [!NOTE]
>  Pokud použijete [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md) – možnost kompilátoru kompilace projektu, se zobrazí s `_set_SSE2_enable` nemá žádný vliv. `/Oi` – Možnost kompilátoru dává kompilátoru oprávnění pro vnitřní funkce použít k nahrazení volání CRT; toto chování přepsání účinku `_set_SSE2_enable`. Pokud chcete zaručit, že `/Oi` nepřepisuje `_set_SSE2_enable`, použijte `/Oi-` kompilace projektu. To může také být vhodné, pokud používáte jiné přepínače kompilátoru, které implikují `/Oi`.  
  
 Implementace SSE2 se používá, pokud jsou maskována všechny výjimky. Použití [_control87, _controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) k výjimkám masky.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_SSE2_enable`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
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
  
 **Output**  
  
 `SSE2 enabled.`  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../../c-runtime-library/crt-library-features.md)